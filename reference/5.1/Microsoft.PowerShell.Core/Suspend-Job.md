---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250132"
---
# <span data-ttu-id="99a79-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="99a79-103">Suspend-Job</span></span>

## <span data-ttu-id="99a79-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="99a79-104">SYNOPSIS</span></span>
<span data-ttu-id="99a79-105">Stopt werk stroom taken tijdelijk.</span><span class="sxs-lookup"><span data-stu-id="99a79-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="99a79-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="99a79-106">SYNTAX</span></span>

### <span data-ttu-id="99a79-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="99a79-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="99a79-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="99a79-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="99a79-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="99a79-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="99a79-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="99a79-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="99a79-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="99a79-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="99a79-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="99a79-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="99a79-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="99a79-113">DESCRIPTION</span></span>
<span data-ttu-id="99a79-114">Met de cmdlet **suspend-job** worden werk stroom taken onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-114">The **Suspend-Job** cmdlet suspends workflow jobs.</span></span>
<span data-ttu-id="99a79-115">Suspend betekent dat een werk stroom taak tijdelijk moet worden onderbroken of onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span>
<span data-ttu-id="99a79-116">Met deze cmdlet kunnen gebruikers die werk stromen uitvoeren, de werk stroom onderbreken.</span><span class="sxs-lookup"><span data-stu-id="99a79-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span>
<span data-ttu-id="99a79-117">Dit is een aanvulling op de activiteit Suspend-workflow https://go.microsoft.com/fwlink/?LinkId=267141 , een opdracht in de werk stroom waarmee de werk stroom wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="99a79-118">De cmdlet **suspend-job** werkt alleen op werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="99a79-118">The **Suspend-Job** cmdlet works only on workflow jobs.</span></span>
<span data-ttu-id="99a79-119">Deze functie werkt niet op standaard achtergrond taken, zoals die worden gestart met behulp van de cmdlet Start-Job.</span><span class="sxs-lookup"><span data-stu-id="99a79-119">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="99a79-120">Zoek naar een waarde van PSWorkflowJob in de eigenschap **PSJobTypeName** van de taak om een werk stroom taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="99a79-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="99a79-121">Zie de Help-onderwerpen voor het aangepaste taak type om te bepalen of een bepaald aangepast taak type de cmdlet **pause-job** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="99a79-121">To determine whether a particular custom job type supports the **Suspend-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="99a79-122">Wanneer u een werk stroom taak uitbreekt, wordt de werk stroom taak uitgevoerd op het volgende controle punt, wordt deze onderbroken en wordt er onmiddellijk een werk stroom taak object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="99a79-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span>
<span data-ttu-id="99a79-123">Als u wilt wachten tot de onderbreking is voltooid voordat u de taak kunt ophalen, gebruikt u de para meter *wait* of **pause-job** of de cmdlet Wait-Job.</span><span class="sxs-lookup"><span data-stu-id="99a79-123">To wait for the suspension to complete before getting the job, use the *Wait* parameter of **Suspend-Job** or the Wait-Job cmdlet.</span></span>
<span data-ttu-id="99a79-124">Wanneer de werk stroom taak is onderbroken, wordt de waarde van de eigenschap **State** van de taak onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="99a79-125">Het onderbreken van de wacht stand is afhankelijk van controle punten.</span><span class="sxs-lookup"><span data-stu-id="99a79-125">Suspending correctly relies on checkpoints.</span></span>
<span data-ttu-id="99a79-126">De huidige taak status, meta gegevens en uitvoer worden opgeslagen in het controle punt zodat de werk stroom taak kan worden hervat zonder dat de status of gegevens verloren gaan.</span><span class="sxs-lookup"><span data-stu-id="99a79-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span>
<span data-ttu-id="99a79-127">Als de werk stroom taak geen controle punten heeft, kan deze niet goed worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span>
<span data-ttu-id="99a79-128">Als u controle punten wilt toevoegen aan een werk stroom die u uitvoert, gebruikt u de algemene para meter *PSPersist* workflow.</span><span class="sxs-lookup"><span data-stu-id="99a79-128">To add checkpoints to a workflow that you are running, use the *PSPersist* workflow common parameter.</span></span>
<span data-ttu-id="99a79-129">U kunt de para meter *Force* gebruiken om een werk stroom taak onmiddellijk te onderbreken en een werk stroom taak te onderbreken die geen controle punten heeft, maar de actie kan leiden tot verlies van status en gegevens.</span><span class="sxs-lookup"><span data-stu-id="99a79-129">You can use the *Force* parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="99a79-130">Voordat u een taak-cmdlet voor een aangepast taak type gebruikt, zoals een werk stroom taak ( **PSWorkflowJob** ), moet u de module importeren die het aangepaste taak type ondersteunt, hetzij met behulp van de cmdlet Import-Module, hetzij met behulp van een cmdlet in de module.</span><span class="sxs-lookup"><span data-stu-id="99a79-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the Import-Module cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="99a79-131">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="99a79-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="99a79-132">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="99a79-132">EXAMPLES</span></span>

