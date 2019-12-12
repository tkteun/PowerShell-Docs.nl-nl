---
title: Parameter sets toevoegen aan een cmdlet | Microsoft Docs
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
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416322"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="16f68-102">Parametersets toevoegen aan een cmdlet</span><span class="sxs-lookup"><span data-stu-id="16f68-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="16f68-103">Wat u moet weten over parameter sets</span><span class="sxs-lookup"><span data-stu-id="16f68-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="16f68-104">Windows Power shell definieert een para meter die is ingesteld als een groep para meters die samen werken.</span><span class="sxs-lookup"><span data-stu-id="16f68-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="16f68-105">Als u de para meters van een cmdlet groepeert, kunt u een enkele cmdlet maken die de functionaliteit ervan kan wijzigen op basis van de groep para meters die de gebruiker opgeeft.</span><span class="sxs-lookup"><span data-stu-id="16f68-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="16f68-106">Een voor beeld van een cmdlet die gebruikmaakt van twee parameters sets voor het definiëren van verschillende functies is de `Get-EventLog`-cmdlet die wordt meegeleverd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="16f68-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="16f68-107">Deze cmdlet retourneert andere informatie wanneer de gebruiker de para meter `List` of `LogName` opgeeft.</span><span class="sxs-lookup"><span data-stu-id="16f68-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="16f68-108">Als de para meter `LogName` is opgegeven, retourneert de cmdlet informatie over de gebeurtenissen in een bepaald gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="16f68-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="16f68-109">Als de para meter `List` is opgegeven, retourneert de cmdlet informatie over de logboek bestanden zelf (niet de gebeurtenis gegevens die ze bevatten).</span><span class="sxs-lookup"><span data-stu-id="16f68-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="16f68-110">In dit geval identificeren de para meters `List` en `LogName` twee afzonderlijke parameter sets.</span><span class="sxs-lookup"><span data-stu-id="16f68-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="16f68-111">Twee belang rijke zaken die u moet onthouden over parameter sets is dat de Windows Power shell-runtime slechts één para meterset voor een bepaalde invoer gebruikt en dat elke parameterset ten minste één para meter moet hebben die uniek is voor de ingestelde para meter.</span><span class="sxs-lookup"><span data-stu-id="16f68-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="16f68-112">Ter illustratie van dat laatste punt gebruikt deze stop-proc-cmdlet drie parameter sets: `ProcessName`, `ProcessId`en `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="16f68-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="16f68-113">Elk van deze parameter sets heeft één para meter die zich niet in de andere parameter sets bevindt.</span><span class="sxs-lookup"><span data-stu-id="16f68-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="16f68-114">De parameter sets kunnen andere para meters delen, maar de cmdlet gebruikt de unieke para meters `ProcessName`, `ProcessId`en `InputObject` om te bepalen welke set para meters moet worden gebruikt door de Windows Power shell-runtime.</span><span class="sxs-lookup"><span data-stu-id="16f68-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="16f68-115">De cmdlet-klasse declareren</span><span class="sxs-lookup"><span data-stu-id="16f68-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="16f68-116">De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert.</span><span class="sxs-lookup"><span data-stu-id="16f68-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="16f68-117">Voor deze cmdlet wordt de levens cyclus term ' Stop ' gebruikt omdat de cmdlet systeem processen stopt.</span><span class="sxs-lookup"><span data-stu-id="16f68-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="16f68-118">De naam van het zelfstandige zelfstandig proces wordt gebruikt omdat de cmdlet werkt voor processen.</span><span class="sxs-lookup"><span data-stu-id="16f68-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="16f68-119">Houd er rekening mee dat het cmdlet-werk woord en de naam van het zelfstandigen worden weer gegeven in de naam van de cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="16f68-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="16f68-120">Zie voor meer informatie over de namen van goedgekeurde cmdlet- [verbs](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="16f68-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="16f68-121">De volgende code is de klassedefinitie voor deze stop-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16f68-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="16f68-122">De para meters van de cmdlet declareren</span><span class="sxs-lookup"><span data-stu-id="16f68-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="16f68-123">Met deze cmdlet worden drie para meters gedefinieerd die nodig zijn als invoer voor de cmdlet (deze para meters definiëren ook de parameter sets), evenals een `Force` para meter waarmee wordt beheerd wat de cmdlet doet en een `PassThru`-para meter die bepaalt of de cmdlet een uitvoer object via de pijp lijn verzendt.</span><span class="sxs-lookup"><span data-stu-id="16f68-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="16f68-124">Met deze cmdlet wordt standaard geen object door gegeven via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="16f68-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="16f68-125">Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over deze laatste twee para meters.</span><span class="sxs-lookup"><span data-stu-id="16f68-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="16f68-126">De para meter name declareren</span><span class="sxs-lookup"><span data-stu-id="16f68-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="16f68-127">Met deze invoer parameter kan de gebruiker de namen opgeven van de processen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="16f68-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="16f68-128">Houd er rekening mee dat het sleutel woord `ParameterSetName` kenmerk van het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de para meter `ProcessName` bevat die voor deze para meter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="16f68-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="16f68-129">Houd er rekening mee dat de alias ' procesnaam ' wordt gegeven aan deze para meter.</span><span class="sxs-lookup"><span data-stu-id="16f68-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="16f68-130">Declareren van de id-para meter</span><span class="sxs-lookup"><span data-stu-id="16f68-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="16f68-131">Met deze invoer parameter kan de gebruiker de id's opgeven van de processen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="16f68-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="16f68-132">Houd er rekening mee dat het sleutel woord `ParameterSetName` kenmerk van het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de para meter set `ProcessId` bevat.</span><span class="sxs-lookup"><span data-stu-id="16f68-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="16f68-133">Houd er rekening mee dat de alias ' ProcessId ' wordt opgegeven voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="16f68-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="16f68-134">Declareren van de para meter input object</span><span class="sxs-lookup"><span data-stu-id="16f68-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="16f68-135">Met deze invoer parameter kan de gebruiker een invoer object opgeven dat informatie bevat over de processen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="16f68-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="16f68-136">Houd er rekening mee dat het sleutel woord `ParameterSetName` kenmerk van het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de para meter `InputObject` bevat die voor deze para meter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="16f68-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="16f68-137">Houd er rekening mee dat deze para meter geen alias heeft.</span><span class="sxs-lookup"><span data-stu-id="16f68-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="16f68-138">Para meters declareren in meerdere parameter sets</span><span class="sxs-lookup"><span data-stu-id="16f68-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="16f68-139">Hoewel er een unieke para meter moet zijn voor elke parameterset, kunnen para meters deel uitmaken van meer dan één parameterset.</span><span class="sxs-lookup"><span data-stu-id="16f68-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="16f68-140">In dergelijke gevallen geeft u de gedeelde para meter een [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk declaratie voor elke set waarvan de para meter deel uitmaakt.</span><span class="sxs-lookup"><span data-stu-id="16f68-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="16f68-141">Als een para meter zich in alle parameter sets bevindt, hoeft u alleen maar één keer het parameter kenmerk te declareren en hoeft u de naam van de parameter set niet op te geven.</span><span class="sxs-lookup"><span data-stu-id="16f68-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="16f68-142">Een invoer verwerkings methode overschrijven</span><span class="sxs-lookup"><span data-stu-id="16f68-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="16f68-143">Elke cmdlet moet een invoer verwerkings methode overschrijven, meestal is dit de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="16f68-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="16f68-144">In deze cmdlet wordt de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) genegeerd, zodat de cmdlet elk wille keurig aantal processen kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="16f68-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="16f68-145">Het bevat een SELECT-instructie die een andere methode aanroept op basis van de para meter die de gebruiker heeft opgegeven.</span><span class="sxs-lookup"><span data-stu-id="16f68-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="16f68-146">De Help-methoden die worden aangeroepen door de SELECT-instructie worden hier niet beschreven, maar u kunt de implementatie ervan bekijken in het voor beeld van de volledige code in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="16f68-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="16f68-147">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="16f68-147">Code Sample</span></span>

