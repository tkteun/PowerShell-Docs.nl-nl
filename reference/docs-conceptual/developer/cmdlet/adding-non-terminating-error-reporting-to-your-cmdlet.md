---
title: Niet-beëindigde fout rapportage toevoegen aan uw cmdlet | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6421d510f3701c12807568ad8786459123e80223
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784585"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="e9875-102">Rapportage aan uw cmdlet toevoegen voor fouten die niet leiden tot de beëindiging van een functie of bewerking</span><span class="sxs-lookup"><span data-stu-id="e9875-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="e9875-103">Cmdlets kunnen niet-afsluit fouten rapporteren door de methode [System. Management. Automation. cmdlet. WriteError][] aan te roepen en nog steeds te blijven werken op het huidige invoer object of op verdere inkomende pijplijn objecten.</span><span class="sxs-lookup"><span data-stu-id="e9875-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="e9875-104">In deze sectie wordt uitgelegd hoe u een cmdlet maakt die niet-afsluit fouten in de invoer methoden van het proces rapporteert.</span><span class="sxs-lookup"><span data-stu-id="e9875-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="e9875-105">Voor niet-afsluit fouten (en het beëindigen van fouten) moet de cmdlet een [System. Management. Automation. ErrorRecord][] -object door geven om de fout te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e9875-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span> <span data-ttu-id="e9875-106">Elke fout record wordt geïdentificeerd door een unieke teken reeks met de naam ' fout-id '.</span><span class="sxs-lookup"><span data-stu-id="e9875-106">Each error record is identified by a unique string called the "error identifier".</span></span> <span data-ttu-id="e9875-107">Naast de id wordt de categorie van elke fout opgegeven door constanten die zijn gedefinieerd door een [System. Management. Automation. ErrorCategory][] -inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="e9875-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span> <span data-ttu-id="e9875-108">De gebruiker kan fouten op basis van hun categorie weer geven door de `$ErrorView` variabele in te stellen op ' CategoryView '.</span><span class="sxs-lookup"><span data-stu-id="e9875-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="e9875-109">Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout records.</span><span class="sxs-lookup"><span data-stu-id="e9875-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="e9875-110">De cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="e9875-110">Defining the Cmdlet</span></span>

