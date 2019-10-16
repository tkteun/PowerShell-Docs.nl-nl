---
title: Para meters toevoegen die de invoer van de pijp lijn verwerken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355641"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="3ce48-102">Parameters toevoegen die pijplijninvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="3ce48-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="3ce48-103">Eén invoer bron voor een cmdlet is een object in de pijp lijn dat afkomstig is uit een upstream-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3ce48-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="3ce48-104">In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de cmdlet Get-proc (die wordt beschreven in [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)), zodat de cmdlet pijplijn objecten kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="3ce48-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="3ce48-105">Deze Get-proc-cmdlet gebruikt een `Name`-para meter die invoer van een pijplijn object accepteert, proces informatie ophaalt van de lokale computer op basis van de opgegeven namen en vervolgens informatie over de processen op de opdracht regel weergeeft.</span><span class="sxs-lookup"><span data-stu-id="3ce48-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="3ce48-106">De cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="3ce48-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="3ce48-107">De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert.</span><span class="sxs-lookup"><span data-stu-id="3ce48-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="3ce48-108">Met deze cmdlet worden proces gegevens opgehaald, zodat de naam van de term ' Get ' is.</span><span class="sxs-lookup"><span data-stu-id="3ce48-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="3ce48-109">(Bijna elk soort cmdlet waarmee informatie kan worden opgehaald, kan opdracht regel invoer verwerken.) Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.</span><span class="sxs-lookup"><span data-stu-id="3ce48-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="3ce48-110">Hier volgt de definitie voor deze Get-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3ce48-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="3ce48-111">Details van deze definitie vindt u in [het maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3ce48-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="3ce48-112">Invoer van de pijp lijn definiëren</span><span class="sxs-lookup"><span data-stu-id="3ce48-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="3ce48-113">In deze sectie wordt beschreven hoe u de invoer van de pijp lijn voor een cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="3ce48-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="3ce48-114">Deze Get-proc-cmdlet definieert een eigenschap die de para meter `Name` vertegenwoordigt, zoals wordt beschreven in [para meters toevoegen die opdracht regel invoer verwerken](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="3ce48-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="3ce48-115">(Zie het onderwerp voor algemene informatie over het declareren van para meters.)</span><span class="sxs-lookup"><span data-stu-id="3ce48-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="3ce48-116">Wanneer een cmdlet echter de invoer van de pijp lijn moet verwerken, moeten de para meters zijn gekoppeld aan invoer waarden door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="3ce48-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="3ce48-117">Als u dit wilt doen, moet u het sleutel woord `ValueFromPipeline` toevoegen of het sleutel woord `ValueFromPipelineByProperty` toevoegen aan de kenmerk declaratie [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3ce48-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="3ce48-118">Geef het sleutel woord `ValueFromPipeline` op als met de cmdlet het volledige invoer object wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="3ce48-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="3ce48-119">Geef de `ValueFromPipelineByProperty` op als met de cmdlet alleen een eigenschap van het object wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="3ce48-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="3ce48-120">Hier volgt de parameter declaratie voor de para meter `Name` van deze Get-proc-cmdlet die pijplijn invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="3ce48-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="3ce48-121">In de vorige verklaring wordt het sleutel woord `ValueFromPipeline` ingesteld op `true` zodat de Windows Power shell-runtime de para meter aan het inkomende object koppelt als het object van hetzelfde type is als de para meter, of als het kan worden gedwongen naar hetzelfde type.</span><span class="sxs-lookup"><span data-stu-id="3ce48-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="3ce48-122">Het sleutel woord `ValueFromPipelineByPropertyName` wordt ook ingesteld op `true` zodat de Windows Power shell-runtime het inkomende object controleert op een eigenschap `Name`.</span><span class="sxs-lookup"><span data-stu-id="3ce48-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="3ce48-123">Als het inkomende object een dergelijke eigenschap heeft, wordt de para meter `Name` door de runtime gebonden aan de eigenschap `Name` van het inkomende object.</span><span class="sxs-lookup"><span data-stu-id="3ce48-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="3ce48-124">De instelling van het sleutel woord `ValueFromPipeline`-kenmerk voor een para meter krijgt voor rang op de instelling voor het sleutel woord `ValueFromPipelineByPropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3ce48-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3ce48-125">Een invoer verwerkings methode overschrijven</span><span class="sxs-lookup"><span data-stu-id="3ce48-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3ce48-126">Als uw cmdlet de invoer van de pijp lijn moet afhandelen, moet de juiste invoer methoden worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="3ce48-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="3ce48-127">De basis methoden voor invoer verwerking zijn geïntroduceerd bij het [maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3ce48-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="3ce48-128">Deze Get-proc-cmdlet overschrijft de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) om de `Name` parameter invoer te verwerken die door de gebruiker of een script is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3ce48-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="3ce48-129">Met deze methode worden de processen voor elke aangevraagde proces naam of alle processen opgehaald als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3ce48-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="3ce48-130">U ziet dat in [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de aanroep van [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) het uitvoer mechanisme is voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="3ce48-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="3ce48-131">De tweede para meter van deze aanroep, `enumerateCollection`, wordt ingesteld op `true` om aan te geven dat de Windows Power shell-runtime de matrix van proces objecten moet opsommen en één proces per keer naar de opdracht regel moet schrijven.</span><span class="sxs-lookup"><span data-stu-id="3ce48-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="3ce48-132">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3ce48-132">Code Sample</span></span>

<span data-ttu-id="3ce48-133">Zie GetProcessSample03- C# voor [beeld](./getprocesssample03-sample.md)voor de volledige voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="3ce48-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="3ce48-134">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="3ce48-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="3ce48-135">Windows Power shell geeft informatie door over cmdlets met behulp van .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="3ce48-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="3ce48-136">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="3ce48-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3ce48-137">Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="3ce48-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3ce48-138">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="3ce48-138">Building the Cmdlet</span></span>

<span data-ttu-id="3ce48-139">Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="3ce48-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3ce48-140">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3ce48-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3ce48-141">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="3ce48-141">Testing the Cmdlet</span></span>

<span data-ttu-id="3ce48-142">Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="3ce48-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="3ce48-143">Test bijvoorbeeld de code voor de voor beeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3ce48-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="3ce48-144">Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="3ce48-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="3ce48-145">Voer de volgende opdrachten bij de Windows Power shell-prompt in om de proces namen via de pijp lijn op te halen.</span><span class="sxs-lookup"><span data-stu-id="3ce48-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="3ce48-146">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3ce48-146">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="3ce48-147">Voer de volgende regels in om de proces objecten op te halen die een `Name`-eigenschap van de processen met de naam "IEXPLORE" hebben.</span><span class="sxs-lookup"><span data-stu-id="3ce48-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="3ce48-148">In dit voor beeld wordt de cmdlet `Get-Process` (meegeleverd door Windows Power shell) gebruikt als een upstream-opdracht om de "IEXPLORE"-processen op te halen.</span><span class="sxs-lookup"><span data-stu-id="3ce48-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="3ce48-149">De volgende uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3ce48-149">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="3ce48-150">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3ce48-150">See Also</span></span>

[<span data-ttu-id="3ce48-151">Para meters toevoegen die opdracht regel invoer verwerken</span><span class="sxs-lookup"><span data-stu-id="3ce48-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="3ce48-152">Uw eerste cmdlet maken</span><span class="sxs-lookup"><span data-stu-id="3ce48-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="3ce48-153">[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3ce48-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="3ce48-154">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3ce48-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="3ce48-155">Naslag informatie voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="3ce48-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="3ce48-156">Voor beelden van cmdlets</span><span class="sxs-lookup"><span data-stu-id="3ce48-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
