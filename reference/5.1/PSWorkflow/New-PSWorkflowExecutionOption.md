---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251505"
---
# <span data-ttu-id="4b54f-103">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="4b54f-103">New-PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="4b54f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4b54f-104">SYNOPSIS</span></span>

<span data-ttu-id="4b54f-105">Hiermee maakt u een-object dat sessie configuratie opties bevat voor werk stroom sessies.</span><span class="sxs-lookup"><span data-stu-id="4b54f-105">Creates an object that contains session configuration options for workflow sessions.</span></span>

## <span data-ttu-id="4b54f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4b54f-106">SYNTAX</span></span>

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="4b54f-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4b54f-107">DESCRIPTION</span></span>

<span data-ttu-id="4b54f-108">De `New-PSWorkflowExecutionOption` cmdlet maakt een object dat geavanceerde opties bevat voor werk stroom sessie configuraties. Dit zijn de sessie configuraties die zijn ontworpen voor het uitvoeren van Windows Power shell workflow-werk stromen.</span><span class="sxs-lookup"><span data-stu-id="4b54f-108">The `New-PSWorkflowExecutionOption` cmdlet creates an object that contains advanced options for workflow session configurations, that is session configurations designed to run Windows PowerShell Workflow workflows.</span></span>

<span data-ttu-id="4b54f-109">U kunt het **New psworkflowexecutionoption** -object gebruiken dat `New-PSWorkflowExecutionOption` wordt gegenereerd als de waarde van de para meter **SessionTypeOption** van cmdlets waarmee een sessie configuratie wordt gemaakt of gewijzigd, zoals de- `Register-PSSessionConfiguration` en- `Set-PSSessionConfiguration` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4b54f-109">You can use the **PSWorkflowExecutionOption** object that `New-PSWorkflowExecutionOption` generates as the value of the **SessionTypeOption** parameter of cmdlets that create or change a session configuration, such as the `Register-PSSessionConfiguration` and `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="4b54f-110">Elke para meter van de `New-PSWorkflowExecutionOption` cmdlet vertegenwoordigt een eigenschap van het werk stroom sessie configuratie optie object dat door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4b54f-110">Each parameter of the `New-PSWorkflowExecutionOption` cmdlet represents a property of the workflow session configuration option object that the cmdlet returns.</span></span> <span data-ttu-id="4b54f-111">Als u een para meter weglaat, maakt de cmdlet het object met een standaard waarde voor de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="4b54f-111">If you omit a parameter, the cmdlet creates the object with a default value for the property.</span></span>

<span data-ttu-id="4b54f-112">De `New-PSWorkflowExecutionOption` cmdlet maakt deel uit van de werk stroom functie van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4b54f-112">The `New-PSWorkflowExecutionOption` cmdlet is part of the Windows PowerShell Workflow feature.</span></span>

<span data-ttu-id="4b54f-113">U kunt ook algemene werk stroom parameters toevoegen aan deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="4b54f-113">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="4b54f-114">Zie [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)voor meer informatie over algemene werk stroom parameters.</span><span class="sxs-lookup"><span data-stu-id="4b54f-114">For more information about workflow common parameters, see [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).</span></span>

<span data-ttu-id="4b54f-115">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4b54f-115">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="4b54f-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4b54f-116">EXAMPLES</span></span>

### <span data-ttu-id="4b54f-117">Voor beeld 1: een werk stroom opties-object maken</span><span class="sxs-lookup"><span data-stu-id="4b54f-117">Example 1: Create a Workflow Options Object</span></span>

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

<span data-ttu-id="4b54f-118">Deze opdracht gebruikt de `New-PSWorkflowExecutionOption` cmdlet om de **MaxSessionsPerWorkflow** -waarde te verhogen tot 10 en de **MaxDisconnectedSessions** -waarde te verlagen tot 200.</span><span class="sxs-lookup"><span data-stu-id="4b54f-118">This command uses the `New-PSWorkflowExecutionOption` cmdlet to increase the **MaxSessionsPerWorkflow** value to 10 and decrease the **MaxDisconnectedSessions** value to 200.</span></span>

<span data-ttu-id="4b54f-119">De uitvoer toont het object dat door de cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4b54f-119">The output shows the object that the cmdlet returns.</span></span>

### <span data-ttu-id="4b54f-120">Voor beeld 2: een werk stroom opties-object gebruiken</span><span class="sxs-lookup"><span data-stu-id="4b54f-120">Example 2: Using a Workflow Options Object</span></span>

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="4b54f-121">Met de eerste twee opdrachten wordt een nieuw sessie configuratie object gemaakt en geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="4b54f-121">The first two commands create a new session configuration object and registers it.</span></span>

