---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388462"
---
# <span data-ttu-id="36b23-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="36b23-103">Suspend-Job</span></span>

## <span data-ttu-id="36b23-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="36b23-104">SYNOPSIS</span></span>
<span data-ttu-id="36b23-105">Stopt werk stroom taken tijdelijk.</span><span class="sxs-lookup"><span data-stu-id="36b23-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="36b23-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="36b23-106">SYNTAX</span></span>

### <span data-ttu-id="36b23-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="36b23-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36b23-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="36b23-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36b23-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="36b23-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36b23-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="36b23-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36b23-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="36b23-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36b23-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="36b23-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="36b23-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="36b23-113">DESCRIPTION</span></span>

<span data-ttu-id="36b23-114">De `Suspend-Job` cmdlet suspendeert werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="36b23-114">The `Suspend-Job` cmdlet suspends workflow jobs.</span></span> <span data-ttu-id="36b23-115">Suspend betekent dat een werk stroom taak tijdelijk moet worden onderbroken of onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span> <span data-ttu-id="36b23-116">Met deze cmdlet kunnen gebruikers die werk stromen uitvoeren, de werk stroom onderbreken.</span><span class="sxs-lookup"><span data-stu-id="36b23-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span> <span data-ttu-id="36b23-117">Dit is een aanvulling op de activiteit Suspend-workflow https://go.microsoft.com/fwlink/?LinkId=267141 , een opdracht in de werk stroom waarmee de werk stroom wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="36b23-118">De `Suspend-Job` cmdlet werkt alleen op werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="36b23-118">The `Suspend-Job` cmdlet works only on workflow jobs.</span></span> <span data-ttu-id="36b23-119">Deze functie werkt niet op standaard achtergrond taken, zoals die worden gestart met behulp van de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36b23-119">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="36b23-120">Zoek naar een waarde van PSWorkflowJob in de eigenschap **PSJobTypeName** van de taak om een werk stroom taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="36b23-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="36b23-121">`Suspend-Job`Zie de Help-onderwerpen voor het aangepaste taak type om te bepalen of een bepaald aangepast taak type de cmdlet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="36b23-121">To determine whether a particular custom job type supports the `Suspend-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="36b23-122">Wanneer u een werk stroom taak uitbreekt, wordt de werk stroom taak uitgevoerd op het volgende controle punt, wordt deze onderbroken en wordt er onmiddellijk een werk stroom taak object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36b23-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span> <span data-ttu-id="36b23-123">Als u wilt wachten tot de onderbreking is voltooid, gebruikt u de para meter **wait** van `Suspend-Job` of de `Wait-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36b23-123">To wait for the suspension to complete before getting the job, use the **Wait** parameter of `Suspend-Job` or the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="36b23-124">Wanneer de werk stroom taak is onderbroken, wordt de waarde van de eigenschap **State** van de taak onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="36b23-125">Het onderbreken van de wacht stand is afhankelijk van controle punten.</span><span class="sxs-lookup"><span data-stu-id="36b23-125">Suspending correctly relies on checkpoints.</span></span> <span data-ttu-id="36b23-126">De huidige taak status, meta gegevens en uitvoer worden opgeslagen in het controle punt zodat de werk stroom taak kan worden hervat zonder dat de status of gegevens verloren gaan.</span><span class="sxs-lookup"><span data-stu-id="36b23-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span> <span data-ttu-id="36b23-127">Als de werk stroom taak geen controle punten heeft, kan deze niet goed worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span> <span data-ttu-id="36b23-128">Als u controle punten wilt toevoegen aan een werk stroom die u uitvoert, gebruikt u de algemene para meter **PSPersist** workflow.</span><span class="sxs-lookup"><span data-stu-id="36b23-128">To add checkpoints to a workflow that you are running, use the **PSPersist** workflow common parameter.</span></span> <span data-ttu-id="36b23-129">U kunt de para meter **Force** gebruiken om een werk stroom taak onmiddellijk te onderbreken en een werk stroom taak te onderbreken die geen controle punten heeft, maar de actie kan leiden tot verlies van status en gegevens.</span><span class="sxs-lookup"><span data-stu-id="36b23-129">You can use the **Force** parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="36b23-130">Voordat u een taak-cmdlet voor een aangepast taak type gebruikt, zoals een werk stroom taak ( **PSWorkflowJob** ), moet u de module importeren die het aangepaste taak type ondersteunt, hetzij met behulp van de cmdlet, hetzij met behulp van `Import-Module` een cmdlet in de module.</span><span class="sxs-lookup"><span data-stu-id="36b23-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the `Import-Module` cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="36b23-131">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="36b23-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="36b23-132">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="36b23-132">EXAMPLES</span></span>