<span data-ttu-id="16f68-148">Zie StopProcessSample04- C# voor [beeld](./stopprocesssample04-sample.md)voor de volledige voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="16f68-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="16f68-149">Object typen en-opmaak definiëren</span><span class="sxs-lookup"><span data-stu-id="16f68-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="16f68-150">Windows Power shell geeft informatie door over cmdlets met behulp van .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="16f68-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="16f68-151">Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft.</span><span class="sxs-lookup"><span data-stu-id="16f68-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="16f68-152">Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.</span><span class="sxs-lookup"><span data-stu-id="16f68-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="16f68-153">De cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="16f68-153">Building the Cmdlet</span></span>

<span data-ttu-id="16f68-154">Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren via een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="16f68-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="16f68-155">Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="16f68-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="16f68-156">De cmdlet testen</span><span class="sxs-lookup"><span data-stu-id="16f68-156">Testing the Cmdlet</span></span>

<span data-ttu-id="16f68-157">Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="16f68-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="16f68-158">Hier volgen enkele tests die laten zien hoe de para meters `ProcessId` en `InputObject` kunnen worden gebruikt om de parameter sets te testen om een proces te stoppen.</span><span class="sxs-lookup"><span data-stu-id="16f68-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="16f68-159">Als Windows Power shell is gestart, voert u de cmdlet stop-proc uit met de para meter `ProcessId` ingesteld op het stoppen van een proces op basis van de id.</span><span class="sxs-lookup"><span data-stu-id="16f68-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="16f68-160">In dit geval gebruikt de cmdlet de `ProcessId` para meter die is ingesteld om het proces te stoppen.</span><span class="sxs-lookup"><span data-stu-id="16f68-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="16f68-161">Als Windows Power shell is gestart, voert u de cmdlet stop-proc uit met de para meter `InputObject` ingesteld op het stoppen van processen voor het Notepad-object dat is opgehaald door de `Get-Process` opdracht.</span><span class="sxs-lookup"><span data-stu-id="16f68-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="16f68-162">Zie ook</span><span class="sxs-lookup"><span data-stu-id="16f68-162">See Also</span></span>

[<span data-ttu-id="16f68-163">Een cmdlet maken die het systeem wijzigt</span><span class="sxs-lookup"><span data-stu-id="16f68-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="16f68-164">Een Windows Power shell-cmdlet maken</span><span class="sxs-lookup"><span data-stu-id="16f68-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="16f68-165">[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="16f68-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="16f68-166">[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="16f68-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="16f68-167">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="16f68-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