<span data-ttu-id="4b54f-122">De derde opdracht gebruikt de `Get-PSSessionConfiguration` cmdlet voor het ophalen van de ITWorkflows-sessie configuratie en de `Format-List` om alle eigenschappen van de sessie configuratie in een lijst weer te geven. In de uitvoer ziet u dat de werk stroom opties in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="4b54f-122">The third command uses the `Get-PSSessionConfiguration` cmdlet to the get the ITWorkflows session configuration and the `Format-List` to display all properties of the session configuration in a list.The output shows that the workflow options in the session configuration.</span></span> <span data-ttu-id="4b54f-123">De sessie configuratie heeft met name een eigenschap **MaxSessionsPerWorkflow** met de waarde 10 en een eigenschap **MaxDisconnectedSessions** met de waarde 200.</span><span class="sxs-lookup"><span data-stu-id="4b54f-123">Specifically, the session configuration has a **MaxSessionsPerWorkflow** property with a value of 10 and a **MaxDisconnectedSessions** property with a value of 200.</span></span>

## <span data-ttu-id="4b54f-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4b54f-124">PARAMETERS</span></span>

### <span data-ttu-id="4b54f-125">-ActivityProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="4b54f-125">-ActivityProcessIdleTimeoutSec</span></span>

<span data-ttu-id="4b54f-126">Hiermee wordt bepaald hoe lang elk hostproces voor activiteiten wordt behouden nadat het proces inactief wordt.</span><span class="sxs-lookup"><span data-stu-id="4b54f-126">Determines how long each activity host process is maintained after the process becomes idle.</span></span> <span data-ttu-id="4b54f-127">Wanneer het interval is verlopen, wordt het proces gesloten.</span><span class="sxs-lookup"><span data-stu-id="4b54f-127">When the interval expires, the process closes.</span></span>

<span data-ttu-id="4b54f-128">Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="4b54f-128">Enter a value in seconds.</span></span> <span data-ttu-id="4b54f-129">De standaard waarde is 60.</span><span class="sxs-lookup"><span data-stu-id="4b54f-129">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-130">-AllowedActivity</span><span class="sxs-lookup"><span data-stu-id="4b54f-130">-AllowedActivity</span></span>

<span data-ttu-id="4b54f-131">Hiermee geeft u de activiteiten op die in de sessie mogen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4b54f-131">Specifies the activities that are permitted to run in the session.</span></span>

<span data-ttu-id="4b54f-132">Voer namen van naam ruimten in die in aanmerking komen, zoals `Microsoft.Powershell.HyperV.Activities.*` .</span><span class="sxs-lookup"><span data-stu-id="4b54f-132">Enter namespace-qualified activity names, such as `Microsoft.Powershell.HyperV.Activities.*`.</span></span>
<span data-ttu-id="4b54f-133">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4b54f-133">Wildcard characters are supported.</span></span> <span data-ttu-id="4b54f-134">De standaard waarde, **PSDefaultActivities** , bevat de ingebouwde Windows Workflow Foundation activiteiten en de activiteiten die de kern-cmdlets van Windows Power shell vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="4b54f-134">The default value, **PSDefaultActivities** , includes the built-in Windows Workflow Foundation activities and the activities that represent the Windows PowerShell Core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-135">-EnableValidation</span><span class="sxs-lookup"><span data-stu-id="4b54f-135">-EnableValidation</span></span>

<span data-ttu-id="4b54f-136">Hiermee wordt gecontroleerd of alle werk stroom activiteiten in de sessie zijn opgenomen in de lijst met toegestane activiteiten.</span><span class="sxs-lookup"><span data-stu-id="4b54f-136">Verifies that all workflow activities in the session are included in the allowed activities list.</span></span>

<span data-ttu-id="4b54f-137">De standaard waarde is True.</span><span class="sxs-lookup"><span data-stu-id="4b54f-137">The default value is True.</span></span> <span data-ttu-id="4b54f-138">Als u validatie wilt uitschakelen, gebruikt u de volgende opdracht indeling: `-EnableValidation:$false` .</span><span class="sxs-lookup"><span data-stu-id="4b54f-138">To disable validation, use the following command format: `-EnableValidation:$false`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-139">-MaxActivityProcesses</span><span class="sxs-lookup"><span data-stu-id="4b54f-139">-MaxActivityProcesses</span></span>