### <span data-ttu-id="36b23-133">Voor beeld 1: een werk stroom taak op naam onderbreken</span><span class="sxs-lookup"><span data-stu-id="36b23-133">Example 1: Suspend a workflow job by name</span></span>

<span data-ttu-id="36b23-134">In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt.</span><span class="sxs-lookup"><span data-stu-id="36b23-134">This example shows how to suspend a workflow job.</span></span>

<span data-ttu-id="36b23-135">Met de eerste opdracht wordt de `Get-SystemLog` werk stroom gemaakt.</span><span class="sxs-lookup"><span data-stu-id="36b23-135">The first command creates the `Get-SystemLog` workflow.</span></span> <span data-ttu-id="36b23-136">De werk stroom gebruikt de `CheckPoint-Workflow` activiteit om een controle punt in de werk stroom te definiëren.</span><span class="sxs-lookup"><span data-stu-id="36b23-136">The workflow uses the `CheckPoint-Workflow` activity to define a checkpoint in the workflow.</span></span>

<span data-ttu-id="36b23-137">De tweede opdracht maakt gebruik van de para meter **AsJob** die gemeen schappelijk is voor alle werk stromen om de `Get-SystemLog` werk stroom als achtergrond taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="36b23-137">The second command uses the **AsJob** parameter that is common to all workflows to run the `Get-SystemLog` workflow as a background job.</span></span> <span data-ttu-id="36b23-138">De opdracht gebruikt de algemene para meter **JobName** workflow om een beschrijvende naam voor de werk stroom taak op te geven.</span><span class="sxs-lookup"><span data-stu-id="36b23-138">The command uses the **JobName** workflow common parameter to specify a friendly name for the workflow job.</span></span>

<span data-ttu-id="36b23-139">De derde opdracht gebruikt de `Get-Job` cmdlet om de `Get-SystemLogJob` werk stroom taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="36b23-139">The third command uses the `Get-Job` cmdlet to get the `Get-SystemLogJob` workflow job.</span></span> <span data-ttu-id="36b23-140">In de uitvoer ziet u dat de waarde van de eigenschap **PSJobTypeName** PSWorkflowJob is.</span><span class="sxs-lookup"><span data-stu-id="36b23-140">The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.</span></span>

<span data-ttu-id="36b23-141">De vierde opdracht gebruikt de `Suspend-Job` cmdlet om de taak te onderbreken `Get-SystemLogJob` .</span><span class="sxs-lookup"><span data-stu-id="36b23-141">The fourth command uses the `Suspend-Job` cmdlet to suspend the `Get-SystemLogJob` job.</span></span> <span data-ttu-id="36b23-142">De taak wordt uitgevoerd op het controle punt en wordt vervolgens onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-142">The job runs to the checkpoint and then suspends.</span></span>

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### <span data-ttu-id="36b23-143">Voor beeld 2: een werk stroom taak opschorten en hervatten</span><span class="sxs-lookup"><span data-stu-id="36b23-143">Example 2: Suspend and resume a workflow job</span></span>

<span data-ttu-id="36b23-144">In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt en hervat.</span><span class="sxs-lookup"><span data-stu-id="36b23-144">This example shows how to suspend and resume a workflow job.</span></span>

<span data-ttu-id="36b23-145">Met de eerste opdracht wordt de LogWorkflowJob-taak onderbroken. De opdracht wordt direct geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36b23-145">The first command suspends the LogWorkflowJob job.The command returns immediately.</span></span> <span data-ttu-id="36b23-146">In de uitvoer ziet u dat de werk stroom taak nog actief is, ook al wordt deze onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-146">The output shows that the workflow job is still running, even though it is being suspended.</span></span>

<span data-ttu-id="36b23-147">De tweede opdracht gebruikt de `Get-Job` cmdlet om de LogWorkflowJob-taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="36b23-147">The second command uses the `Get-Job` cmdlet to get the LogWorkflowJob job.</span></span> <span data-ttu-id="36b23-148">In de uitvoer ziet u dat de werk stroom taak is onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-148">The output shows that the workflow job suspended successfully.</span></span>