### <span data-ttu-id="99a79-133">Voor beeld 1: een werk stroom taak op naam onderbreken</span><span class="sxs-lookup"><span data-stu-id="99a79-133">Example 1: Suspend a workflow job by name</span></span>

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

<span data-ttu-id="99a79-134">In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt.</span><span class="sxs-lookup"><span data-stu-id="99a79-134">This example shows how to suspend a workflow job.</span></span>

### <span data-ttu-id="99a79-135">Voor beeld 2: een werk stroom taak opschorten en hervatten</span><span class="sxs-lookup"><span data-stu-id="99a79-135">Example 2: Suspend and resume a workflow job</span></span>

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

<span data-ttu-id="99a79-136">In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt en hervat.</span><span class="sxs-lookup"><span data-stu-id="99a79-136">This example shows how to suspend and resume a workflow job.</span></span>

### <span data-ttu-id="99a79-137">Voor beeld 3: een werk stroom taak op een externe computer onderbreken</span><span class="sxs-lookup"><span data-stu-id="99a79-137">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="99a79-138">Met deze opdracht wordt de cmdlet Invoke-Command gebruikt om een werk stroom taak op de externe computer Srv01 te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="99a79-138">This command uses the Invoke-Command cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span>
<span data-ttu-id="99a79-139">De waarde van de *filter* parameter is een hash-tabel waarin een CustomID-waarde wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="99a79-139">The value of the *Filter* parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="99a79-140">Dit **CustomID** is taak-meta gegevens ( **PSPrivateMetadata** ).</span><span class="sxs-lookup"><span data-stu-id="99a79-140">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="99a79-141">Voor beeld 4: wachten tot de werk stroom taak is onderbroken</span><span class="sxs-lookup"><span data-stu-id="99a79-141">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="99a79-142">Met deze opdracht wordt de werk stroom taak VersionCheck onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-142">This command suspends the VersionCheck workflow job.</span></span>
<span data-ttu-id="99a79-143">De opdracht gebruikt de *wait* -para meter om te wachten tot de werk stroom taak is onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-143">The command uses the *Wait* parameter to wait until the workflow job is suspended.</span></span>
<span data-ttu-id="99a79-144">Wanneer de werk stroom taak wordt uitgevoerd op het volgende controle punt en is onderbroken, wordt de opdracht beëindigd en wordt het taak object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="99a79-144">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="99a79-145">Voor beeld 5: een werk stroom taak geforceerd onderbreken</span><span class="sxs-lookup"><span data-stu-id="99a79-145">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="99a79-146">Met deze opdracht wordt de werk stroom taak geforceerd onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-146">This command suspends the Maintenance workflow job forcibly.</span></span>
<span data-ttu-id="99a79-147">De onderhouds taak heeft geen controle punten.</span><span class="sxs-lookup"><span data-stu-id="99a79-147">The Maintenance job does not have checkpoints.</span></span>
<span data-ttu-id="99a79-148">Het kan niet juist worden onderbroken en wordt mogelijk niet goed hervat.</span><span class="sxs-lookup"><span data-stu-id="99a79-148">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="99a79-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="99a79-149">PARAMETERS</span></span>

### <span data-ttu-id="99a79-150">-Filter</span><span class="sxs-lookup"><span data-stu-id="99a79-150">-Filter</span></span>
<span data-ttu-id="99a79-151">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="99a79-151">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="99a79-152">Met deze cmdlet worden taken opgeschort die voldoen aan alle voor waarden.</span><span class="sxs-lookup"><span data-stu-id="99a79-152">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="99a79-153">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="99a79-153">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="99a79-154">-Force</span><span class="sxs-lookup"><span data-stu-id="99a79-154">-Force</span></span>
<span data-ttu-id="99a79-155">Hiermee wordt de werk stroom taak onmiddellijk onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-155">Suspends the workflow job immediately.</span></span>
<span data-ttu-id="99a79-156">Deze actie kan leiden tot verlies van status en gegevens.</span><span class="sxs-lookup"><span data-stu-id="99a79-156">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="99a79-157">Standaard kan de werk stroom **taak worden uitgevoerd** tot het volgende controle punt. vervolgens wordt de taak onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-157">By default, **Suspend-Job** lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="99a79-158">U kunt deze para meter ook gebruiken om werk stroom taken te onderbreken die geen controle punten hebben.</span><span class="sxs-lookup"><span data-stu-id="99a79-158">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

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