<span data-ttu-id="4b54f-140">Hiermee geeft u het maximum aantal processen op dat in de sessie kan worden gemaakt voor de ondersteuning van werk stroom activiteiten.</span><span class="sxs-lookup"><span data-stu-id="4b54f-140">Specifies the maximum number of processes that can be created in the session to support workflow activities.</span></span> <span data-ttu-id="4b54f-141">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="4b54f-141">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-142">-MaxConnectedSessions</span><span class="sxs-lookup"><span data-stu-id="4b54f-142">-MaxConnectedSessions</span></span>

<span data-ttu-id="4b54f-143">Hiermee geeft u het maximum aantal externe sessies met een operationele status op.</span><span class="sxs-lookup"><span data-stu-id="4b54f-143">Specifies the maximum number of remote sessions that are in an operational state.</span></span> <span data-ttu-id="4b54f-144">Dit quotum wordt toegepast op sessies die zijn verbonden met alle externe knoop punten (doel computers).</span><span class="sxs-lookup"><span data-stu-id="4b54f-144">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="4b54f-145">De standaardwaarde is 100.</span><span class="sxs-lookup"><span data-stu-id="4b54f-145">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-146">-MaxDisconnectedSessions</span><span class="sxs-lookup"><span data-stu-id="4b54f-146">-MaxDisconnectedSessions</span></span>

<span data-ttu-id="4b54f-147">Hiermee geeft u het maximum aantal externe sessies in de status niet verbonden.</span><span class="sxs-lookup"><span data-stu-id="4b54f-147">Specifies the maximum number of remote sessions that are in a disconnected state.</span></span> <span data-ttu-id="4b54f-148">Dit quotum wordt toegepast op sessies die zijn verbonden met alle externe knoop punten (doel computers).</span><span class="sxs-lookup"><span data-stu-id="4b54f-148">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="4b54f-149">De standaardwaarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="4b54f-149">The default value is 1000.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-150">-MaxPersistenceStoreSizeGB</span><span class="sxs-lookup"><span data-stu-id="4b54f-150">-MaxPersistenceStoreSizeGB</span></span>

<span data-ttu-id="4b54f-151">Hiermee geeft u de maximale grootte, in gigabytes, op van de persistentie opslag die is toegewezen aan werk stromen die worden uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="4b54f-151">Specifies the maximum size, in gigabytes, of the persistence store allocated to workflows that run in the session.</span></span> <span data-ttu-id="4b54f-152">Wanneer de grootte wordt overschreden, wordt de persistentie opslag uitgebreid om alle persistente gegevens op te slaan, maar er wordt een waarschuwing weer gegeven en er wordt een bericht naar het gebeurtenis logboek van de werk stroom geschreven.</span><span class="sxs-lookup"><span data-stu-id="4b54f-152">When the size is exceeded, the persistence store is expanded to save all persisted data, but a warning is displayed and a message is written to the workflow event log.</span></span> <span data-ttu-id="4b54f-153">De standaardwaarde is 10.</span><span class="sxs-lookup"><span data-stu-id="4b54f-153">The default value is 10.</span></span>

<span data-ttu-id="4b54f-154">Het persistentie archief bevat gegevens voor alle werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="4b54f-154">The persistence store contains data for all workflow jobs.</span></span> <span data-ttu-id="4b54f-155">Met de mogelijkheid om gegevens op te slaan, kunnen de taken worden hervat zonder dat de status verloren gaat.</span><span class="sxs-lookup"><span data-stu-id="4b54f-155">The ability to store data allows the jobs to resume without losing state.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-156">-MaxRunningWorkflows</span><span class="sxs-lookup"><span data-stu-id="4b54f-156">-MaxRunningWorkflows</span></span>

<span data-ttu-id="4b54f-157">Hiermee geeft u op dat het maximum aantal werk stromen dat gelijktijdig kan worden uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="4b54f-157">Specifies that maximum number of workflows that can run in the session concurrently.</span></span>
<span data-ttu-id="4b54f-158">De standaardwaarde is 30.</span><span class="sxs-lookup"><span data-stu-id="4b54f-158">The default value is 30.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-159">-MaxSessionsPerRemoteNode</span><span class="sxs-lookup"><span data-stu-id="4b54f-159">-MaxSessionsPerRemoteNode</span></span>