<span data-ttu-id="36b23-149">De derde opdracht gebruikt de `Get-Job` cmdlet om de LogWorkflowJob-taak en de `Resume-Job` cmdlet te krijgen om deze te hervatten.</span><span class="sxs-lookup"><span data-stu-id="36b23-149">The third command uses the `Get-Job` cmdlet to get the LogWorkflowJob job and the `Resume-Job` cmdlet to resume it.</span></span> <span data-ttu-id="36b23-150">In de uitvoer ziet u dat de werk stroom taak is hervat en nu wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36b23-150">The output shows that the workflow job resumed successfully and is now running.</span></span>

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### <span data-ttu-id="36b23-151">Voor beeld 3: een werk stroom taak op een externe computer onderbreken</span><span class="sxs-lookup"><span data-stu-id="36b23-151">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="36b23-152">Met deze opdracht wordt de `Invoke-Command` cmdlet gebruikt om een werk stroom taak op de externe computer Srv01 te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="36b23-152">This command uses the `Invoke-Command` cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span> <span data-ttu-id="36b23-153">De waarde van de **filter** parameter is een hash-tabel waarin een CustomID-waarde wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="36b23-153">The value of the **Filter** parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="36b23-154">Dit **CustomID** is taak-meta gegevens ( **PSPrivateMetadata** ).</span><span class="sxs-lookup"><span data-stu-id="36b23-154">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="36b23-155">Voor beeld 4: wachten tot de werk stroom taak is onderbroken</span><span class="sxs-lookup"><span data-stu-id="36b23-155">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="36b23-156">Met deze opdracht wordt de werk stroom taak VersionCheck onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-156">This command suspends the VersionCheck workflow job.</span></span> <span data-ttu-id="36b23-157">De opdracht gebruikt de **wait** -para meter om te wachten tot de werk stroom taak is onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-157">The command uses the **Wait** parameter to wait until the workflow job is suspended.</span></span> <span data-ttu-id="36b23-158">Wanneer de werk stroom taak wordt uitgevoerd op het volgende controle punt en is onderbroken, wordt de opdracht beëindigd en wordt het taak object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36b23-158">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="36b23-159">Voor beeld 5: een werk stroom taak geforceerd onderbreken</span><span class="sxs-lookup"><span data-stu-id="36b23-159">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="36b23-160">Met deze opdracht wordt de werk stroom taak geforceerd onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-160">This command suspends the Maintenance workflow job forcibly.</span></span> <span data-ttu-id="36b23-161">De onderhouds taak heeft geen controle punten.</span><span class="sxs-lookup"><span data-stu-id="36b23-161">The Maintenance job does not have checkpoints.</span></span> <span data-ttu-id="36b23-162">Het kan niet juist worden onderbroken en wordt mogelijk niet goed hervat.</span><span class="sxs-lookup"><span data-stu-id="36b23-162">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="36b23-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36b23-163">PARAMETERS</span></span>

### <span data-ttu-id="36b23-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="36b23-164">-Filter</span></span>

<span data-ttu-id="36b23-165">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="36b23-165">Specifies a hash table of conditions.</span></span> <span data-ttu-id="36b23-166">Met deze cmdlet worden taken opgeschort die voldoen aan alle voor waarden.</span><span class="sxs-lookup"><span data-stu-id="36b23-166">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="36b23-167">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="36b23-167">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-168">-Force</span><span class="sxs-lookup"><span data-stu-id="36b23-168">-Force</span></span>

<span data-ttu-id="36b23-169">Hiermee wordt de werk stroom taak onmiddellijk onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-169">Suspends the workflow job immediately.</span></span> <span data-ttu-id="36b23-170">Deze actie kan leiden tot verlies van status en gegevens.</span><span class="sxs-lookup"><span data-stu-id="36b23-170">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="36b23-171">Standaard kan `Suspend-Job` de werk stroom taak worden uitgevoerd tot het volgende controle punt en wordt deze vervolgens onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-171">By default, `Suspend-Job` lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="36b23-172">U kunt deze para meter ook gebruiken om werk stroom taken te onderbreken die geen controle punten hebben.</span><span class="sxs-lookup"><span data-stu-id="36b23-172">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-173">-Id</span><span class="sxs-lookup"><span data-stu-id="36b23-173">-Id</span></span>

