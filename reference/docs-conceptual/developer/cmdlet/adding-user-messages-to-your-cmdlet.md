---
ms.date: 09/13/2016
ms.topic: reference
title: Gebruikersberichten toevoegen aan uw cmdlet
description: Gebruikersberichten toevoegen aan uw cmdlet
ms.openlocfilehash: de6fcc093af1d01287eed1eb8cc7b81cf5d2fdd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668334"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="b4a61-103">Gebruikersberichten toevoegen aan uw cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4a61-103">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="b4a61-104">Met cmdlets kunt u verschillende soorten berichten schrijven die kunnen worden weer gegeven aan de gebruiker door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="b4a61-104">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="b4a61-105">Deze berichten bevatten de volgende typen:</span><span class="sxs-lookup"><span data-stu-id="b4a61-105">These messages include the following types:</span></span>

- <span data-ttu-id="b4a61-106">Uitgebreide berichten die algemene gebruikers informatie bevatten.</span><span class="sxs-lookup"><span data-stu-id="b4a61-106">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="b4a61-107">Fouten opsporen in berichten die informatie over het oplossen van problemen bevatten.</span><span class="sxs-lookup"><span data-stu-id="b4a61-107">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="b4a61-108">Waarschuwings berichten die een melding bevatten dat de cmdlet een bewerking moet uitvoeren die onverwachte resultaten kan hebben.</span><span class="sxs-lookup"><span data-stu-id="b4a61-108">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="b4a61-109">Voortgangs rapport berichten die informatie bevatten over de hoeveelheid werk die de cmdlet heeft voltooid bij het uitvoeren van een bewerking die lange tijd in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="b4a61-109">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="b4a61-110">Er zijn geen beperkingen voor het aantal berichten dat door de cmdlet kan worden geschreven of het type berichten dat door de cmdlet wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="b4a61-110">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="b4a61-111">Elk bericht wordt geschreven door een specifieke aanroep uit te voeren binnen de invoer verwerkings methode van uw cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b4a61-111">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="b4a61-112">De cmdlet definiëren</span><span class="sxs-lookup"><span data-stu-id="b4a61-112">Defining the Cmdlet</span></span>

<span data-ttu-id="b4a61-113">De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert.</span><span class="sxs-lookup"><span data-stu-id="b4a61-113">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b4a61-114">Elke sorteer-of cmdlet kan gebruikers meldingen schrijven van de invoer methoden. in het algemeen kunt u deze cmdlet een naam gegeven met een wille keurige term die aangeeft welke systeem wijzigingen de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b4a61-114">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="b4a61-115">Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b4a61-116">De cmdlet Stop-Proc is ontworpen om het systeem te wijzigen; Daarom moet de declaratie [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) voor de .net-klasse het `SupportsShouldProcess` sleutel woord attribute bevatten en worden ingesteld op `true` .</span><span class="sxs-lookup"><span data-stu-id="b4a61-116">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="b4a61-117">De volgende code is de definitie voor deze Stop-Proc-cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="b4a61-117">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="b4a61-118">Zie voor meer informatie over deze definitie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b4a61-118">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="b4a61-119">Para meters definiëren voor systeem wijziging</span><span class="sxs-lookup"><span data-stu-id="b4a61-119">Defining Parameters for System Modification</span></span>

