---
description: Hierin worden geavanceerde geplande taak onderwerpen beschreven, met inbegrip van de bestands structuur waarin geplande taken worden uitgevoerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252413"
---
# <a name="about-scheduled-jobs-advanced"></a><span data-ttu-id="0a505-104">Over geplande taken Geavanceerd</span><span class="sxs-lookup"><span data-stu-id="0a505-104">About Scheduled Jobs Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="0a505-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="0a505-105">Short description</span></span>

<span data-ttu-id="0a505-106">Hierin worden geavanceerde geplande taak onderwerpen beschreven, met inbegrip van de bestands structuur waarin geplande taken worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a505-106">Explains advanced scheduled job topics, including the file structure that underlies scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="0a505-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="0a505-107">Long description</span></span>

<span data-ttu-id="0a505-108">Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.</span><span class="sxs-lookup"><span data-stu-id="0a505-108">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="scheduled-job-directories-and-files"></a><span data-ttu-id="0a505-109">Geplande mappen en bestanden voor de taak</span><span class="sxs-lookup"><span data-stu-id="0a505-109">Scheduled job directories and files</span></span>

<span data-ttu-id="0a505-110">Geplande power shell-taken zijn zowel Power shell-taken als taak planner taken.</span><span class="sxs-lookup"><span data-stu-id="0a505-110">PowerShell scheduled jobs are both PowerShell jobs and Task Scheduler tasks.</span></span>
<span data-ttu-id="0a505-111">Elke geplande taak wordt geregistreerd in de taak planner en opgeslagen op schijf in de XML-indeling van Microsoft .NET Framework-serialisatie.</span><span class="sxs-lookup"><span data-stu-id="0a505-111">Each scheduled job is registered in Task Scheduler and saved on disk in Microsoft .NET Framework Serialization XML format.</span></span>