### <span data-ttu-id="99a79-159">-Id</span><span class="sxs-lookup"><span data-stu-id="99a79-159">-Id</span></span>
<span data-ttu-id="99a79-160">Hiermee geeft u de Id's op van taken die met deze cmdlet worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-160">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="99a79-161">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="99a79-161">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="99a79-162">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="99a79-162">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="99a79-163">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="99a79-163">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="99a79-164">Gebruik de cmdlet Get-Job om de ID van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="99a79-164">To find the ID of a job, use the Get-Job cmdlet.</span></span>

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

### <span data-ttu-id="99a79-165">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="99a79-165">-InstanceId</span></span>
<span data-ttu-id="99a79-166">Hiermee geeft u de exemplaar-Id's op van de taken die met deze cmdlet worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-166">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="99a79-167">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="99a79-167">The default is all jobs.</span></span>

<span data-ttu-id="99a79-168">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="99a79-168">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="99a79-169">Gebruik **Get-job** om de exemplaar-id van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="99a79-169">To find the instance ID of a job, use **Get-Job**.</span></span>

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

### <span data-ttu-id="99a79-170">-Taak</span><span class="sxs-lookup"><span data-stu-id="99a79-170">-Job</span></span>
<span data-ttu-id="99a79-171">Hiermee geeft u de werk stroom taken op die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="99a79-171">Specifies the workflow jobs that this cmdlet stops.</span></span>
<span data-ttu-id="99a79-172">Voer een variabele in die de werk stroom taken bevat of een opdracht waarmee de werk stroom taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="99a79-172">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span>
<span data-ttu-id="99a79-173">U kunt werk stroom taken ook pipet naar de cmdlet **pause-job** .</span><span class="sxs-lookup"><span data-stu-id="99a79-173">You can also pipe workflow jobs to the **Suspend-Job** cmdlet.</span></span>

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

### <span data-ttu-id="99a79-174">-Name</span><span class="sxs-lookup"><span data-stu-id="99a79-174">-Name</span></span>
<span data-ttu-id="99a79-175">Hiermee geeft u beschrijvende namen op van taken die met deze cmdlet worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-175">Specifies friendly names of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="99a79-176">Voer een of meer werk stroom taak namen in.</span><span class="sxs-lookup"><span data-stu-id="99a79-176">Enter one or more workflow job names.</span></span>
<span data-ttu-id="99a79-177">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="99a79-177">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="99a79-178">-Status</span><span class="sxs-lookup"><span data-stu-id="99a79-178">-State</span></span>
<span data-ttu-id="99a79-179">Hiermee geeft u een taak status op.</span><span class="sxs-lookup"><span data-stu-id="99a79-179">Specifies a job state.</span></span>
<span data-ttu-id="99a79-180">Met deze cmdlet worden alleen taken in de opgegeven status gestopt.</span><span class="sxs-lookup"><span data-stu-id="99a79-180">This cmdlet stops only jobs in the specified state.</span></span>
<span data-ttu-id="99a79-181">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="99a79-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="99a79-182">NotStarted</span><span class="sxs-lookup"><span data-stu-id="99a79-182">NotStarted</span></span>
- <span data-ttu-id="99a79-183">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="99a79-183">Running</span></span>
- <span data-ttu-id="99a79-184">Voltooid</span><span class="sxs-lookup"><span data-stu-id="99a79-184">Completed</span></span>
- <span data-ttu-id="99a79-185">Mislukt</span><span class="sxs-lookup"><span data-stu-id="99a79-185">Failed</span></span>
- <span data-ttu-id="99a79-186">Gestopt</span><span class="sxs-lookup"><span data-stu-id="99a79-186">Stopped</span></span>
- <span data-ttu-id="99a79-187">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="99a79-187">Blocked</span></span>
- <span data-ttu-id="99a79-188">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="99a79-188">Suspended</span></span>
- <span data-ttu-id="99a79-189">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="99a79-189">Disconnected</span></span>
- <span data-ttu-id="99a79-190">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="99a79-190">Suspending</span></span>
- <span data-ttu-id="99a79-191">Stoppen</span><span class="sxs-lookup"><span data-stu-id="99a79-191">Stopping</span></span>

<span data-ttu-id="99a79-192">**Suspend: taak** suspendeert alleen werk stroom taken met de status **actief** .</span><span class="sxs-lookup"><span data-stu-id="99a79-192">**Suspend-Job** suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="99a79-193">Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.</span><span class="sxs-lookup"><span data-stu-id="99a79-193">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="99a79-194">-Wachten</span><span class="sxs-lookup"><span data-stu-id="99a79-194">-Wait</span></span>
<span data-ttu-id="99a79-195">Geeft aan dat deze cmdlet de opdracht prompt onderdrukt totdat de werk stroom taak de status onderbroken heeft.</span><span class="sxs-lookup"><span data-stu-id="99a79-195">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span>
<span data-ttu-id="99a79-196">Standaard wordt de **suspend-taak** onmiddellijk geretourneerd, zelfs als de werk stroom taak nog niet de status onderbroken heeft.</span><span class="sxs-lookup"><span data-stu-id="99a79-196">By default, **Suspend-Job** returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="99a79-197">De *wait* -para meter is gelijk aan het sluizen van een **suspend-job-** opdracht naar de cmdlet **wait-job** .</span><span class="sxs-lookup"><span data-stu-id="99a79-197">The *Wait* parameter is equivalent to piping a **Suspend-Job** command to the **Wait-Job** cmdlet.</span></span>

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