<span data-ttu-id="b4a61-120">De cmdlet Stop-Proc definieert drie para meters: `Name` , `Force` en `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="b4a61-120">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="b4a61-121">Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over het definiëren van deze para meters.</span><span class="sxs-lookup"><span data-stu-id="b4a61-121">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="b4a61-122">Dit is de parameter declaratie voor de Stop-Proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b4a61-122">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b4a61-123">Een invoer verwerkings methode overschrijven</span><span class="sxs-lookup"><span data-stu-id="b4a61-123">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b4a61-124">De cmdlet moet een invoer verwerkings methode overschrijven, meestal is [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="b4a61-124">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="b4a61-125">Deze Stop-Proc-cmdlet overschrijft de verwerkings methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="b4a61-125">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="b4a61-126">In deze implementatie van de Stop-Proc cmdlet worden aanroepen gedaan om uitgebreide berichten, fout opsporingsgegevens en waarschuwings berichten te schrijven.</span><span class="sxs-lookup"><span data-stu-id="b4a61-126">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="b4a61-127">Zie [Creating a cmdlet waarmee het systeem wordt gewijzigd](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over hoe deze methode de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept.</span><span class="sxs-lookup"><span data-stu-id="b4a61-127">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="b4a61-128">Een uitgebreid bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="b4a61-128">Writing a Verbose Message</span></span>

<span data-ttu-id="b4a61-129">De methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) wordt gebruikt om algemene informatie op gebruikers niveau te schrijven die niet gerelateerd is aan specifieke fout voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="b4a61-129">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="b4a61-130">De systeem beheerder kan deze gegevens vervolgens gebruiken om de verwerking van andere opdrachten voort te zetten.</span><span class="sxs-lookup"><span data-stu-id="b4a61-130">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="b4a61-131">Daarnaast moeten alle informatie die met deze methode wordt geschreven, naar behoefte worden gelokaliseerd.</span><span class="sxs-lookup"><span data-stu-id="b4a61-131">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="b4a61-132">De volgende code uit deze Stop-Proc-cmdlet toont twee aanroepen naar de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) van de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="b4a61-132">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="b4a61-133">Een debug-bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="b4a61-133">Writing a Debug Message</span></span>

<span data-ttu-id="b4a61-134">De methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) wordt gebruikt voor het schrijven van fout opsporingsgegevens die kunnen worden gebruikt om de werking van de cmdlet op te lossen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-134">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="b4a61-135">De aanroep wordt uitgevoerd vanuit een invoer verwerkings methode.</span><span class="sxs-lookup"><span data-stu-id="b4a61-135">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="b4a61-136">Windows Power shell definieert ook een `Debug` para meter die zowel uitgebreide als fout opsporingsgegevens bevat.</span><span class="sxs-lookup"><span data-stu-id="b4a61-136">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="b4a61-137">Als uw cmdlet deze para meter ondersteunt, hoeft [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) niet te worden aangeroepen in dezelfde code die [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)aanroept.</span><span class="sxs-lookup"><span data-stu-id="b4a61-137">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="b4a61-138">De volgende twee secties van code uit de voor beeld-Stop-Proc-cmdlet geven aanroepen naar de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) uit de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="b4a61-138">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="b4a61-139">Dit fout bericht wordt onmiddellijk beschreven voordat [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="b4a61-140">Dit fout bericht wordt onmiddellijk beschreven voordat [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-140">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="b4a61-141">Windows Power shell stuurt automatisch alle [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -aanroepen naar de tracerings infrastructuur en-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b4a61-141">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="b4a61-142">Hierdoor kan de methode aanroepen naar de hosttoepassing, een bestand of een fout opsporingsprogramma worden getraceerd zonder dat u in de cmdlet extra ontwikkel werkzaamheden hoeft te doen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-142">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="b4a61-143">Het volgende opdracht regel item implementeert een tracerings bewerking.</span><span class="sxs-lookup"><span data-stu-id="b4a61-143">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="b4a61-144">**PS> Trace-Expression stop-proc-File proc. log-opdracht stop-proc Notepad**</span><span class="sxs-lookup"><span data-stu-id="b4a61-144">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="b4a61-145">Een waarschuwings bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="b4a61-145">Writing a Warning Message</span></span>

<span data-ttu-id="b4a61-146">De methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) wordt gebruikt om een waarschuwing te schrijven wanneer de cmdlet een bewerking uitvoert die een onverwacht resultaat kan hebben, bijvoorbeeld het overschrijven van een alleen-lezen bestand.</span><span class="sxs-lookup"><span data-stu-id="b4a61-146">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="b4a61-147">De volgende code uit de voor beeld-Stop-Proc-cmdlet toont de aanroep van de methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) van de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="b4a61-147">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="b4a61-148">Een voortgangs bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="b4a61-148">Writing a Progress Message</span></span>

<span data-ttu-id="b4a61-149">[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) wordt gebruikt om voortgangs berichten te schrijven wanneer cmdlet-bewerkingen een lange tijd lang duren om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b4a61-149">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="b4a61-150">Een aanroep van [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) geeft een [System. Management. Automation. Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) -object door dat naar de hosting toepassing wordt verzonden voor rendering naar de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b4a61-150">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="b4a61-151">Deze Stop-Proc cmdlet omvat geen aanroep van de methode [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .</span><span class="sxs-lookup"><span data-stu-id="b4a61-151">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="b4a61-152">De volgende code is een voor beeld van een voortgangs bericht dat is geschreven door een cmdlet die probeert een item te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="b4a61-152">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="b4a61-153">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b4a61-153">Code Sample</span></span>

<span data-ttu-id="b4a61-154">Zie StopProcessSample02-voor [beeld](./stopprocesssample02-sample.md)voor de volledige C#-voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="b4a61-154">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="b4a61-155">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="b4a61-155">Define Object Types and Formatting</span></span>

<span data-ttu-id="b4a61-156">Windows Power shell geeft informatie door over cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="b4a61-156">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b4a61-157">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="b4a61-157">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b4a61-158">Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-158">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b4a61-159">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="b4a61-159">Building the Cmdlet</span></span>

<span data-ttu-id="b4a61-160">Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="b4a61-160">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b4a61-161">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b4a61-161">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b4a61-162">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="b4a61-162">Testing the Cmdlet</span></span>

<span data-ttu-id="b4a61-163">Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b4a61-163">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="b4a61-164">We gaan de voor beeld-Stop-Proc-cmdlet testen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-164">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="b4a61-165">Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b4a61-165">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="b4a61-166">De volgende opdracht regel vermelding maakt gebruik van Stop-Proc om het proces ' NOTEPAD ' te stoppen, uitgebreide meldingen op te geven en fout opsporingsgegevens op te lossen.</span><span class="sxs-lookup"><span data-stu-id="b4a61-166">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

    <span data-ttu-id="b4a61-167">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b4a61-167">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="b4a61-168">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b4a61-168">See Also</span></span>

[<span data-ttu-id="b4a61-169">Een cmdlet maken die het systeem wijzigt</span><span class="sxs-lookup"><span data-stu-id="b4a61-169">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b4a61-170">Een Windows Power shell-cmdlet maken</span><span class="sxs-lookup"><span data-stu-id="b4a61-170">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="b4a61-171">[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b4a61-171">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="b4a61-172">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b4a61-172">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="b4a61-173">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b4a61-173">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
