---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 6d08d9053e100cb53d37a6e4931d118f90c35a6a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388532"
---
# <span data-ttu-id="f490f-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="f490f-103">Resume-Job</span></span>

## <span data-ttu-id="f490f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f490f-104">SYNOPSIS</span></span>
<span data-ttu-id="f490f-105">Hiermee wordt een onderbroken taak opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="f490f-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="f490f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f490f-106">SYNTAX</span></span>

### <span data-ttu-id="f490f-107">SessionIdParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="f490f-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f490f-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="f490f-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f490f-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f490f-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f490f-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f490f-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f490f-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="f490f-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f490f-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="f490f-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f490f-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f490f-113">DESCRIPTION</span></span>

<span data-ttu-id="f490f-114">Met de `Resume-Job` cmdlet wordt een werk stroom taak hervat die is onderbroken, bijvoorbeeld door gebruik te maken van de `Suspend-Job` cmdlet of de activiteit [about_Suspend werk stroom](../PSWorkflow/about/about_Suspend-Workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="f490f-114">The `Resume-Job` cmdlet resumes a workflow job that was suspended, such as by using the `Suspend-Job` cmdlet or the [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) activity.</span></span> <span data-ttu-id="f490f-115">Wanneer een werk stroom taak wordt hervat, bouwt de taak engine de status, meta gegevens en uitvoer op uit opgeslagen resources, zoals controle punten.</span><span class="sxs-lookup"><span data-stu-id="f490f-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span> <span data-ttu-id="f490f-116">De taak wordt opnieuw gestart zonder dat de status of gegevens verloren zijn gegaan.</span><span class="sxs-lookup"><span data-stu-id="f490f-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="f490f-117">De taak status is gewijzigd van **opgeschort** in **actief**.</span><span class="sxs-lookup"><span data-stu-id="f490f-117">The job state is changed from **Suspended** to **Running**.</span></span>

<span data-ttu-id="f490f-118">Gebruik de para meters van `Resume-Job` om taken op naam, id, exemplaar-id of pipe een taak object te selecteren, zoals één geretourneerd door de `Get-Job` cmdlet `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="f490f-118">Use the parameters of `Resume-Job` to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the `Get-Job` cmdlet, to `Resume-Job`.</span></span> <span data-ttu-id="f490f-119">U kunt ook een eigenschappen filter gebruiken om een taak te selecteren die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="f490f-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="f490f-120">Standaard `Resume-Job` wordt direct geretourneerd, zelfs als alle taken mogelijk nog niet zijn hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-120">By default, `Resume-Job` returns immediately, even though all jobs might not yet be resumed.</span></span> <span data-ttu-id="f490f-121">Gebruik de **wait** -para meter om de opdracht prompt te onderdrukken totdat alle opgegeven taken zijn hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-121">To suppress the command prompt until all specified jobs are resumed, use the **Wait** parameter.</span></span>

<span data-ttu-id="f490f-122">De `Resume-Job` cmdlet werkt alleen voor aangepaste taak typen, zoals werk stroom taken.</span><span class="sxs-lookup"><span data-stu-id="f490f-122">The `Resume-Job` cmdlet works only on custom job types, such as workflow jobs.</span></span> <span data-ttu-id="f490f-123">Deze functie werkt niet op standaard achtergrond taken, zoals die worden gestart met behulp van de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f490f-123">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="f490f-124">Als u een taak voor een niet-ondersteund type verzendt, `Resume-Job` genereert een afsluit fout en stopt de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="f490f-124">If you submit a job of an unsupported type, `Resume-Job` generates a terminating error and stops running.</span></span>

<span data-ttu-id="f490f-125">Zoek naar een waarde van **PSWorkflowJob** in de eigenschap **PSJobTypeName** van de taak om een werk stroom taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f490f-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="f490f-126">`Resume-Job`Zie de Help-onderwerpen voor het aangepaste taak type om te bepalen of een bepaald aangepast taak type de cmdlet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="f490f-126">To determine whether a particular custom job type supports the `Resume-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="f490f-127">Voordat u een taak-cmdlet voor een aangepast taak type gebruikt, importeert u de module die het aangepaste taak type ondersteunt, hetzij met behulp van de cmdlet, hetzij door `Import-Module` een cmdlet in de module op te halen of te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f490f-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the `Import-Module` cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="f490f-128">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f490f-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f490f-129">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f490f-129">EXAMPLES</span></span>

### <span data-ttu-id="f490f-130">Voor beeld 1: een taak hervatten op ID</span><span class="sxs-lookup"><span data-stu-id="f490f-130">Example 1: Resume a job by ID</span></span>

<span data-ttu-id="f490f-131">Met de opdrachten in dit voor beeld wordt gecontroleerd of de taak een onderbroken werk stroom taak is en vervolgens de taak hervatten.</span><span class="sxs-lookup"><span data-stu-id="f490f-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span> <span data-ttu-id="f490f-132">De eerste opdracht gebruikt de `Get-Job` cmdlet om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="f490f-132">The first command uses the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="f490f-133">In de uitvoer ziet u dat de taak een onderbroken werk stroom taak is.</span><span class="sxs-lookup"><span data-stu-id="f490f-133">The output shows that the job is a suspended workflow job.</span></span> <span data-ttu-id="f490f-134">De tweede opdracht maakt gebruik van de para meter **id** van de `Resume-Job` cmdlet om de taak te hervatten met de **id-** waarde 4.</span><span class="sxs-lookup"><span data-stu-id="f490f-134">The second command uses the **Id** parameter of the `Resume-Job` cmdlet to resume the job with an **Id** value of 4.</span></span>

```
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

PS C:\> Resume-Job -Id 4
```

### <span data-ttu-id="f490f-135">Voor beeld 2: een taak hervatten op naam</span><span class="sxs-lookup"><span data-stu-id="f490f-135">Example 2: Resume a job by name</span></span>

<span data-ttu-id="f490f-136">Met deze opdracht wordt de para meter **name** gebruikt voor het hervatten van verschillende werk stroom taken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f490f-136">This command uses the **Name** parameter to resume several workflow jobs on the local computer.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

### <span data-ttu-id="f490f-137">Voor beeld 3: aangepaste eigenschaps waarden gebruiken</span><span class="sxs-lookup"><span data-stu-id="f490f-137">Example 3: Use custom property values</span></span>

<span data-ttu-id="f490f-138">Met deze opdracht wordt de waarde van een aangepaste eigenschap gebruikt om de werk stroom taak te identificeren die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="f490f-138">This command uses the value of a custom property to identify the workflow job to resume.</span></span> <span data-ttu-id="f490f-139">De **filter** parameter wordt gebruikt om de werk stroom taak te identificeren met behulp van de eigenschap **CustomID** .</span><span class="sxs-lookup"><span data-stu-id="f490f-139">It uses the **Filter** parameter to identify the workflow job by its **CustomID** property.</span></span> <span data-ttu-id="f490f-140">Er wordt ook gebruikgemaakt van de para meter **State** om te controleren of de werk stroom taak is onderbroken voordat deze probeert om deze te hervatten.</span><span class="sxs-lookup"><span data-stu-id="f490f-140">It also uses the **State** parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

### <span data-ttu-id="f490f-141">Voor beeld 4: alle uitgestelde taken op een externe computer hervatten</span><span class="sxs-lookup"><span data-stu-id="f490f-141">Example 4: Resume all suspended jobs on a remote computer</span></span>

<span data-ttu-id="f490f-142">Met deze opdracht worden alle onderbroken taken hervat op de externe computer Srv01.</span><span class="sxs-lookup"><span data-stu-id="f490f-142">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="f490f-143">De opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren op de computer Srv01.</span><span class="sxs-lookup"><span data-stu-id="f490f-143">The command uses the `Invoke-Command` cmdlet to run a command on the Srv01 computer.</span></span> <span data-ttu-id="f490f-144">De opdracht extern maakt gebruik van de para meter **State** van de `Get-Job` cmdlet om alle uitgestelde taken op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="f490f-144">The remote command uses the **State** parameter of the `Get-Job` cmdlet to get all suspended jobs on the computer.</span></span> <span data-ttu-id="f490f-145">Een pijplijn operator ( `|` ) verzendt de uitgestelde taken naar de `Resume-Job` cmdlet, waarna deze worden hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-145">A pipeline operator (`|`) sends the suspended jobs to the `Resume-Job` cmdlet, which resumes them.</span></span>

### <span data-ttu-id="f490f-146">Voor beeld 5: wachten tot taken worden hervat</span><span class="sxs-lookup"><span data-stu-id="f490f-146">Example 5: Wait for jobs to resume</span></span>

<span data-ttu-id="f490f-147">Met deze opdracht wordt de **wait** -para meter gebruikt om `Resume-Job` alleen te retour neren nadat alle opgegeven taken zijn hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-147">This command uses the **Wait** parameter to direct `Resume-Job` to return only after all specified jobs are resumed.</span></span> <span data-ttu-id="f490f-148">De **wait** -para meter is vooral nuttig in scripts die ervan uitgaan dat taken worden hervat voordat het script doorgaat.</span><span class="sxs-lookup"><span data-stu-id="f490f-148">The **Wait** parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

### <span data-ttu-id="f490f-149">Voor beeld 6: een werk stroom die zichzelf onderbreekt hervatten</span><span class="sxs-lookup"><span data-stu-id="f490f-149">Example 6: Resume a workflow that suspends itself</span></span>

<span data-ttu-id="f490f-150">Dit code voorbeeld toont de `Suspend-Workflow` activiteit in een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="f490f-150">This code sample shows the `Suspend-Workflow` activity in a workflow.</span></span>

<span data-ttu-id="f490f-151">De `Test-Suspend` werk stroom op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="f490f-151">The `Test-Suspend` workflow on the Server01 computer.</span></span> <span data-ttu-id="f490f-152">Wanneer u de werk stroom uitvoert, voert de werk stroom de `Get-Date` activiteit uit en slaat het resultaat op in de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="f490f-152">When you run the workflow, the workflow runs the `Get-Date` activity and stores the result in the `$a` variable.</span></span> <span data-ttu-id="f490f-153">Vervolgens wordt de `Suspend-Workflow` activiteit uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f490f-153">Then it runs the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="f490f-154">Als antwoord neemt het een controle punt in, wordt de werk stroom onderbroken en wordt een werk stroom taak object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f490f-154">In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.</span></span> <span data-ttu-id="f490f-155">`Suspend-Workflow` retourneert een werk stroom taak object, zelfs als de werk stroom niet expliciet als een taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f490f-155">`Suspend-Workflow` returns a workflow job object even if the workflow is not explicitly run as a job.</span></span>

<span data-ttu-id="f490f-156">`Resume-Job` Hiermee wordt de `Test-Suspend` werk stroom hervat in Job8.</span><span class="sxs-lookup"><span data-stu-id="f490f-156">`Resume-Job` resumes the `Test-Suspend` workflow in Job8.</span></span> <span data-ttu-id="f490f-157">De para meter **wait** wordt gebruikt om de opdracht prompt te bewaren totdat de taak wordt hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-157">It uses the **Wait** parameter to hold the command prompt until the job is resumed.</span></span>

<span data-ttu-id="f490f-158">`Receive-Job`Met de cmdlet worden de resultaten van de `Test-Suspend` werk stroom opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f490f-158">The `Receive-Job` cmdlet gets the results of the `Test-Suspend` workflow.</span></span> <span data-ttu-id="f490f-159">De laatste opdracht in de werk stroom retourneert een **span** -object dat de verstreken tijd vertegenwoordigt tussen de huidige datum en tijd en de datum en tijd die zijn opgeslagen in de `$a` variabele voordat de werk stroom werd onderbroken.</span><span class="sxs-lookup"><span data-stu-id="f490f-159">The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the `$a` variable before the workflow was suspended.</span></span>

```
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

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

<span data-ttu-id="f490f-160">`Resume-Job`Met de cmdlet kunt u een werk stroom taak hervatten die is onderbroken door gebruik te maken van de `Suspend-Workflow` activiteit.</span><span class="sxs-lookup"><span data-stu-id="f490f-160">The `Resume-Job` cmdlet lets you resume a workflow job that was suspend by using the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="f490f-161">Met deze activiteit wordt een werk stroom in een werk stroom onderbroken.</span><span class="sxs-lookup"><span data-stu-id="f490f-161">This activity suspends a workflow from within a workflow.</span></span> <span data-ttu-id="f490f-162">Het is alleen geldig in werk stromen.</span><span class="sxs-lookup"><span data-stu-id="f490f-162">It is valid only in workflows.</span></span>

<span data-ttu-id="f490f-163">Zie voor meer informatie over de `Suspend-Workflow` , About_Suspend werk stroom] (.. /PSWorkflow/about/about_Suspend-werk stroom. MD).</span><span class="sxs-lookup"><span data-stu-id="f490f-163">For information about the `Suspend-Workflow`, see about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md).</span></span>

## <span data-ttu-id="f490f-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f490f-164">PARAMETERS</span></span>

### <span data-ttu-id="f490f-165">-Filter</span><span class="sxs-lookup"><span data-stu-id="f490f-165">-Filter</span></span>

<span data-ttu-id="f490f-166">Hiermee geeft u een hash-tabel met voor waarden op.</span><span class="sxs-lookup"><span data-stu-id="f490f-166">Specifies a hash table of conditions.</span></span> <span data-ttu-id="f490f-167">Met deze cmdlet worden taken hervat die voldoen aan alle voor waarden in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="f490f-167">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="f490f-168">Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="f490f-168">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="f490f-169">-Id</span><span class="sxs-lookup"><span data-stu-id="f490f-169">-Id</span></span>

<span data-ttu-id="f490f-170">Hiermee wordt een matrix met Id's opgegeven voor taken die met deze cmdlet worden hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-170">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="f490f-171">De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f490f-171">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="f490f-172">Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f490f-172">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="f490f-173">U kunt een of meer Id's typen, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="f490f-173">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="f490f-174">Voer uit om de ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f490f-174">To find the ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="f490f-175">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f490f-175">-InstanceId</span></span>

<span data-ttu-id="f490f-176">Hiermee geeft u een matrix met exemplaar-Id's van taken op die met deze cmdlet worden hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-176">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="f490f-177">De standaard waarde is alle taken.</span><span class="sxs-lookup"><span data-stu-id="f490f-177">The default is all jobs.</span></span>

<span data-ttu-id="f490f-178">Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="f490f-178">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="f490f-179">Voer uit om de exemplaar-ID van een taak te vinden `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f490f-179">To find the instance ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="f490f-180">-Taak</span><span class="sxs-lookup"><span data-stu-id="f490f-180">-Job</span></span>

<span data-ttu-id="f490f-181">Hiermee geeft u de taken op die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-181">Specifies the jobs to be resumed.</span></span> <span data-ttu-id="f490f-182">Voer een variabele in die de taken bevat of een opdracht waarmee de taken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f490f-182">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="f490f-183">U kunt ook taken door sluizen naar de `Resume-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f490f-183">You can also pipe jobs to the `Resume-Job` cmdlet.</span></span>

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

### <span data-ttu-id="f490f-184">-Name</span><span class="sxs-lookup"><span data-stu-id="f490f-184">-Name</span></span>

<span data-ttu-id="f490f-185">Hiermee geeft u een matrix met beschrijvende namen op van taken die met deze cmdlet worden hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-185">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="f490f-186">Voer een of meer taak namen in.</span><span class="sxs-lookup"><span data-stu-id="f490f-186">Enter one or more job names.</span></span>
<span data-ttu-id="f490f-187">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f490f-187">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f490f-188">-Status</span><span class="sxs-lookup"><span data-stu-id="f490f-188">-State</span></span>

<span data-ttu-id="f490f-189">Hiermee wordt de status van taken opgegeven die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-189">Specifies the state of jobs to resume.</span></span> <span data-ttu-id="f490f-190">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f490f-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f490f-191">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f490f-191">NotStarted</span></span>
- <span data-ttu-id="f490f-192">Wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="f490f-192">Running</span></span>
- <span data-ttu-id="f490f-193">Voltooid</span><span class="sxs-lookup"><span data-stu-id="f490f-193">Completed</span></span>
- <span data-ttu-id="f490f-194">Mislukt</span><span class="sxs-lookup"><span data-stu-id="f490f-194">Failed</span></span>
- <span data-ttu-id="f490f-195">Gestopt</span><span class="sxs-lookup"><span data-stu-id="f490f-195">Stopped</span></span>
- <span data-ttu-id="f490f-196">Geblokkeerd</span><span class="sxs-lookup"><span data-stu-id="f490f-196">Blocked</span></span>
- <span data-ttu-id="f490f-197">Onderbroken</span><span class="sxs-lookup"><span data-stu-id="f490f-197">Suspended</span></span>
- <span data-ttu-id="f490f-198">Ontkoppeld</span><span class="sxs-lookup"><span data-stu-id="f490f-198">Disconnected</span></span>
- <span data-ttu-id="f490f-199">Onderbreken</span><span class="sxs-lookup"><span data-stu-id="f490f-199">Suspending</span></span>
- <span data-ttu-id="f490f-200">Stoppen</span><span class="sxs-lookup"><span data-stu-id="f490f-200">Stopping</span></span>

<span data-ttu-id="f490f-201">Met deze cmdlet worden alleen taken hervat die de status **onderbroken** hebben.</span><span class="sxs-lookup"><span data-stu-id="f490f-201">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="f490f-202">Zie [JobState Enumeration](/dotnet/api/system.management.automation.jobstate)(Engelstalig) voor meer informatie over de status van een taak.</span><span class="sxs-lookup"><span data-stu-id="f490f-202">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="f490f-203">-Wachten</span><span class="sxs-lookup"><span data-stu-id="f490f-203">-Wait</span></span>

<span data-ttu-id="f490f-204">Geeft aan dat deze cmdlet de opdracht prompt onderdrukt voordat alle taak resultaten opnieuw worden gestart.</span><span class="sxs-lookup"><span data-stu-id="f490f-204">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span> <span data-ttu-id="f490f-205">Standaard retourneert deze cmdlet onmiddellijk de beschik bare resultaten.</span><span class="sxs-lookup"><span data-stu-id="f490f-205">By default, this cmdlet immediately returns the available results.</span></span>

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

### <span data-ttu-id="f490f-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f490f-206">-Confirm</span></span>

<span data-ttu-id="f490f-207">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f490f-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f490f-208">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f490f-208">-WhatIf</span></span>

<span data-ttu-id="f490f-209">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f490f-209">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f490f-210">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f490f-210">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f490f-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f490f-211">CommonParameters</span></span>

<span data-ttu-id="f490f-212">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f490f-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f490f-213">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f490f-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f490f-214">INVOER</span><span class="sxs-lookup"><span data-stu-id="f490f-214">INPUTS</span></span>

### <span data-ttu-id="f490f-215">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="f490f-215">System.Management.Automation.Job</span></span>

<span data-ttu-id="f490f-216">U kunt alle typen taken naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="f490f-216">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="f490f-217">Als er `Resume-Job` een taak wordt opgehaald van een type dat niet wordt ondersteund, wordt een afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f490f-217">If `Resume-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="f490f-218">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f490f-218">OUTPUTS</span></span>

### <span data-ttu-id="f490f-219">Geen, System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="f490f-219">None, System.Management.Automation.Job</span></span>

<span data-ttu-id="f490f-220">Met deze cmdlet worden de taken geretourneerd die worden hervat als u de para meter **PassThru** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f490f-220">This cmdlet returns the jobs that it tries to resume, if you use the **PassThru** parameter.</span></span>
<span data-ttu-id="f490f-221">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f490f-221">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f490f-222">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f490f-222">NOTES</span></span>

- <span data-ttu-id="f490f-223">`Resume-Job` kan alleen taken hervatten die zijn onderbroken.</span><span class="sxs-lookup"><span data-stu-id="f490f-223">`Resume-Job` can only resume jobs that are suspended.</span></span> <span data-ttu-id="f490f-224">Als u een taak in een andere status verzendt, `Resume-Job` wordt de bewerking hervatten voor de taak uitgevoerd, maar er wordt een waarschuwing gegenereerd om u te melden dat de taak niet kan worden hervat.</span><span class="sxs-lookup"><span data-stu-id="f490f-224">If you submit a job in a different state, `Resume-Job` runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="f490f-225">Als u de waarschuwing wilt onderdrukken, gebruikt u de gemeen schappelijke **WarningAction** para meter met de waarde SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="f490f-225">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>
- <span data-ttu-id="f490f-226">Als een taak niet van een type is dat hervatten ondersteunt, zoals een werk stroom taak ( **PSWorkflowJob** ), `Resume-Job` wordt er een afsluit fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f490f-226">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), `Resume-Job` returns a terminating error.</span></span>
- <span data-ttu-id="f490f-227">Het mechanisme en de locatie voor het opslaan van een onderbroken taak kunnen variëren afhankelijk van het taak type.</span><span class="sxs-lookup"><span data-stu-id="f490f-227">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="f490f-228">Onderbroken werk stroom taken worden bijvoorbeeld standaard opgeslagen in een plat bestands archief, maar kunnen ook worden opgeslagen in een SQL database.</span><span class="sxs-lookup"><span data-stu-id="f490f-228">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
- <span data-ttu-id="f490f-229">Wanneer u een taak hervat, wordt de status van de taak gewijzigd van **opgeschort** in **actief**.</span><span class="sxs-lookup"><span data-stu-id="f490f-229">When you resume a job, the job state changes from **Suspended** to **Running**.</span></span> <span data-ttu-id="f490f-230">Als u de taken wilt vinden die worden uitgevoerd, met inbegrip van die die zijn hervat door deze cmdlet, gebruikt u de para meter **State** van de `Get-Job` cmdlet om taken in de **actieve** status op te halen.</span><span class="sxs-lookup"><span data-stu-id="f490f-230">To find the jobs that are running, including those that were resumed by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get jobs in the **Running** state.</span></span>
- <span data-ttu-id="f490f-231">Sommige taak typen hebben opties of eigenschappen die verhinderen dat Windows Power shell de taak onderbreekt.</span><span class="sxs-lookup"><span data-stu-id="f490f-231">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="f490f-232">Als er wordt geprobeerd de taak te onderbreken, controleert u of de taak opties en eigenschappen het blok keren toestaan.</span><span class="sxs-lookup"><span data-stu-id="f490f-232">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="f490f-233">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f490f-233">RELATED LINKS</span></span>

[<span data-ttu-id="f490f-234">Get-job</span><span class="sxs-lookup"><span data-stu-id="f490f-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="f490f-235">Receive-job</span><span class="sxs-lookup"><span data-stu-id="f490f-235">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="f490f-236">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="f490f-236">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="f490f-237">Begin taak</span><span class="sxs-lookup"><span data-stu-id="f490f-237">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f490f-238">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="f490f-238">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="f490f-239">Onderbreken-taak</span><span class="sxs-lookup"><span data-stu-id="f490f-239">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="f490f-240">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f490f-240">Wait-Job</span></span>](Wait-Job.md)
