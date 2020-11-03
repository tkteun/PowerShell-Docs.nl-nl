---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 85cbfad2a4866bf18e69fb99afb8698e233c4c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250145"
---
# <span data-ttu-id="b8c69-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="b8c69-103">Resume-Job</span></span>

## <span data-ttu-id="b8c69-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b8c69-104">SYNOPSIS</span></span>
<span data-ttu-id="b8c69-105">Hiermee wordt een onderbroken taak opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="b8c69-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="b8c69-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b8c69-106">SYNTAX</span></span>

### <span data-ttu-id="b8c69-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b8c69-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b8c69-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="b8c69-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b8c69-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="b8c69-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b8c69-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="b8c69-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b8c69-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="b8c69-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b8c69-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="b8c69-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b8c69-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b8c69-113">DESCRIPTION</span></span>
<span data-ttu-id="b8c69-114">Met de cmdlet **Resume-job** wordt een werk stroom taak hervat die is onderbroken, bijvoorbeeld door gebruik te maken van de Suspend-Job cmdlet of de activiteit About_Suspend werk stroom.</span><span class="sxs-lookup"><span data-stu-id="b8c69-114">The **Resume-Job** cmdlet resumes a workflow job that was suspended, such as by using the Suspend-Job cmdlet or the about_Suspend-Workflow activity.</span></span>
<span data-ttu-id="b8c69-115">Wanneer een werk stroom taak wordt hervat, bouwt de taak engine de status, meta gegevens en uitvoer op uit opgeslagen resources, zoals controle punten.</span><span class="sxs-lookup"><span data-stu-id="b8c69-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span>
<span data-ttu-id="b8c69-116">De taak wordt opnieuw gestart zonder dat de status of gegevens verloren zijn gegaan.</span><span class="sxs-lookup"><span data-stu-id="b8c69-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="b8c69-117">De taak status is gewijzigd van **opgeschort** in **actief**.</span><span class="sxs-lookup"><span data-stu-id="b8c69-117">The job state is changed from **Suspended** to **Running**.</span></span>

<span data-ttu-id="b8c69-118">Gebruik de para meters van **Resume-job** om taken op naam, id, exemplaar-id of pipe een taak object te selecteren, zoals één geretourneerd door de Get-Job-cmdlet, om de **taak te hervatten**.</span><span class="sxs-lookup"><span data-stu-id="b8c69-118">Use the parameters of **Resume-Job** to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the Get-Job cmdlet, to **Resume-Job**.</span></span>
<span data-ttu-id="b8c69-119">U kunt ook een eigenschappen filter gebruiken om een taak te selecteren die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="b8c69-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="b8c69-120">**Resume-job** retourneert standaard onmiddellijk, zelfs als alle taken nog niet zijn hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-120">By default, **Resume-Job** returns immediately, even though all jobs might not yet be resumed.</span></span>
<span data-ttu-id="b8c69-121">Gebruik de *wait* -para meter om de opdracht prompt te onderdrukken totdat alle opgegeven taken zijn hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-121">To suppress the command prompt until all specified jobs are resumed, use the *Wait* parameter.</span></span>

<span data-ttu-id="b8c69-122">De cmdlet **Resume-job** werkt alleen voor aangepaste taak typen, zoals werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="b8c69-122">The **Resume-Job** cmdlet works only on custom job types, such as workflow jobs.</span></span>
<span data-ttu-id="b8c69-123">Deze functie werkt niet op standaard achtergrond taken, zoals die worden gestart met behulp van de cmdlet Start-Job.</span><span class="sxs-lookup"><span data-stu-id="b8c69-123">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>
<span data-ttu-id="b8c69-124">Als u een taak voor een niet-ondersteund type verzendt, wordt met **hervatten taak** een afsluit fout gegenereerd en stopt de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="b8c69-124">If you submit a job of an unsupported type, **Resume-Job** generates a terminating error and stops running.</span></span>