<span data-ttu-id="36b23-174">Hiermee geeft u de Id's op van taken die met deze cmdlet worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-174">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="36b23-175">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="36b23-175">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="36b23-176">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="36b23-176">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="36b23-177">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="36b23-177">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="36b23-178">Gebruik de cmdlet om de ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="36b23-178">To find the ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-179">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="36b23-179">-InstanceId</span></span>

<span data-ttu-id="36b23-180">Hiermee geeft u de exemplaar-Id's op van de taken die met deze cmdlet worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-180">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="36b23-181">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="36b23-181">The default is all jobs.</span></span>

<span data-ttu-id="36b23-182">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="36b23-182">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="36b23-183">Gebruik om de exemplaar-ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="36b23-183">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-184">-Taak</span><span class="sxs-lookup"><span data-stu-id="36b23-184">-Job</span></span>

<span data-ttu-id="36b23-185">Hiermee geeft u de werk stroom taken op die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="36b23-185">Specifies the workflow jobs that this cmdlet stops.</span></span> <span data-ttu-id="36b23-186">Voer een variabele in die de werk stroom taken bevat of een opdracht waarmee de werk stroom taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36b23-186">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span> <span data-ttu-id="36b23-187">U kunt werk stroom taken ook door sluizen naar de `Suspend-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36b23-187">You can also pipe workflow jobs to the `Suspend-Job` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-188">-Name</span><span class="sxs-lookup"><span data-stu-id="36b23-188">-Name</span></span>

<span data-ttu-id="36b23-189">Hiermee geeft u beschrijvende namen op van taken die met deze cmdlet worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-189">Specifies friendly names of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="36b23-190">Voer een of meer werk stroom taak namen in.</span><span class="sxs-lookup"><span data-stu-id="36b23-190">Enter one or more workflow job names.</span></span>
<span data-ttu-id="36b23-191">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="36b23-191">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-192">-Status</span><span class="sxs-lookup"><span data-stu-id="36b23-192">-State</span></span>

<span data-ttu-id="36b23-193">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="36b23-193">Specifies a job state.</span></span> <span data-ttu-id="36b23-194">Met deze cmdlet worden alleen taken in de opgegeven status gestopt.</span><span class="sxs-lookup"><span data-stu-id="36b23-194">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="36b23-195">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="36b23-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="36b23-196">NotStarted</span><span class="sxs-lookup"><span data-stu-id="36b23-196">NotStarted</span></span>
- <span data-ttu-id="36b23-197">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="36b23-197">Running</span></span>
- <span data-ttu-id="36b23-198">Voltooid</span><span class="sxs-lookup"><span data-stu-id="36b23-198">Completed</span></span>
- <span data-ttu-id="36b23-199">Mislukt</span><span class="sxs-lookup"><span data-stu-id="36b23-199">Failed</span></span>
- <span data-ttu-id="36b23-200">Gestopt</span><span class="sxs-lookup"><span data-stu-id="36b23-200">Stopped</span></span>
- <span data-ttu-id="36b23-201">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="36b23-201">Blocked</span></span>
- <span data-ttu-id="36b23-202">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="36b23-202">Suspended</span></span>
- <span data-ttu-id="36b23-203">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="36b23-203">Disconnected</span></span>
- <span data-ttu-id="36b23-204">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="36b23-204">Suspending</span></span>
- <span data-ttu-id="36b23-205">Stoppen</span><span class="sxs-lookup"><span data-stu-id="36b23-205">Stopping</span></span>

<span data-ttu-id="36b23-206">`Suspend-Job` Hiermee worden alleen werk stroom taken met de status **actief** onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-206">`Suspend-Job` suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="36b23-207">Zie [JobState Enumeration](/dotnet/api/system.management.automation.jobstate)(Engelstalig) voor meer informatie over de status van een taak.</span><span class="sxs-lookup"><span data-stu-id="36b23-207">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-208">-Wachten</span><span class="sxs-lookup"><span data-stu-id="36b23-208">-Wait</span></span>