<span data-ttu-id="4b54f-160">Hiermee geeft u het maximum aantal sessies op dat kan worden verbonden met elk extern knoop punt (doel computer).</span><span class="sxs-lookup"><span data-stu-id="4b54f-160">Specifies the maximum number of sessions that can be connected to each remote node (target computer).</span></span> <span data-ttu-id="4b54f-161">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="4b54f-161">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-162">-MaxSessionsPerWorkflow</span><span class="sxs-lookup"><span data-stu-id="4b54f-162">-MaxSessionsPerWorkflow</span></span>

<span data-ttu-id="4b54f-163">Hiermee geeft u het maximum aantal sessies op dat kan worden gemaakt ter ondersteuning van elke werk stroom.</span><span class="sxs-lookup"><span data-stu-id="4b54f-163">Specifies the maximum number of session that can be created to support each workflow.</span></span> <span data-ttu-id="4b54f-164">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="4b54f-164">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-165">-OutOfProcessActivity</span><span class="sxs-lookup"><span data-stu-id="4b54f-165">-OutOfProcessActivity</span></span>

<span data-ttu-id="4b54f-166">Hiermee wordt bepaald welke toegestane activiteiten (opgegeven met de para meter **AllowedActivities** ) out-of-process worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4b54f-166">Determines which allowed activities (specified by the **AllowedActivities** parameter) run out-of-process.</span></span> <span data-ttu-id="4b54f-167">De standaard waarde is **InlineScript**.</span><span class="sxs-lookup"><span data-stu-id="4b54f-167">The default value is **InlineScript**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-168">-PersistencePath</span><span class="sxs-lookup"><span data-stu-id="4b54f-168">-PersistencePath</span></span>

<span data-ttu-id="4b54f-169">Hiermee geeft u de locatie op de schijf waarop de werk stroom status en-gegevens worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="4b54f-169">Specifies the location on disk where workflow state and data are stored.</span></span> <span data-ttu-id="4b54f-170">Door de werk stroom status en-gegevens op te slaan, kunnen werk stromen worden onderbroken en hervat, en kunnen er onderbrekingen en netwerk fouten worden hersteld.</span><span class="sxs-lookup"><span data-stu-id="4b54f-170">Storing the workflow state and data allows workflows to be suspended and resumed, and to recover from interruptions and network failures.</span></span>

<span data-ttu-id="4b54f-171">De standaardwaarde is `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span><span class="sxs-lookup"><span data-stu-id="4b54f-171">The default value is `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-172">-PersistWithEncryption</span><span class="sxs-lookup"><span data-stu-id="4b54f-172">-PersistWithEncryption</span></span>

<span data-ttu-id="4b54f-173">Geeft aan dat de werk stroom de gegevens in de opslag voor persistentie versleutelt.</span><span class="sxs-lookup"><span data-stu-id="4b54f-173">Indicates that the workflow encrypts the data in the persistence store.</span></span> <span data-ttu-id="4b54f-174">Overweeg het gebruik van deze functie bij het opslaan van persistentie gegevens in een netwerk share.</span><span class="sxs-lookup"><span data-stu-id="4b54f-174">Consider using this feature when storing persistence data in a network share.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-175">-RemoteNodeSessionIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="4b54f-175">-RemoteNodeSessionIdleTimeoutSec</span></span>

<span data-ttu-id="4b54f-176">Hiermee geeft u op hoe lang een sessie die is verbonden met een extern knoop punt (doel computer) wordt onderhouden als deze niet actief is.</span><span class="sxs-lookup"><span data-stu-id="4b54f-176">Specifies how long a session that is connected to a remote node (target computer) is maintained if it is idle.</span></span>

<span data-ttu-id="4b54f-177">Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="4b54f-177">Enter a value in seconds.</span></span> <span data-ttu-id="4b54f-178">De standaard waarde is 60.</span><span class="sxs-lookup"><span data-stu-id="4b54f-178">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-179">-SessionThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4b54f-179">-SessionThrottleLimit</span></span>

<span data-ttu-id="4b54f-180">Hiermee geeft u op hoeveel bewerkingen worden gemaakt voor de ondersteuning van alle werk stromen die in de sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="4b54f-180">Specifies how many operations are created to support all workflows started in the session.</span></span> <span data-ttu-id="4b54f-181">De standaardwaarde is 100.</span><span class="sxs-lookup"><span data-stu-id="4b54f-181">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-182">-WorkflowShutdownTimeoutMSec</span><span class="sxs-lookup"><span data-stu-id="4b54f-182">-WorkflowShutdownTimeoutMSec</span></span>