<span data-ttu-id="b8c69-125">Zoek naar een waarde van **PSWorkflowJob** in de eigenschap **PSJobTypeName** van de taak om een werk stroom taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="b8c69-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="b8c69-126">Zie de Help-onderwerpen voor het aangepaste taak type om te bepalen of een bepaald aangepast taak type de cmdlet **Resume-job** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="b8c69-126">To determine whether a particular custom job type supports the **Resume-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="b8c69-127">Voordat u een taak-cmdlet voor een aangepast taak type gebruikt, importeert u de module die het aangepaste taak type ondersteunt, hetzij met behulp van de cmdlet Import-Module, hetzij door een cmdlet in de module op te halen of te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b8c69-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the Import-Module cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="b8c69-128">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b8c69-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b8c69-129">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b8c69-129">EXAMPLES</span></span>

### <span data-ttu-id="b8c69-130">Voor beeld 1: een taak hervatten op ID</span><span class="sxs-lookup"><span data-stu-id="b8c69-130">Example 1: Resume a job by ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get the job. The output shows that the job is a suspended workflow job.
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

The second command uses the *Id* parameter of the **Resume-Job** cmdlet to resume the job with an *Id* value of 4.
PS C:\> Resume-Job -Id 4
```

<span data-ttu-id="b8c69-131">Met de opdrachten in dit voor beeld wordt gecontroleerd of de taak een onderbroken werk stroom taak is en vervolgens de taak hervatten.</span><span class="sxs-lookup"><span data-stu-id="b8c69-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span>

### <span data-ttu-id="b8c69-132">Voor beeld 2: een taak hervatten op naam</span><span class="sxs-lookup"><span data-stu-id="b8c69-132">Example 2: Resume a job by name</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

<span data-ttu-id="b8c69-133">Met deze opdracht wordt de para meter *name* gebruikt voor het hervatten van verschillende werk stroom taken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b8c69-133">This command uses the *Name* parameter to resume several workflow jobs on the local computer.</span></span>

### <span data-ttu-id="b8c69-134">Voor beeld 3: aangepaste eigenschaps waarden gebruiken</span><span class="sxs-lookup"><span data-stu-id="b8c69-134">Example 3: Use custom property values</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

<span data-ttu-id="b8c69-135">Met deze opdracht wordt de waarde van een aangepaste eigenschap gebruikt om de werk stroom taak te identificeren die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="b8c69-135">This command uses the value of a custom property to identify the workflow job to resume.</span></span>
<span data-ttu-id="b8c69-136">De *filter* parameter wordt gebruikt om de werk stroom taak te identificeren met behulp van de eigenschap **CustomID** .</span><span class="sxs-lookup"><span data-stu-id="b8c69-136">It uses the *Filter* parameter to identify the workflow job by its **CustomID** property.</span></span>
<span data-ttu-id="b8c69-137">Er wordt ook gebruikgemaakt van de para meter *State* om te controleren of de werk stroom taak is onderbroken voordat deze probeert om deze te hervatten.</span><span class="sxs-lookup"><span data-stu-id="b8c69-137">It also uses the *State* parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

### <span data-ttu-id="b8c69-138">Voor beeld 4: alle uitgestelde taken op een externe computer hervatten</span><span class="sxs-lookup"><span data-stu-id="b8c69-138">Example 4: Resume all suspended jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="b8c69-139">Met deze opdracht worden alle onderbroken taken hervat op de externe computer Srv01.</span><span class="sxs-lookup"><span data-stu-id="b8c69-139">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

<span data-ttu-id="b8c69-140">De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Srv01.</span><span class="sxs-lookup"><span data-stu-id="b8c69-140">The command uses the Invoke-Command cmdlet to run a command on the Srv01 computer.</span></span>
<span data-ttu-id="b8c69-141">De opdracht extern maakt gebruik van de para meter *State* van de cmdlet **Get-job** om alle uitgestelde taken op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="b8c69-141">The remote command uses the *State* parameter of the **Get-Job** cmdlet to get all suspended jobs on the computer.</span></span>
<span data-ttu-id="b8c69-142">Met een pijplijn operator (|) worden de uitgestelde taken verzonden naar de cmdlet **Resume-job** , waarmee ze worden hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-142">A pipeline operator (|) sends the suspended jobs to the **Resume-Job** cmdlet, which resumes them.</span></span>

### <span data-ttu-id="b8c69-143">Voor beeld 5: wachten tot taken worden hervat</span><span class="sxs-lookup"><span data-stu-id="b8c69-143">Example 5: Wait for jobs to resume</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

<span data-ttu-id="b8c69-144">Met deze opdracht wordt de *wait* -para meter voor het direct hervatten van de **taak** gebruikt om alleen te retour neren nadat alle opgegeven taken zijn hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-144">This command uses the *Wait* parameter to direct **Resume-Job** to return only after all specified jobs are resumed.</span></span>
<span data-ttu-id="b8c69-145">De *wait* -para meter is vooral nuttig in scripts die ervan uitgaan dat taken worden hervat voordat het script doorgaat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-145">The *Wait* parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

### <span data-ttu-id="b8c69-146">Voor beeld 6: een werk stroom die zichzelf onderbreekt hervatten</span><span class="sxs-lookup"><span data-stu-id="b8c69-146">Example 6: Resume a workflow that suspends itself</span></span>

```
This code sample shows the **Suspend-Workflow** activity in a workflow.
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