<span data-ttu-id="0a505-112">Wanneer u een geplande taak maakt, maakt Power shell een map voor de geplande taak in de `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0a505-112">When you create a scheduled job, PowerShell creates a directory for the scheduled job in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span> <span data-ttu-id="0a505-113">De mapnaam is hetzelfde als de naam van de taak.</span><span class="sxs-lookup"><span data-stu-id="0a505-113">The directory name is the same as the job name.</span></span>

<span data-ttu-id="0a505-114">Hier volgt een voor beeld van een **ScheduledJobs** -map.</span><span class="sxs-lookup"><span data-stu-id="0a505-114">The following is a sample **ScheduledJobs** directory.</span></span>

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

<span data-ttu-id="0a505-115">Elke geplande taak heeft een eigen map.</span><span class="sxs-lookup"><span data-stu-id="0a505-115">Each scheduled job has its own directory.</span></span> <span data-ttu-id="0a505-116">De map bevat het XML-bestand met de geplande taak en een **uitvoer** subdirectory.</span><span class="sxs-lookup"><span data-stu-id="0a505-116">The directory contains the scheduled job XML file and an **Output** subdirectory.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

<span data-ttu-id="0a505-117">De **uitvoermap** voor een geplande taak bevat de uitvoerings geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="0a505-117">The **Output** directory for a scheduled job contains its execution history.</span></span>
<span data-ttu-id="0a505-118">Telkens wanneer een taak trigger een geplande taak start, maakt Power shell een naam van een time stamp-map in de uitvoermap.</span><span class="sxs-lookup"><span data-stu-id="0a505-118">Each time a job trigger starts a scheduled job, PowerShell creates a timestamp-named directory in the output directory.</span></span> <span data-ttu-id="0a505-119">De time stamp-map bevat de resultaten van de taak in een **Results.xml** -bestand en de taak status in een **Status.xml** bestand.</span><span class="sxs-lookup"><span data-stu-id="0a505-119">The timestamp directory contains the results of the job in a **Results.xml** file and the job status in a **Status.xml** file.</span></span>

<span data-ttu-id="0a505-120">De volgende opdracht toont de uitvoerings geschiedenis mappen voor de geplande taak **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="0a505-120">The following command shows the execution history directories for the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

<span data-ttu-id="0a505-121">U kunt de bestanden van de **ScheduledJobDefinition.xml** , **Results.xml** en **Status.xml** openen en bekijken of de `Select-XML` cmdlet gebruiken om het bestand te parseren.</span><span class="sxs-lookup"><span data-stu-id="0a505-121">You can open and examine the **ScheduledJobDefinition.xml** , **Results.xml** and **Status.xml** files or use the `Select-XML` cmdlet to parse the files.</span></span>

> [!WARNING]
> <span data-ttu-id="0a505-122">Bewerk de XML-bestanden niet.</span><span class="sxs-lookup"><span data-stu-id="0a505-122">Do not edit the XML files.</span></span> <span data-ttu-id="0a505-123">Als een XML-bestand ongeldige XML bevat, verwijdert Power shell de geplande taak en de uitvoerings geschiedenis, inclusief de taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="0a505-123">If any XML file contains invalid XML, PowerShell deletes the scheduled job and its execution history, including job results.</span></span>

## <a name="start-a-scheduled-job-immediately"></a><span data-ttu-id="0a505-124">Een geplande taak onmiddellijk starten</span><span class="sxs-lookup"><span data-stu-id="0a505-124">Start a scheduled job immediately</span></span>

<span data-ttu-id="0a505-125">U kunt een geplande taak onmiddellijk op een van de volgende twee manieren starten:</span><span class="sxs-lookup"><span data-stu-id="0a505-125">You can start a scheduled job immediately in one of two ways:</span></span>

- <span data-ttu-id="0a505-126">Voer de `Start-Job` cmdlet uit om een geplande taak te starten.</span><span class="sxs-lookup"><span data-stu-id="0a505-126">Run the `Start-Job` cmdlet to start any scheduled job.</span></span>
- <span data-ttu-id="0a505-127">Voeg de **RunNow** -para meter toe aan de `Register-ScheduledJob` opdracht om de taak te starten zodra de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0a505-127">Add the **RunNow** parameter to your `Register-ScheduledJob` command to start the job as soon as the command is run.</span></span>

<span data-ttu-id="0a505-128">Taken die zijn gestart met behulp van de `Start-Job` cmdlet zijn standaard-Power shell-achtergrond taken, geen exemplaren van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="0a505-128">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="0a505-129">Net als alle achtergrond taken worden deze taken onmiddellijk gestart, niet onderhevig aan taak opties of worden beïnvloed door taak triggers.</span><span class="sxs-lookup"><span data-stu-id="0a505-129">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers.</span></span> <span data-ttu-id="0a505-130">De taak uitvoer wordt niet opgeslagen in de **uitvoermap** van de geplande projectmap.</span><span class="sxs-lookup"><span data-stu-id="0a505-130">The job output isn't saved in the **Output** directory of the scheduled job directory.</span></span>

<span data-ttu-id="0a505-131">De volgende opdracht maakt gebruik van de para meter **definitienaam** van de `Start-Job` cmdlet om de geplande taak ProcessJob te starten.</span><span class="sxs-lookup"><span data-stu-id="0a505-131">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the ProcessJob scheduled job.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="0a505-132">Gebruik de taak-cmdlets om de taak te beheren en de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="0a505-132">To manage the job and get the job results, use the job cmdlets.</span></span> <span data-ttu-id="0a505-133">Zie [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)voor meer informatie over de taak-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0a505-133">For more information about the job cmdlets, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0a505-134">Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="0a505-134">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="0a505-135">Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="0a505-135">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

## <a name="rename-a-scheduled-job"></a><span data-ttu-id="0a505-136">De naam van een geplande taak wijzigen</span><span class="sxs-lookup"><span data-stu-id="0a505-136">Rename a scheduled job</span></span>

<span data-ttu-id="0a505-137">Als u de naam van een geplande taak wilt wijzigen, gebruikt u de para meter name van de `Set-ScheduledJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0a505-137">To rename a scheduled job, use the Name parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="0a505-138">Wanneer u de naam van een geplande taak wijzigt, wijzigt Power shell de naam van de geplande taak en de map geplande taak.</span><span class="sxs-lookup"><span data-stu-id="0a505-138">When you rename a scheduled job, PowerShell changes the name of the scheduled job and the scheduled job directory.</span></span> <span data-ttu-id="0a505-139">De namen van exemplaren van de geplande taak die al zijn uitgevoerd, worden echter niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="0a505-139">However, it doesn't change the names of instances of the scheduled job that have already run.</span></span>

## <a name="get-start-and-end-times"></a><span data-ttu-id="0a505-140">Begin-en eind tijden ophalen</span><span class="sxs-lookup"><span data-stu-id="0a505-140">Get start and end times</span></span>

<span data-ttu-id="0a505-141">Gebruik de eigenschappen **PSBeginTime** en **PSEndTime** van het ScheduledJob-object dat `Get-Job` wordt geretourneerd voor geplande taken om de datums en tijden te verkrijgen waarop de taak exemplaren zijn gestart en beëindigd.</span><span class="sxs-lookup"><span data-stu-id="0a505-141">To get the dates and times that job instances started and ended, use the **PSBeginTime** and **PSEndTime** properties of the ScheduledJob object that `Get-Job` returns for scheduled jobs.</span></span>

<span data-ttu-id="0a505-142">In het volgende voor beeld wordt de **eigenschap** para meter van de `Format-Table` cmdlet gebruikt om de eigenschappen **PSBeginTime** en **PSEndTime** van elk taak exemplaar in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="0a505-142">The following example uses the **Property** parameter of the `Format-Table` cmdlet to display the **PSBeginTime** and **PSEndTime** properties of each job instance in a table.</span></span> <span data-ttu-id="0a505-143">Een berekende eigenschap met de naam **Label** toont de verstreken tijd van elk taak exemplaar.</span><span class="sxs-lookup"><span data-stu-id="0a505-143">A calculated property named **Label** displays the elapsed time of each job instance.</span></span>

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a><span data-ttu-id="0a505-144">Uitvoerings geschiedenis beheren</span><span class="sxs-lookup"><span data-stu-id="0a505-144">Manage execution history</span></span>