<span data-ttu-id="4b54f-183">Hiermee geeft u op hoe lang de sessie wordt behouden nadat alle werk stromen in de sessie geforceerd zijn onderbroken.</span><span class="sxs-lookup"><span data-stu-id="4b54f-183">Specifies how long the session is maintained after all workflows in the session are forcibly suspended.</span></span> <span data-ttu-id="4b54f-184">Wanneer de time-out is verlopen, wordt de sessie door Windows Power shell gesloten, zelfs als alle werk stromen nog niet zijn onderbroken.</span><span class="sxs-lookup"><span data-stu-id="4b54f-184">When the timeout expires, Windows PowerShell closes the session, even if all workflows are not yet suspended.</span></span>

<span data-ttu-id="4b54f-185">Voer een waarde in milliseconden in.</span><span class="sxs-lookup"><span data-stu-id="4b54f-185">Enter a value in milliseconds.</span></span>
<span data-ttu-id="4b54f-186">De standaardwaarde is 500.</span><span class="sxs-lookup"><span data-stu-id="4b54f-186">The default value is 500.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4b54f-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b54f-187">CommonParameters</span></span>

<span data-ttu-id="4b54f-188">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4b54f-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b54f-189">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4b54f-189">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4b54f-190">INVOER</span><span class="sxs-lookup"><span data-stu-id="4b54f-190">INPUTS</span></span>

### <span data-ttu-id="4b54f-191">Geen</span><span class="sxs-lookup"><span data-stu-id="4b54f-191">None</span></span>

<span data-ttu-id="4b54f-192">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b54f-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4b54f-193">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4b54f-193">OUTPUTS</span></span>

### <span data-ttu-id="4b54f-194">Micro soft. Power shell. commands. New psworkflowexecutionoption</span><span class="sxs-lookup"><span data-stu-id="4b54f-194">Microsoft.PowerShell.Commands.PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="4b54f-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4b54f-195">NOTES</span></span>

<span data-ttu-id="4b54f-196">Wanneer de maximum waarde die is ingesteld met een optie wordt overschreden, mislukt de opdracht voor het maken van een instantie in de sessie, tenzij vermeld in de parameter beschrijving.</span><span class="sxs-lookup"><span data-stu-id="4b54f-196">When the maximum value set by an option is exceeded, the command to create another instance in the session fails, unless noted in the parameter description.</span></span> <span data-ttu-id="4b54f-197">Als de waarde van **MaxConnectedSessions** bijvoorbeeld 100 is.</span><span class="sxs-lookup"><span data-stu-id="4b54f-197">For example, if the value of **MaxConnectedSessions** is 100.</span></span> <span data-ttu-id="4b54f-198">De opdracht voor het maken van de 101st-sessie naar een extern knoop punt (doel computer) is mislukt.</span><span class="sxs-lookup"><span data-stu-id="4b54f-198">The command to create the 101st session to a remote node (target computer) fails.</span></span>

<span data-ttu-id="4b54f-199">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="4b54f-199">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="4b54f-200">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="4b54f-200">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="4b54f-201">Met name de eigenschappen van sessie configuraties die een **PSWorkflowExecutionOptions** -object bevatten, variëren op basis van de waarden van de werk stroom optie.</span><span class="sxs-lookup"><span data-stu-id="4b54f-201">In particular, the properties of session configurations that include a **PSWorkflowExecutionOptions** object vary based on the workflow option values.</span></span> <span data-ttu-id="4b54f-202">Als de sessie configuratie bijvoorbeeld een **PSWorkflowExecutionOptions** -object bevat dat een niet-standaard waarde voor de eigenschap **SessionThrottleLimit** instelt, heeft de sessie configuratie een **SessionThrottleLimit** -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="4b54f-202">For example, if the session configuration includes a **PSWorkflowExecutionOptions** object that sets a non-default value for the **SessionThrottleLimit** property, the session configuration has a **SessionThrottleLimit** property.</span></span> <span data-ttu-id="4b54f-203">Anders is dit niet het geval.</span><span class="sxs-lookup"><span data-stu-id="4b54f-203">Otherwise, it does not.</span></span>

## <span data-ttu-id="4b54f-204">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4b54f-204">RELATED LINKS</span></span>

[<span data-ttu-id="4b54f-205">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="4b54f-205">New-PSWorkflowSession</span></span>](New-PSWorkflowSession.md)

[<span data-ttu-id="4b54f-206">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="4b54f-206">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="4b54f-207">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b54f-207">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)