<span data-ttu-id="36b23-209">Geeft aan dat deze cmdlet de opdracht prompt onderdrukt totdat de werk stroom taak de status onderbroken heeft.</span><span class="sxs-lookup"><span data-stu-id="36b23-209">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span> <span data-ttu-id="36b23-210">Standaard wordt `Suspend-Job` direct geretourneerd, zelfs als de werk stroom taak nog niet de status onderbroken heeft.</span><span class="sxs-lookup"><span data-stu-id="36b23-210">By default, `Suspend-Job` returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="36b23-211">De **wait** -para meter is gelijk aan het sluizen van een `Suspend-Job` opdracht aan de `Wait-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36b23-211">The **Wait** parameter is equivalent to piping a `Suspend-Job` command to the `Wait-Job` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-212">-Confirm</span><span class="sxs-lookup"><span data-stu-id="36b23-212">-Confirm</span></span>

<span data-ttu-id="36b23-213">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="36b23-213">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-214">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="36b23-214">-WhatIf</span></span>

<span data-ttu-id="36b23-215">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="36b23-215">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="36b23-216">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36b23-216">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36b23-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36b23-217">CommonParameters</span></span>

<span data-ttu-id="36b23-218">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36b23-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36b23-219">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36b23-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36b23-220">INVOER</span><span class="sxs-lookup"><span data-stu-id="36b23-220">INPUTS</span></span>

### <span data-ttu-id="36b23-221">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="36b23-221">System.Management.Automation.Job</span></span>

<span data-ttu-id="36b23-222">U kunt alle typen taken naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="36b23-222">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="36b23-223">Als er echter `Suspend-Job` een taak van een niet-ondersteund type wordt opgehaald, wordt een afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36b23-223">However, if `Suspend-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="36b23-224">UITVOER</span><span class="sxs-lookup"><span data-stu-id="36b23-224">OUTPUTS</span></span>

### <span data-ttu-id="36b23-225">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="36b23-225">System.Management.Automation.Job</span></span>
<span data-ttu-id="36b23-226">Met deze cmdlet worden de taken geretourneerd die zijn onderbroken.</span><span class="sxs-lookup"><span data-stu-id="36b23-226">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="36b23-227">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="36b23-227">NOTES</span></span>

- <span data-ttu-id="36b23-228">Het mechanisme en de locatie voor het opslaan van een onderbroken taak kunnen variëren afhankelijk van het taak type.</span><span class="sxs-lookup"><span data-stu-id="36b23-228">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="36b23-229">Onderbroken werk stroom taken worden bijvoorbeeld standaard opgeslagen in een plat bestands archief, maar kunnen ook worden opgeslagen in een Data Base.</span><span class="sxs-lookup"><span data-stu-id="36b23-229">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
- <span data-ttu-id="36b23-230">Als u een werk stroom taak indient die niet wordt uitgevoerd, `Suspend-Job` wordt een waarschuwings bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36b23-230">If you submit a workflow job that is not in the Running state, `Suspend-Job` displays a warning message.</span></span> <span data-ttu-id="36b23-231">Als u de waarschuwing wilt onderdrukken, gebruikt u de gemeen schappelijke **WarningAction** para meter met de waarde SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="36b23-231">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="36b23-232">Als een taak niet van een type is dat opschorting ondersteunt, `Suspend-Job` wordt een afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36b23-232">If a job is not of a type that supports suspending, `Suspend-Job` returns a terminating error.</span></span>

- <span data-ttu-id="36b23-233">Gebruik de para meter **State** van de cmdlet om werk stroom taken met de status onderbroken te krijgen om de werk stroom taken te vinden die zijn onderbroken `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="36b23-233">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get workflow jobs in the Suspended state.</span></span>
- <span data-ttu-id="36b23-234">Sommige taak typen hebben opties of eigenschappen die verhinderen dat Windows Power shell de taak onderbreekt.</span><span class="sxs-lookup"><span data-stu-id="36b23-234">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="36b23-235">Als er wordt geprobeerd de taak te onderbreken, controleert u of de taak opties en eigenschappen het blok keren toestaan.</span><span class="sxs-lookup"><span data-stu-id="36b23-235">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="36b23-236">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="36b23-236">RELATED LINKS</span></span>

[<span data-ttu-id="36b23-237">Get-job</span><span class="sxs-lookup"><span data-stu-id="36b23-237">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="36b23-238">Receive-job</span><span class="sxs-lookup"><span data-stu-id="36b23-238">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="36b23-239">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="36b23-239">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="36b23-240">Resume-job</span><span class="sxs-lookup"><span data-stu-id="36b23-240">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="36b23-241">Begin taak</span><span class="sxs-lookup"><span data-stu-id="36b23-241">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="36b23-242">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="36b23-242">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="36b23-243">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="36b23-243">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="36b23-244">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="36b23-244">Wait-Job</span></span>](Wait-Job.md)