<span data-ttu-id="e9875-111">De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert.</span><span class="sxs-lookup"><span data-stu-id="e9875-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e9875-112">Met deze cmdlet worden proces gegevens opgehaald, zodat de naam van de term ' Get ' is.</span><span class="sxs-lookup"><span data-stu-id="e9875-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="e9875-113">(Bijna elk soort cmdlet waarmee informatie kan worden opgehaald, kan opdracht regel invoer verwerken.) Zie [cmdlet verb names](approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.</span><span class="sxs-lookup"><span data-stu-id="e9875-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e9875-114">Hier volgt de definitie voor deze `Get-Proc` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e9875-114">The following is the definition for this `Get-Proc` cmdlet.</span></span> <span data-ttu-id="e9875-115">Details van deze definitie vindt u in [het maken van uw eerste cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e9875-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="e9875-116">Para meters definiëren</span><span class="sxs-lookup"><span data-stu-id="e9875-116">Defining Parameters</span></span>

<span data-ttu-id="e9875-117">Als dat nodig is, moet uw cmdlet para meters definiëren voor het verwerken van invoer.</span><span class="sxs-lookup"><span data-stu-id="e9875-117">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="e9875-118">Deze Get-proc-cmdlet definieert een **naam** parameter zoals beschreven in [para meters toevoegen die opdracht regel invoer verwerken](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="e9875-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="e9875-119">Hier volgt de parameter declaratie voor de para meter **name** van deze Get-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e9875-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="e9875-120">Invoer verwerkings methoden overschrijven</span><span class="sxs-lookup"><span data-stu-id="e9875-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="e9875-121">Alle cmdlets moeten ten minste één van de invoer verwerkings methoden van de klasse [System. Management. Automation. cmdlet][] overschrijven.</span><span class="sxs-lookup"><span data-stu-id="e9875-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span> <span data-ttu-id="e9875-122">Deze methoden worden besproken bij [het maken van uw eerste cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e9875-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e9875-123">De cmdlet moet elke record zo onafhankelijk mogelijk verwerken.</span><span class="sxs-lookup"><span data-stu-id="e9875-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="e9875-124">Deze Get-proc-cmdlet onderdrukt de methode [System. Management. Automation. cmdlet. ProcessRecord][] om de para meter **name** te verwerken voor de invoer van de gebruiker of een script.</span><span class="sxs-lookup"><span data-stu-id="e9875-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span> <span data-ttu-id="e9875-125">Met deze methode worden de processen voor elke aangevraagde proces naam of alle processen opgehaald als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e9875-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="e9875-126">Details van deze onderdrukking zijn gegeven bij [het maken van uw eerste cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e9875-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="e9875-127">Dingen die u moet onthouden bij het rapporteren van fouten</span><span class="sxs-lookup"><span data-stu-id="e9875-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="e9875-128">Het object [System. Management. Automation. ErrorRecord][] dat door de cmdlet wordt door gegeven tijdens het schrijven van een fout, vereist een uitzonde ring op de kern.</span><span class="sxs-lookup"><span data-stu-id="e9875-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="e9875-129">Volg de .NET-richt lijnen bij het bepalen van de uitzonde ring die moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e9875-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="e9875-130">Als de fout semantisch hetzelfde is als een bestaande uitzonde ring, moet de cmdlet deze uitzonde ring gebruiken of afleiden.</span><span class="sxs-lookup"><span data-stu-id="e9875-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="e9875-131">Anders moet het een nieuwe uitzonde ring of uitzonderings hiërarchie rechtstreeks vanuit de klasse [System. Exception][] worden afgeleid.</span><span class="sxs-lookup"><span data-stu-id="e9875-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="e9875-132">Houd bij het maken van fout-id's (toegankelijk via de eigenschap FullyQualifiedErrorId van de klasse ErrorRecord) het volgende in acht.</span><span class="sxs-lookup"><span data-stu-id="e9875-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="e9875-133">Gebruik teken reeksen die zijn gericht op diagnostische doel einden, zodat u bij het controleren van de volledig gekwalificeerde id kunt bepalen wat de fout is en waar de fout vandaan komt.</span><span class="sxs-lookup"><span data-stu-id="e9875-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="e9875-134">Een goed gevormde, volledig gekwalificeerde fout-id kan er als volgt uitzien.</span><span class="sxs-lookup"><span data-stu-id="e9875-134">A well formed fully qualified error identifier might be as follows.</span></span>

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="e9875-135">In het vorige voor beeld wordt met de fout-id (het eerste token) aangegeven wat de fout is en het resterende deel geeft aan waar de fout vandaan komt.</span><span class="sxs-lookup"><span data-stu-id="e9875-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="e9875-136">Voor complexere scenario's kan de fout-id een token gescheiden door een punt zijn dat bij inspectie kan worden geparseerd.</span><span class="sxs-lookup"><span data-stu-id="e9875-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="e9875-137">Hierdoor kunt u de onderdelen van de fout-id en de fout-id en fout categorie als vertakking hebben.</span><span class="sxs-lookup"><span data-stu-id="e9875-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="e9875-138">De cmdlet moet specifieke fout-id's toewijzen aan verschillende code paden.</span><span class="sxs-lookup"><span data-stu-id="e9875-138">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="e9875-139">Houd de volgende informatie in acht voor het toewijzen van fout-id's:</span><span class="sxs-lookup"><span data-stu-id="e9875-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="e9875-140">Een fout-id moet constant blijven gedurende de levens cyclus van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e9875-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="e9875-141">Wijzig de semantiek van een fout-id tussen de cmdlet-versies niet.</span><span class="sxs-lookup"><span data-stu-id="e9875-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>
- <span data-ttu-id="e9875-142">Gebruik tekst voor een fout-id die tersely overeenkomt met de fout die wordt gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="e9875-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="e9875-143">Gebruik geen spaties of lees tekens.</span><span class="sxs-lookup"><span data-stu-id="e9875-143">Do not use white space or punctuation.</span></span>
- <span data-ttu-id="e9875-144">Laat uw cmdlet alleen fout-id's genereren die kunnen worden gereproduceerd.</span><span class="sxs-lookup"><span data-stu-id="e9875-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="e9875-145">Er mag bijvoorbeeld geen id worden gegenereerd die een proces-id bevat.</span><span class="sxs-lookup"><span data-stu-id="e9875-145">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="e9875-146">Fout-id's zijn alleen nuttig voor gebruikers wanneer ze overeenkomen met id's die worden gezien door andere gebruikers die hetzelfde probleem ondervinden.</span><span class="sxs-lookup"><span data-stu-id="e9875-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="e9875-147">Niet-verwerkte uitzonde ringen worden niet in de volgende omstandigheden door Power shell gedetecteerd:</span><span class="sxs-lookup"><span data-stu-id="e9875-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="e9875-148">Als een cmdlet een nieuwe thread maakt en de code die in die thread wordt uitgevoerd, een onverwerkte uitzonde ring genereert, wordt de fout niet onderschept door Power shell en wordt het proces beëindigd.</span><span class="sxs-lookup"><span data-stu-id="e9875-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>
- <span data-ttu-id="e9875-149">Als een object code bevat in de Destruct-of Dispose-methoden die een niet-verwerkte uitzonde ring veroorzaakt, wordt de fout niet onderschept door Power shell en wordt het proces beëindigd.</span><span class="sxs-lookup"><span data-stu-id="e9875-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="e9875-150">Niet-afsluit fouten rapporteren</span><span class="sxs-lookup"><span data-stu-id="e9875-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="e9875-151">Een van de invoer verwerkings methoden kan een niet-afsluit fout melden aan de uitvoer stroom met behulp van de methode [System. Management. Automation. cmdlet. WriteError][] .</span><span class="sxs-lookup"><span data-stu-id="e9875-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="e9875-152">Hier volgt een code voorbeeld van deze Get-proc-cmdlet die de aanroep van [System. Management. Automation. cmdlet. WriteError][] in de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord][] illustreert.</span><span class="sxs-lookup"><span data-stu-id="e9875-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span> <span data-ttu-id="e9875-153">In dit geval wordt de aanroep gedaan als de cmdlet geen proces voor een opgegeven proces-id kan vinden.</span><span class="sxs-lookup"><span data-stu-id="e9875-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="e9875-154">Wat u moet weten over het schrijven van niet-afsluit fouten</span><span class="sxs-lookup"><span data-stu-id="e9875-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="e9875-155">Voor een niet-afsluit fout moet de cmdlet een specifieke fout-id genereren voor elk specifiek invoer object.</span><span class="sxs-lookup"><span data-stu-id="e9875-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="e9875-156">Een cmdlet moet regel matig de Power shell-actie wijzigen die is geproduceerd door een niet-afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="e9875-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="e9875-157">U kunt dit doen door de `ErrorAction` `ErrorVariable` para meters en te definiëren.</span><span class="sxs-lookup"><span data-stu-id="e9875-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="e9875-158">Bij het definiëren `ErrorAction` van de para meter geeft de cmdlet de gebruikers opties [System. Management. Automation. ActionPreference][], kunt u ook rechtstreeks van invloed zijn op de actie door de variabele in te stellen `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="e9875-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="e9875-159">Met de-cmdlet kunnen niet-afsluit fouten worden opgeslagen in een variabele met behulp `ErrorVariable` van de para meter, die niet wordt beïnvloed door de instelling van `ErrorAction` .</span><span class="sxs-lookup"><span data-stu-id="e9875-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="e9875-160">Fouten kunnen worden toegevoegd aan een bestaande fout variabele door een plus teken (+) toe te voegen aan het begin van de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="e9875-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e9875-161">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e9875-161">Code Sample</span></span>

<span data-ttu-id="e9875-162">Zie GetProcessSample04-voor [beeld](./getprocesssample04-sample.md)voor de volledige C#-voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="e9875-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="e9875-163">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="e9875-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="e9875-164">Power shell geeft informatie door over cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="e9875-164">PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="e9875-165">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="e9875-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e9875-166">Zie [object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="e9875-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e9875-167">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="e9875-167">Building the Cmdlet</span></span>

<span data-ttu-id="e9875-168">Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren via een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="e9875-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e9875-169">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e9875-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e9875-170">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="e9875-170">Testing the Cmdlet</span></span>

<span data-ttu-id="e9875-171">Als uw cmdlet is geregistreerd bij Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="e9875-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e9875-172">We gaan de voor beeld van de cmdlet Get-proc testen om te zien of er een fout melding wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="e9875-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="e9875-173">Start Power shell en gebruik de cmdlet Get-proc om de processen met de naam TEST op te halen.</span><span class="sxs-lookup"><span data-stu-id="e9875-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

  ```powershell
  get-proc -name test
  ```

  <span data-ttu-id="e9875-174">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e9875-174">The following output appears.</span></span>

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a><span data-ttu-id="e9875-175">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e9875-175">See Also</span></span>

[<span data-ttu-id="e9875-176">Parameters toevoegen die pijplijninvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="e9875-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="e9875-177">Para meters toevoegen die opdracht regel invoer verwerken</span><span class="sxs-lookup"><span data-stu-id="e9875-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="e9875-178">Uw eerste cmdlet maken</span><span class="sxs-lookup"><span data-stu-id="e9875-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="e9875-179">[Object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e9875-179">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="e9875-180">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e9875-180">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="e9875-181">Naslaginformatie over Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9875-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="e9875-182">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="e9875-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System.Exception]: /dotnet/api/System.Exception
[System. Management. Automation. ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