The following command runs the Test-Suspend workflow on the Server01 computer.When you run the workflow, the workflow runs the Get-Date activity and stores the result in the $a variable. Then it runs the Suspend-Workflow activity. In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.  Suspend-Workflow returns a workflow job object even if the workflow is not explicitly run as a job.
PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

The following command resumes the Test-Suspend workflow in Job8. It uses the *Wait* parameter to hold the command prompt until the job is resumed.
PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command

--     ----            -------------   -----         -----------     --------             -------

8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

This command uses the **Receive-Job** cmdlet to get the results of the Test-Suspend workflow. The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the $a variable before the workflow was suspended.
PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

<span data-ttu-id="b8c69-147">Met de cmdlet **Resume-job** kunt u een werk stroom taak hervatten die is onderbroken met behulp van de **suspend-werk stroom** activiteit.</span><span class="sxs-lookup"><span data-stu-id="b8c69-147">The **Resume-Job** cmdlet lets you resume a workflow job that was suspend by using the **Suspend-Workflow** activity.</span></span>
<span data-ttu-id="b8c69-148">Met deze activiteit wordt een werk stroom in een werk stroom onderbroken.</span><span class="sxs-lookup"><span data-stu-id="b8c69-148">This activity suspends a workflow from within a workflow.</span></span>
<span data-ttu-id="b8c69-149">Het is alleen geldig in werk stromen.</span><span class="sxs-lookup"><span data-stu-id="b8c69-149">It is valid only in workflows.</span></span>

<span data-ttu-id="b8c69-150">Zie about_Suspend-werk stroom voor meer informatie over de Suspend-werk stroom.</span><span class="sxs-lookup"><span data-stu-id="b8c69-150">For information about the Suspend-Workflow, see about_Suspend-Workflow.</span></span>

## <span data-ttu-id="b8c69-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8c69-151">PARAMETERS</span></span>

### <span data-ttu-id="b8c69-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="b8c69-152">-Filter</span></span>
<span data-ttu-id="b8c69-153">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="b8c69-153">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="b8c69-154">Met deze cmdlet worden taken hervat die voldoen aan alle voor waarden in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="b8c69-154">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span>
<span data-ttu-id="b8c69-155">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="b8c69-155">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="b8c69-156">-Id</span><span class="sxs-lookup"><span data-stu-id="b8c69-156">-Id</span></span>
<span data-ttu-id="b8c69-157">Hiermee wordt een matrix met Id's opgegeven voor taken die met deze cmdlet worden hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-157">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="b8c69-158">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b8c69-158">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="b8c69-159">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="b8c69-159">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="b8c69-160">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="b8c69-160">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="b8c69-161">Voer **Get-job** uit om de id van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="b8c69-161">To find the ID of a job, run **Get-Job**.</span></span>

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

### <span data-ttu-id="b8c69-162">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="b8c69-162">-InstanceId</span></span>
<span data-ttu-id="b8c69-163">Hiermee geeft u een matrix met exemplaar-Id's van taken op die met deze cmdlet worden hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-163">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="b8c69-164">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="b8c69-164">The default is all jobs.</span></span>

<span data-ttu-id="b8c69-165">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="b8c69-165">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="b8c69-166">Voer **Get-job** uit om de exemplaar-id van een taak te vinden.</span><span class="sxs-lookup"><span data-stu-id="b8c69-166">To find the instance ID of a job, run **Get-Job**.</span></span>

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

