---
title: Parameter toe te voegen aan een Cmdlet ingesteld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: 6a3b592c5f85c1f065ad4b5b0290cf44dcef484e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854883"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="40d2a-102">Parametersets toevoegen aan een cmdlet</span><span class="sxs-lookup"><span data-stu-id="40d2a-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="40d2a-103">Om te weten over parametersets</span><span class="sxs-lookup"><span data-stu-id="40d2a-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="40d2a-104">Windows PowerShell definieert een parameter is ingesteld als een groep van de parameters die samen te werken.</span><span class="sxs-lookup"><span data-stu-id="40d2a-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="40d2a-105">Door het groeperen van de parameters van een cmdlet, kunt u één cmdlet die de functionaliteit ervan op basis van welke groep van de parameters worden opgegeven die de gebruiker kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="40d2a-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="40d2a-106">Een voorbeeld van een cmdlet die twee parametersets gebruikt voor het definiëren van verschillende functies is de `Get-EventLog` cmdlet die wordt geleverd door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40d2a-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="40d2a-107">Deze cmdlet worden verschillende gegevens geretourneerd wanneer de gebruiker Hiermee geeft u de `List` of `LogName` parameter.</span><span class="sxs-lookup"><span data-stu-id="40d2a-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="40d2a-108">Als de `LogName` parameter is opgegeven, wordt de cmdlet retourneert informatie over de gebeurtenissen in een opgegeven gebeurtenislogboek.</span><span class="sxs-lookup"><span data-stu-id="40d2a-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="40d2a-109">Als de `List` parameter is opgegeven, wordt de cmdlet retourneert informatie over het logboek bestanden zelf (niet de gebeurtenisgegevens ze bevatten).</span><span class="sxs-lookup"><span data-stu-id="40d2a-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="40d2a-110">In dit geval de `List` en `LogName` parameters identificeren twee afzonderlijke parametersets.</span><span class="sxs-lookup"><span data-stu-id="40d2a-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="40d2a-111">Twee belangrijke dingen om te weten over parametersets is dat de Windows PowerShell-runtime wordt slechts één parameter is ingesteld voor een bepaalde invoer gebruikt, en elke parameter is ingesteld, moet ten minste één parameter hebben die uniek is voor deze parameter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="40d2a-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="40d2a-112">Als u wilt laten zien dat laatste moment, met deze cmdlet Stop-Proc maakt gebruik van drie parametersets: `ProcessName`, `ProcessId`, en `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="40d2a-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="40d2a-113">Elk van deze parametersets heeft een parameter die zich niet in de andere parametersets.</span><span class="sxs-lookup"><span data-stu-id="40d2a-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="40d2a-114">De parametersets andere parameters kunnen delen, maar de cmdlet maakt gebruik van de unieke parameters `ProcessName`, `ProcessId`, en `InputObject` om te bepalen welke set parameters die voor de Windows PowerShell-runtime wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40d2a-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="40d2a-115">De Cmdlet-klasse declareren</span><span class="sxs-lookup"><span data-stu-id="40d2a-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="40d2a-116">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="40d2a-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="40d2a-117">Voor deze cmdlet wordt de levenscyclus van een term 'Stop' omdat de cmdlet systeemprocessen stopt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40d2a-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="40d2a-118">De naam van het zelfstandig naamwoord 'Proc' wordt gebruikt omdat de cmdlet op processen werkt.</span><span class="sxs-lookup"><span data-stu-id="40d2a-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="40d2a-119">Houd er rekening mee dat de naam van de cmdlet werkwoord en een zelfstandig naamwoord naam van de cmdlet-klasse worden weergegeven in de onderstaande verklaring.</span><span class="sxs-lookup"><span data-stu-id="40d2a-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="40d2a-120">Zie voor meer informatie over de namen van de term goedgekeurde cmdlet [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="40d2a-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="40d2a-121">De volgende code wordt de klassedefinitie van deze cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="40d2a-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="40d2a-122">De Parameters van de Cmdlet declareren</span><span class="sxs-lookup"><span data-stu-id="40d2a-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="40d2a-123">Deze cmdlet definieert drie parameters nodig als invoer voor de cmdlet (deze parameters ook definiëren de parametersets), evenals een `Force` parameter die wordt beheerd betekenis van de cmdlet en een `PassThru` parameter waarmee wordt bepaald of de cmdlet verzendt een uitvoerobject via de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="40d2a-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="40d2a-124">Deze cmdlet geeft standaard, niet een object via de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="40d2a-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="40d2a-125">Zie voor meer informatie over deze laatste twee parameters [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="40d2a-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="40d2a-126">De Parameter Name declareren</span><span class="sxs-lookup"><span data-stu-id="40d2a-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="40d2a-127">Deze invoerparameter kan de gebruiker om op te geven van de namen van de processen worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="40d2a-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="40d2a-128">Houd er rekening mee dat de `ParameterSetName` kenmerken van het door u opgegeven trefwoord de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk geeft u de `ProcessName` parameter ingesteld voor deze parameter.</span><span class="sxs-lookup"><span data-stu-id="40d2a-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="40d2a-129">Houd er ook rekening mee dat u dat de alias "Procesnaam" voor deze parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="40d2a-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="40d2a-130">De Parameter Id declareren</span><span class="sxs-lookup"><span data-stu-id="40d2a-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="40d2a-131">Deze invoerparameter kan de gebruiker om op te geven van de id's van de processen worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="40d2a-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="40d2a-132">Houd er rekening mee dat de `ParameterSetName` kenmerken van het door u opgegeven trefwoord de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk geeft u de `ProcessId` parameterset.</span><span class="sxs-lookup"><span data-stu-id="40d2a-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="40d2a-133">Houd er ook rekening mee dat u dat de alias "Proces-id" aan deze parameter wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="40d2a-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="40d2a-134">De InputObject Parameter declareren</span><span class="sxs-lookup"><span data-stu-id="40d2a-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="40d2a-135">Deze invoerparameter kan de gebruiker om op te geven van een invoer-object dat informatie bevat over de processen worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="40d2a-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="40d2a-136">Houd er rekening mee dat de `ParameterSetName` kenmerken van het door u opgegeven trefwoord de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk geeft u de `InputObject` parameter ingesteld voor deze parameter.</span><span class="sxs-lookup"><span data-stu-id="40d2a-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="40d2a-137">Houd er ook rekening mee dat u dat deze parameter geen alias heeft.</span><span class="sxs-lookup"><span data-stu-id="40d2a-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="40d2a-138">Parameters in meerdere parametersets declareren</span><span class="sxs-lookup"><span data-stu-id="40d2a-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="40d2a-139">Hoewel er een unieke parameter voor elke parameter is ingesteld moet, kunnen tot meer dan één parameterset parameters behoren.</span><span class="sxs-lookup"><span data-stu-id="40d2a-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="40d2a-140">In dergelijke gevallen geeft u de gedeelde parameter een [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de kenmerkdeclaratie van het voor elke waartoe de parameter set hoort.</span><span class="sxs-lookup"><span data-stu-id="40d2a-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="40d2a-141">Als een parameter in alle parametersets, alleen moet de parameterkenmerk eenmaal declareren en hoeft niet om op te geven dat de naam van de parameterset.</span><span class="sxs-lookup"><span data-stu-id="40d2a-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="40d2a-142">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="40d2a-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="40d2a-143">Elke cmdlet moet verwerken van methode invoer overschrijven, dit is meestal de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="40d2a-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="40d2a-144">In deze cmdlet de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode zodat een willekeurig aantal processen kan worden verwerkt door de cmdlet wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="40d2a-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="40d2a-145">Het bevat een instructie Select die aanroepen van een andere methode op basis van welke parameterset de gebruiker is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="40d2a-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="40d2a-146">De Help-methoden aangeroepen door de Select-instructie niet hier worden beschreven, maar ziet u de implementatie in het volledige codevoorbeeld in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="40d2a-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="40d2a-147">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="40d2a-147">Code Sample</span></span>

<span data-ttu-id="40d2a-148">Voor de volledige C# voorbeeldcode, Zie [StopProcessSample04 voorbeeld](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="40d2a-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="40d2a-149">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="40d2a-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="40d2a-150">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="40d2a-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="40d2a-151">Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40d2a-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="40d2a-152">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="40d2a-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="40d2a-153">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="40d2a-153">Building the Cmdlet</span></span>

<span data-ttu-id="40d2a-154">Na de implementatie van een cmdlet, moet u deze registreren met Windows PowerShell via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="40d2a-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="40d2a-155">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="40d2a-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="40d2a-156">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="40d2a-156">Testing the Cmdlet</span></span>

<span data-ttu-id="40d2a-157">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze door te voeren op de opdrachtregel testen.</span><span class="sxs-lookup"><span data-stu-id="40d2a-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="40d2a-158">Hier volgen enkele tests uit die laten zien hoe de `ProcessId` en `InputObject` parameters kunnen worden gebruikt voor het testen van hun parametersets om een proces te stoppen.</span><span class="sxs-lookup"><span data-stu-id="40d2a-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="40d2a-159">Met Windows PowerShell is gestart, voert u de cmdlet Stop-Proc met de `ProcessId` parameter ingesteld om een proces op basis van de id te stoppen.</span><span class="sxs-lookup"><span data-stu-id="40d2a-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="40d2a-160">In dit geval wordt de cmdlet gebruikt de `ProcessId` parameter ingesteld op het proces beëindigen.</span><span class="sxs-lookup"><span data-stu-id="40d2a-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="40d2a-161">Met Windows PowerShell is gestart, voert u de cmdlet Stop-Proc met de `InputObject` parameter ingesteld op het beëindigen van processen voor het Kladblok-object opgehaald door de `Get-Process` opdracht.</span><span class="sxs-lookup"><span data-stu-id="40d2a-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="40d2a-162">Zie ook</span><span class="sxs-lookup"><span data-stu-id="40d2a-162">See Also</span></span>

[<span data-ttu-id="40d2a-163">Het maken van een Cmdlet die Hiermee wijzigt u het systeem</span><span class="sxs-lookup"><span data-stu-id="40d2a-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="40d2a-164">Over het maken van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="40d2a-164">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="40d2a-165">Objecttypen uitbreiden en opmaak</span><span class="sxs-lookup"><span data-stu-id="40d2a-165">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="40d2a-166">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="40d2a-166">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="40d2a-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="40d2a-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