### <span data-ttu-id="99a79-198">-Confirm</span><span class="sxs-lookup"><span data-stu-id="99a79-198">-Confirm</span></span>
<span data-ttu-id="99a79-199">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="99a79-199">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="99a79-200">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="99a79-200">-WhatIf</span></span>
<span data-ttu-id="99a79-201">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="99a79-201">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="99a79-202">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="99a79-202">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="99a79-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="99a79-203">CommonParameters</span></span>
<span data-ttu-id="99a79-204">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="99a79-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="99a79-205">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="99a79-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="99a79-206">INVOER</span><span class="sxs-lookup"><span data-stu-id="99a79-206">INPUTS</span></span>

### <span data-ttu-id="99a79-207">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="99a79-207">System.Management.Automation.Job</span></span>
<span data-ttu-id="99a79-208">U kunt alle typen taken naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="99a79-208">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="99a79-209">Als **opschorting-taak** echter een taak van een niet-ondersteund type krijgt, wordt een afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="99a79-209">However, if **Suspend-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="99a79-210">UITVOER</span><span class="sxs-lookup"><span data-stu-id="99a79-210">OUTPUTS</span></span>

### <span data-ttu-id="99a79-211">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="99a79-211">System.Management.Automation.Job</span></span>
<span data-ttu-id="99a79-212">Met deze cmdlet worden de taken geretourneerd die zijn onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-212">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="99a79-213">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="99a79-213">NOTES</span></span>

* <span data-ttu-id="99a79-214">Het mechanisme en de locatie voor het opslaan van een onderbroken taak kunnen variëren afhankelijk van het taak type.</span><span class="sxs-lookup"><span data-stu-id="99a79-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="99a79-215">Onderbroken werk stroom taken worden bijvoorbeeld standaard opgeslagen in een plat bestands archief, maar kunnen ook worden opgeslagen in een Data Base.</span><span class="sxs-lookup"><span data-stu-id="99a79-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
* <span data-ttu-id="99a79-216">Als u een werk stroom taak indient die niet wordt uitgevoerd, wordt er een waarschuwings bericht weer gegeven in de **suspend-taak** .</span><span class="sxs-lookup"><span data-stu-id="99a79-216">If you submit a workflow job that is not in the Running state, **Suspend-Job** displays a warning message.</span></span> <span data-ttu-id="99a79-217">Als u de waarschuwing wilt onderdrukken, gebruikt u de gemeen schappelijke *WarningAction* para meter met de waarde SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="99a79-217">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="99a79-218">Als een taak niet van een type is dat opschorting ondersteunt, retourneert **suspend-taak** een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="99a79-218">If a job is not of a type that supports suspending, **Suspend-Job** returns a terminating error.</span></span>

* <span data-ttu-id="99a79-219">Gebruik de para meter *State* van de cmdlet **Get-job** om werk stroom taken met de status onderbroken te krijgen om de werk stroom taken te vinden die zijn onderbroken.</span><span class="sxs-lookup"><span data-stu-id="99a79-219">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get workflow jobs in the Suspended state.</span></span>
* <span data-ttu-id="99a79-220">Sommige taak typen hebben opties of eigenschappen die verhinderen dat Windows Power shell de taak onderbreekt.</span><span class="sxs-lookup"><span data-stu-id="99a79-220">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="99a79-221">Als er wordt geprobeerd de taak te onderbreken, controleert u of de taak opties en eigenschappen het blok keren toestaan.</span><span class="sxs-lookup"><span data-stu-id="99a79-221">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="99a79-222">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="99a79-222">RELATED LINKS</span></span>

[<span data-ttu-id="99a79-223">Get-job</span><span class="sxs-lookup"><span data-stu-id="99a79-223">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="99a79-224">Receive-job</span><span class="sxs-lookup"><span data-stu-id="99a79-224">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="99a79-225">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="99a79-225">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="99a79-226">Resume-job</span><span class="sxs-lookup"><span data-stu-id="99a79-226">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="99a79-227">Begin taak</span><span class="sxs-lookup"><span data-stu-id="99a79-227">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="99a79-228">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="99a79-228">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="99a79-229">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="99a79-229">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="99a79-230">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="99a79-230">Wait-Job</span></span>](Wait-Job.md)