<span data-ttu-id="0a505-145">U kunt het aantal taak instantie resultaten bepalen dat voor elke geplande taak wordt opgeslagen en de uitvoerings geschiedenis en de opgeslagen taak resultaten van een geplande taak verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0a505-145">You can determine the number of job instance results that are saved for each scheduled job and delete the execution history and saved job results of any scheduled job.</span></span>

<span data-ttu-id="0a505-146">De eigenschap **ExecutionHistoryLength** van een geplande taak bepaalt hoeveel taak exemplaar resultaten voor de geplande taak worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0a505-146">The **ExecutionHistoryLength** property of a scheduled job determines how many job instance results are saved for the scheduled job.</span></span> <span data-ttu-id="0a505-147">Wanneer het aantal opgeslagen resultaten de waarde van de eigenschap **ExecutionHistoryLength** overschrijdt, verwijdert Power shell de resultaten van de oudste instantie om ruimte te maken voor de resultaten van het nieuwste exemplaar.</span><span class="sxs-lookup"><span data-stu-id="0a505-147">When the number of saved results exceeds the value of the **ExecutionHistoryLength** property, PowerShell deletes the results of the oldest instance to make room for the results of the newest instance.</span></span>

<span data-ttu-id="0a505-148">Standaard slaat Power shell de uitvoerings geschiedenis en resultaten van 32 exemplaren van elke geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="0a505-148">By default, PowerShell saves the execution history and results of 32 instances of each scheduled job.</span></span> <span data-ttu-id="0a505-149">Als u deze waarde wilt wijzigen, gebruikt u de para meters van de **MaxResultCount** van de- `Register-ScheduledJob` of- `Set-ScheduledJob` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0a505-149">To change that value, use the **MaxResultCount** parameters of the `Register-ScheduledJob` or `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="0a505-150">Als u de uitvoerings geschiedenis en alle resultaten voor een geplande taak wilt verwijderen, gebruikt u de para meter **ClearExecutionHistory** van de `Set-ScheduledJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0a505-150">To delete the execution history and all results for a scheduled job, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="0a505-151">Als u deze uitvoerings geschiedenis verwijdert, wordt niet voor komen dat Power shell de resultaten van nieuwe exemplaren van de geplande taak opslaat.</span><span class="sxs-lookup"><span data-stu-id="0a505-151">Deleting this execution history does not prevent PowerShell from saving the results of new instances of the scheduled job.</span></span>

<span data-ttu-id="0a505-152">In het volgende voor beeld wordt splatting gebruikt om `$JobParms` de parameter waarden te maken die worden door gegeven aan de `Register-ScheduledJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0a505-152">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="0a505-153">Zie [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0a505-153">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="0a505-154">`Register-ScheduledJob`Hiermee `@JobParms` maakt u een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="0a505-154">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="0a505-155">De opdracht gebruikt de para meter **MaxResultCount** met de waarde 12 om alleen de 12 nieuwste taak instantie resultaten van de geplande taak op te slaan.</span><span class="sxs-lookup"><span data-stu-id="0a505-155">The command uses the **MaxResultCount** parameter with a value of 12 to save only the 12 newest job instance results of the scheduled job.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="0a505-156">De volgende opdracht maakt gebruik van de para meter **MaxResultCount** van de `Set-ScheduledJob` cmdlet om het aantal opgeslagen instantie resultaten te verhogen naar</span><span class="sxs-lookup"><span data-stu-id="0a505-156">The following command uses the **MaxResultCount** parameter of the `Set-ScheduledJob` cmdlet to increase the number of saved instance results to</span></span>
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

<span data-ttu-id="0a505-157">Met de volgende opdracht worden de uitvoerings geschiedenis en de huidige opgeslagen resultaten van de geplande taak **ProcessJob** verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0a505-157">The following command deletes the execution history and the current saved results of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="0a505-158">Met de volgende opdracht worden de waarden van de eigenschappen name en **ExecutionHistoryLength** van alle geplande taken op de computer opgehaald en weer gegeven in een tabel.</span><span class="sxs-lookup"><span data-stu-id="0a505-158">The following command gets the values of the name and **ExecutionHistoryLength** properties of all scheduled jobs on the computer and displays them in a table.</span></span>

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a><span data-ttu-id="0a505-159">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0a505-159">See also</span></span>

[<span data-ttu-id="0a505-160">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="0a505-160">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="0a505-161">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="0a505-161">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="0a505-162">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="0a505-162">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="0a505-163">about_Splatting. MD</span><span class="sxs-lookup"><span data-stu-id="0a505-163">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="0a505-164">[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets</span><span class="sxs-lookup"><span data-stu-id="0a505-164">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="0a505-165">Taak planner</span><span class="sxs-lookup"><span data-stu-id="0a505-165">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