### <span data-ttu-id="b8c69-167">-Taak</span><span class="sxs-lookup"><span data-stu-id="b8c69-167">-Job</span></span>
<span data-ttu-id="b8c69-168">Hiermee geeft u de taken op die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-168">Specifies the jobs to be resumed.</span></span>
<span data-ttu-id="b8c69-169">Voer een variabele in die de taken bevat of een opdracht waarmee de taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b8c69-169">Enter a variable that contains the jobs or a command that gets the jobs.</span></span>
<span data-ttu-id="b8c69-170">U kunt ook taken door sluizen naar de cmdlet **Resume-job** .</span><span class="sxs-lookup"><span data-stu-id="b8c69-170">You can also pipe jobs to the **Resume-Job** cmdlet.</span></span>

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

### <span data-ttu-id="b8c69-171">-Name</span><span class="sxs-lookup"><span data-stu-id="b8c69-171">-Name</span></span>
<span data-ttu-id="b8c69-172">Hiermee geeft u een matrix met beschrijvende namen op van taken die met deze cmdlet worden hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-172">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="b8c69-173">Voer een of meer taak namen in.</span><span class="sxs-lookup"><span data-stu-id="b8c69-173">Enter one or more job names.</span></span>
<span data-ttu-id="b8c69-174">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b8c69-174">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b8c69-175">-Status</span><span class="sxs-lookup"><span data-stu-id="b8c69-175">-State</span></span>
<span data-ttu-id="b8c69-176">Hiermee wordt de status van taken opgegeven die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-176">Specifies the state of jobs to resume.</span></span>
<span data-ttu-id="b8c69-177">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b8c69-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b8c69-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="b8c69-178">NotStarted</span></span>
- <span data-ttu-id="b8c69-179">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="b8c69-179">Running</span></span>
- <span data-ttu-id="b8c69-180">Voltooid</span><span class="sxs-lookup"><span data-stu-id="b8c69-180">Completed</span></span>
- <span data-ttu-id="b8c69-181">Mislukt</span><span class="sxs-lookup"><span data-stu-id="b8c69-181">Failed</span></span>
- <span data-ttu-id="b8c69-182">Gestopt</span><span class="sxs-lookup"><span data-stu-id="b8c69-182">Stopped</span></span>
- <span data-ttu-id="b8c69-183">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="b8c69-183">Blocked</span></span>
- <span data-ttu-id="b8c69-184">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="b8c69-184">Suspended</span></span>
- <span data-ttu-id="b8c69-185">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="b8c69-185">Disconnected</span></span>
- <span data-ttu-id="b8c69-186">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="b8c69-186">Suspending</span></span>
- <span data-ttu-id="b8c69-187">Stoppen</span><span class="sxs-lookup"><span data-stu-id="b8c69-187">Stopping</span></span>

<span data-ttu-id="b8c69-188">Met deze cmdlet worden alleen taken hervat die de status **onderbroken** hebben.</span><span class="sxs-lookup"><span data-stu-id="b8c69-188">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="b8c69-189">Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.</span><span class="sxs-lookup"><span data-stu-id="b8c69-189">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="b8c69-190">-Wachten</span><span class="sxs-lookup"><span data-stu-id="b8c69-190">-Wait</span></span>
<span data-ttu-id="b8c69-191">Geeft aan dat deze cmdlet de opdracht prompt onderdrukt voordat alle taak resultaten opnieuw worden gestart.</span><span class="sxs-lookup"><span data-stu-id="b8c69-191">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span>
<span data-ttu-id="b8c69-192">Standaard retourneert deze cmdlet onmiddellijk de beschik bare resultaten.</span><span class="sxs-lookup"><span data-stu-id="b8c69-192">By default, this cmdlet immediately returns the available results.</span></span>

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

### <span data-ttu-id="b8c69-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b8c69-193">-Confirm</span></span>
<span data-ttu-id="b8c69-194">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b8c69-194">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b8c69-195">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b8c69-195">-WhatIf</span></span>
<span data-ttu-id="b8c69-196">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b8c69-196">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b8c69-197">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b8c69-197">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b8c69-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8c69-198">CommonParameters</span></span>
<span data-ttu-id="b8c69-199">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8c69-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8c69-200">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b8c69-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8c69-201">INVOER</span><span class="sxs-lookup"><span data-stu-id="b8c69-201">INPUTS</span></span>

### <span data-ttu-id="b8c69-202">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="b8c69-202">System.Management.Automation.Job</span></span>
<span data-ttu-id="b8c69-203">U kunt alle typen taken naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="b8c69-203">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="b8c69-204">Als **Resume-job** een taak van een niet-ondersteund type ontvangt, wordt een afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b8c69-204">If **Resume-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="b8c69-205">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b8c69-205">OUTPUTS</span></span>

### <span data-ttu-id="b8c69-206">Geen, System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="b8c69-206">None, System.Management.Automation.Job</span></span>
<span data-ttu-id="b8c69-207">Met deze cmdlet worden de taken geretourneerd die worden hervat als u de para meter *PassThru* gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b8c69-207">This cmdlet returns the jobs that it tries to resume, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="b8c69-208">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b8c69-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b8c69-209">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b8c69-209">NOTES</span></span>

* <span data-ttu-id="b8c69-210">**Resume-job** kan alleen taken hervatten die zijn onderbroken.</span><span class="sxs-lookup"><span data-stu-id="b8c69-210">**Resume-Job** can only resume jobs that are suspended.</span></span> <span data-ttu-id="b8c69-211">Als u een taak in een andere status verzendt, wordt de **bewerking hervatten voor de taak uitgevoerd.** er wordt een waarschuwing gegenereerd om u te melden dat de taak niet kan worden hervat.</span><span class="sxs-lookup"><span data-stu-id="b8c69-211">If you submit a job in a different state, **Resume-Job** runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="b8c69-212">Als u de waarschuwing wilt onderdrukken, gebruikt u de gemeen schappelijke *WarningAction* para meter met de waarde SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="b8c69-212">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>
* <span data-ttu-id="b8c69-213">Als een taak niet van een type is dat hervatten ondersteunt, zoals een werk stroom taak ( **PSWorkflowJob** ), retourneert **hervatten taak** een afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="b8c69-213">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), **Resume-Job** returns a terminating error.</span></span>
* <span data-ttu-id="b8c69-214">Het mechanisme en de locatie voor het opslaan van een onderbroken taak kunnen variëren afhankelijk van het taak type.</span><span class="sxs-lookup"><span data-stu-id="b8c69-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="b8c69-215">Onderbroken werk stroom taken worden bijvoorbeeld standaard opgeslagen in een plat bestands archief, maar kunnen ook worden opgeslagen in een SQL database.</span><span class="sxs-lookup"><span data-stu-id="b8c69-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
* <span data-ttu-id="b8c69-216">Wanneer u een taak hervat, wordt de status van de taak gewijzigd van **opgeschort** in **actief**.</span><span class="sxs-lookup"><span data-stu-id="b8c69-216">When you resume a job, the job state changes from **Suspended** to **Running**.</span></span> <span data-ttu-id="b8c69-217">Als u de taken wilt vinden die worden uitgevoerd, met inbegrip van die die zijn hervat door deze cmdlet, gebruikt u de para meter *State* van de cmdlet **Get-job** om taken in de **actieve** status op te halen.</span><span class="sxs-lookup"><span data-stu-id="b8c69-217">To find the jobs that are running, including those that were resumed by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get jobs in the **Running** state.</span></span>
* <span data-ttu-id="b8c69-218">Sommige taak typen hebben opties of eigenschappen die verhinderen dat Windows Power shell de taak onderbreekt.</span><span class="sxs-lookup"><span data-stu-id="b8c69-218">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="b8c69-219">Als er wordt geprobeerd de taak te onderbreken, controleert u of de taak opties en eigenschappen het blok keren toestaan.</span><span class="sxs-lookup"><span data-stu-id="b8c69-219">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="b8c69-220">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b8c69-220">RELATED LINKS</span></span>

[<span data-ttu-id="b8c69-221">Get-job</span><span class="sxs-lookup"><span data-stu-id="b8c69-221">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="b8c69-222">Receive-job</span><span class="sxs-lookup"><span data-stu-id="b8c69-222">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="b8c69-223">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="b8c69-223">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="b8c69-224">Begin taak</span><span class="sxs-lookup"><span data-stu-id="b8c69-224">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="b8c69-225">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="b8c69-225">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="b8c69-226">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="b8c69-226">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="b8c69-227">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="b8c69-227">Wait-Job</span></span>](Wait-Job.md)
