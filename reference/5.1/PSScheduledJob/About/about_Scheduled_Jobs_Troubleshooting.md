---
description: Legt uit hoe u problemen met geplande taken kunt oplossen
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: 924205edb9d44724cfef201d84baa304ecde67ad
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252409"
---
# <a name="about-scheduled-jobs-troubleshooting"></a><span data-ttu-id="00b40-104">Over het oplossen van problemen met geplande taken</span><span class="sxs-lookup"><span data-stu-id="00b40-104">About Scheduled Jobs Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="00b40-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="00b40-105">Short description</span></span>

<span data-ttu-id="00b40-106">Legt uit hoe u problemen met geplande taken kunt oplossen</span><span class="sxs-lookup"><span data-stu-id="00b40-106">Explains how to resolve problems with scheduled jobs</span></span>

## <a name="long-description"></a><span data-ttu-id="00b40-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="00b40-107">Long description</span></span>

<span data-ttu-id="00b40-108">In dit document worden enkele van de problemen beschreven die u kunt ondervinden bij het gebruik van de geplande taak functies van Power shell en worden oplossingen voor deze problemen voorgesteld.</span><span class="sxs-lookup"><span data-stu-id="00b40-108">This document describes some of the problems that you might experience when using the scheduled job features of PowerShell and it suggests solutions to these problems.</span></span>

<span data-ttu-id="00b40-109">Zie [about_Scheduled_Jobs](about_Scheduled_Jobs.md) en de gerelateerde geplande taken over onderwerpen voor informatie over het gebruik van Power shell-geplande taken.</span><span class="sxs-lookup"><span data-stu-id="00b40-109">Before using PowerShell scheduled jobs, see [about_Scheduled_Jobs](about_Scheduled_Jobs.md) and the related scheduled jobs about topics.</span></span>

<span data-ttu-id="00b40-110">Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.</span><span class="sxs-lookup"><span data-stu-id="00b40-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="cant-find-job-results"></a><span data-ttu-id="00b40-111">Kan geen taak resultaten vinden</span><span class="sxs-lookup"><span data-stu-id="00b40-111">Can't find job results</span></span>

### <a name="basic-method-for-getting-job-results-in-powershell"></a><span data-ttu-id="00b40-112">Basis methode voor het ophalen van taak resultaten in Power shell</span><span class="sxs-lookup"><span data-stu-id="00b40-112">Basic method for getting job results in PowerShell</span></span>

<span data-ttu-id="00b40-113">Wanneer een geplande taak wordt uitgevoerd, wordt er een exemplaar van de geplande taak gemaakt.</span><span class="sxs-lookup"><span data-stu-id="00b40-113">When a scheduled job runs, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="00b40-114">Gebruik de taak-cmdlets om de resultaten van geplande taak exemplaren weer te geven, te beheren en op te halen.</span><span class="sxs-lookup"><span data-stu-id="00b40-114">To view, manage, and get the results of scheduled job instances, use the Job cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="00b40-115">Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="00b40-115">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="00b40-116">Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="00b40-116">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="00b40-117">Als u een lijst wilt weer geven van alle exemplaren van een geplande taak, gebruikt u de `Get-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00b40-117">To get a list of all instances of a scheduled job, use the `Get-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

<span data-ttu-id="00b40-118">De `Get-Job` cmdlet verzendt **ProcessJob** -objecten omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="00b40-118">The `Get-Job` cmdlet sends **ProcessJob** objects down the pipeline.</span></span> <span data-ttu-id="00b40-119">`Format-Table`Met de cmdlet worden de eigenschappen **name** , **id** en **PSBeginTime** van een geplande taak instantie in een tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="00b40-119">The `Format-Table` cmdlet displays the **Name** , **ID** , and **PSBeginTime** properties of a scheduled job instance in a table.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

<span data-ttu-id="00b40-120">Gebruik de cmdlet om de resultaten van een exemplaar van een geplande taak op te halen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="00b40-120">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="00b40-121">Met de volgende opdracht worden de resultaten van het nieuwste exemplaar van de ProcessJob (ID = 50) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="00b40-121">The following command gets the results of the newest instance of the ProcessJob (ID = 50).</span></span>

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a><span data-ttu-id="00b40-122">Basis methode voor het zoeken naar taak resultaten op schijf</span><span class="sxs-lookup"><span data-stu-id="00b40-122">Basic method for finding job results on disk</span></span>

<span data-ttu-id="00b40-123">Als u geplande taken wilt beheren, gebruikt u de taak-cmdlets, zoals `Get-Job` en `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="00b40-123">To manage scheduled jobs, use the job cmdlets, such as `Get-Job` and `Receive-Job`.</span></span>

<span data-ttu-id="00b40-124">Als `Get-Job` het taak exemplaar niet wordt opgehaald of `Receive-Job` de taak resultaten niet worden opgehaald, kunt u de uitvoerings geschiedenis bestanden voor de taak zoeken op schijf.</span><span class="sxs-lookup"><span data-stu-id="00b40-124">If `Get-Job` does not get the job instance or `Receive-Job` does not get the job results, you can search the execution history files for the job on disk.</span></span>
<span data-ttu-id="00b40-125">De uitvoerings geschiedenis bevat een record van alle geactiveerde taak exemplaren.</span><span class="sxs-lookup"><span data-stu-id="00b40-125">The execution history contains a record of all triggered job instances.</span></span>

<span data-ttu-id="00b40-126">Controleer of er een time stamp-naam voor komt in de Directory voor een geplande taak in het volgende pad:</span><span class="sxs-lookup"><span data-stu-id="00b40-126">Verify that there is a timestamp-named directory in the directory for a scheduled job in the following path:</span></span>

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="00b40-127">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="00b40-127">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="00b40-128">Met de `Get-ChildItem` cmdlet wordt bijvoorbeeld de uitvoerings geschiedenis op schijf opgehaald van de geplande taak **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="00b40-128">For example, the `Get-ChildItem` cmdlet gets the on-disk execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

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

<span data-ttu-id="00b40-129">Elke time stamp-naam directory vertegenwoordigt een taak exemplaar.</span><span class="sxs-lookup"><span data-stu-id="00b40-129">Each timestamp-named directory represents a job instance.</span></span> <span data-ttu-id="00b40-130">De resultaten van elk taak exemplaar worden opgeslagen in een **Results.xml** -bestand in de map met de naam van de tijds tempel.</span><span class="sxs-lookup"><span data-stu-id="00b40-130">The results of each job instance are saved in a **Results.xml** file in the timestamp-named directory.</span></span>

<span data-ttu-id="00b40-131">Met de volgende opdracht worden bijvoorbeeld de **Results.xml** -bestanden voor elk opgeslagen exemplaar van de geplande taak **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="00b40-131">For example, the following command gets the **Results.xml** files for every saved instance of the **ProcessJob** scheduled job.</span></span> <span data-ttu-id="00b40-132">Als het **Results.xml** bestand ontbreekt, kan Power shell de taak resultaten niet retour neren of weer geven.</span><span class="sxs-lookup"><span data-stu-id="00b40-132">If the **Results.xml** file is missing, PowerShell cannot return or display the job results.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

<span data-ttu-id="00b40-133">Het is mogelijk dat de taak-cmdlet geen geplande taak exemplaren of de bijbehorende resultaten kan ophalen omdat de **PSScheduledJob** -module niet is geïmporteerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="00b40-133">The job cmdlet might not be able to get scheduled job instances or their results because the **PSScheduledJob** module is not imported into the session.</span></span>

> [!NOTE]
> <span data-ttu-id="00b40-134">Voordat u een taak-cmdlet gebruikt voor geplande taak instanties, controleert u of de **PSScheduledJob** -module is opgenomen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="00b40-134">Before using a job cmdlet on scheduled job instances, verify that the **PSScheduledJob** module is included in the session.</span></span> <span data-ttu-id="00b40-135">Zonder de **PSScheduledJob** -module kunnen de taak-cmdlets geen geplande taak exemplaren of hun resultaten ophalen.</span><span class="sxs-lookup"><span data-stu-id="00b40-135">Without the **PSScheduledJob** module, the job cmdlets cannot get scheduled job instances or their results.</span></span>

<span data-ttu-id="00b40-136">De **PSScheduledJob** -module importeren:</span><span class="sxs-lookup"><span data-stu-id="00b40-136">To import the **PSScheduledJob** module:</span></span>

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a><span data-ttu-id="00b40-137">De resultaten zijn mogelijk al geretourneerd door de Receive-Job-cmdlet</span><span class="sxs-lookup"><span data-stu-id="00b40-137">Receive-Job cmdlet might already have returned the results</span></span>

<span data-ttu-id="00b40-138">Als geen `Receive-Job` taak exemplaar resultaat retourneert, kan dit zijn omdat er een `Receive-Job` opdracht voor dat taak exemplaar is uitgevoerd in de huidige sessie zonder de para meter **Keep** .</span><span class="sxs-lookup"><span data-stu-id="00b40-138">If `Receive-Job` does not return job instance results, it might be because a `Receive-Job` command has been run for that job instance in the current session without the **Keep** parameter.</span></span>

<span data-ttu-id="00b40-139">Wanneer u gebruikt `Receive-Job` zonder de para meter **Keep** , worden `Receive-Job` de taak resultaten geretourneerd en wordt de eigenschap **HasMoreData** van het taak exemplaar ingesteld op **Onwaar**.</span><span class="sxs-lookup"><span data-stu-id="00b40-139">When you use `Receive-Job` without the **Keep** parameter, `Receive-Job` returns the job results and sets the job instance's **HasMoreData** property to **False**.</span></span> <span data-ttu-id="00b40-140">De waarde **Onwaar** geeft `Receive-Job` aan dat de resultaten van de taak zijn geretourneerd en het exemplaar heeft geen resultaten meer die kunnen worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="00b40-140">The **False** value means that `Receive-Job` returned the job's results and the instance has no more results to return.</span></span> <span data-ttu-id="00b40-141">Deze instelling is geschikt voor standaard achtergrond taken, maar niet voor exemplaren van geplande taken die op schijf worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="00b40-141">This setting is appropriate for standard background jobs, but not for instances of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="00b40-142">Als u de resultaten van de taak instantie opnieuw wilt ophalen, start u een nieuwe Power shell-sessie door te typen `PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="00b40-142">To get the job instance results again, start a new PowerShell session by typing `PowerShell`.</span></span> <span data-ttu-id="00b40-143">Importeer de **PSScheduledJob** -module en voer de `Receive-Job` opdracht opnieuw uit.</span><span class="sxs-lookup"><span data-stu-id="00b40-143">Import the **PSScheduledJob** module, and try the `Receive-Job` command again.</span></span>

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a><span data-ttu-id="00b40-144">De para meter Keep gebruiken om resultaten meer dan één keer in een sessie op te halen</span><span class="sxs-lookup"><span data-stu-id="00b40-144">Using Keep parameter to get results more than one time in a session</span></span>

<span data-ttu-id="00b40-145">Als u het resultaat van een taak exemplaar in een sessie meer dan één keer wilt ophalen, gebruikt u de para meter **Keep** van de `Receive-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00b40-145">To get the result of a job instance more than one time in a session, use the **Keep** parameter of the `Receive-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a><span data-ttu-id="00b40-146">De geplande taak is mogelijk beschadigd</span><span class="sxs-lookup"><span data-stu-id="00b40-146">The scheduled job might be corrupted</span></span>

<span data-ttu-id="00b40-147">Als een geplande taak beschadigd raakt, verwijdert Power shell de beschadigde geplande taak en de resultaten ervan.</span><span class="sxs-lookup"><span data-stu-id="00b40-147">If a scheduled job becomes corrupted, PowerShell deletes the corrupted scheduled job and its results.</span></span> <span data-ttu-id="00b40-148">U kunt de resultaten van een beschadigde geplande taak niet herstellen.</span><span class="sxs-lookup"><span data-stu-id="00b40-148">You cannot recover the results of a corrupted scheduled job.</span></span>

<span data-ttu-id="00b40-149">Gebruik de cmdlet om te bepalen of een geplande taak nog bestaat `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="00b40-149">To determine if a scheduled job still exists, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a><span data-ttu-id="00b40-150">Het aantal resultaten kan de ExecutionHistoryLength overschrijden</span><span class="sxs-lookup"><span data-stu-id="00b40-150">The number of results might have exceeded the ExecutionHistoryLength</span></span>

<span data-ttu-id="00b40-151">De eigenschap **ExecutionHistoryLength** van een geplande taak bepaalt hoeveel taak exemplaren en de bijbehorende resultaten worden opgeslagen op schijf.</span><span class="sxs-lookup"><span data-stu-id="00b40-151">The **ExecutionHistoryLength** property of a scheduled job determines how many job instances, and their results, are saved to disk.</span></span> <span data-ttu-id="00b40-152">De standaard waarde is 32.</span><span class="sxs-lookup"><span data-stu-id="00b40-152">The default value is 32.</span></span>
<span data-ttu-id="00b40-153">Wanneer het aantal exemplaren van een geplande taak deze waarde overschrijdt, verwijdert Power shell het oudste taak exemplaar om ruimte te maken voor elk nieuw taak exemplaar.</span><span class="sxs-lookup"><span data-stu-id="00b40-153">When the number of instances of a scheduled job exceeds this value, PowerShell deletes the oldest job instance to make room for each new job instance.</span></span>

<span data-ttu-id="00b40-154">Als u de waarde van de eigenschap **ExecutionHistoryLength** van een geplande taak wilt ophalen, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="00b40-154">To get the value of the **ExecutionHistoryLength** property of a scheduled job, use the following command format:</span></span>

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

<span data-ttu-id="00b40-155">Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **ExecutionHistoryLength** van de geplande **ProcessJob** -taak opgehaald.</span><span class="sxs-lookup"><span data-stu-id="00b40-155">For example, the following command gets the value of the **ExecutionHistoryLength** property of the **ProcessJob** scheduled job.</span></span>

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

<span data-ttu-id="00b40-156">Als u de waarde van de eigenschap **ExecutionHistoryLength** wilt instellen of wijzigen, gebruikt u de para meter **MaxResultCount** van de `Register-ScheduledJob` `Set-ScheduledJob` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="00b40-156">To set or change the value of the **ExecutionHistoryLength** property, use the **MaxResultCount** parameter of the `Register-ScheduledJob` and `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="00b40-157">Met de volgende opdracht wordt de waarde van de eigenschap **ExecutionHistoryLength** verhoogd naar 50.</span><span class="sxs-lookup"><span data-stu-id="00b40-157">The following command increases the value of the **ExecutionHistoryLength** property to 50.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a><span data-ttu-id="00b40-158">De resultaten van de taak instantie zijn mogelijk verwijderd</span><span class="sxs-lookup"><span data-stu-id="00b40-158">The job instance results might have been deleted</span></span>

<span data-ttu-id="00b40-159">Met de para meter **ClearExecutionHistory** van de `Set-ScheduledJob` cmdlet wordt de uitvoerings geschiedenis van een taak verwijderd.</span><span class="sxs-lookup"><span data-stu-id="00b40-159">The **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet deletes the execution history of a job.</span></span> <span data-ttu-id="00b40-160">U kunt deze functie gebruiken om schijf ruimte vrij te maken of resultaten te verwijderen die niet nodig zijn of al zijn gebruikt, te analyseren of op een andere locatie op te slaan.</span><span class="sxs-lookup"><span data-stu-id="00b40-160">You can use this feature to free up disk space or delete results that are not needed, or already used, analyzed or saved in a different location.</span></span>

<span data-ttu-id="00b40-161">Als u de uitvoerings geschiedenis van een geplande taak wilt verwijderen, gebruikt u de para meter **ClearExecutionHistory** van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="00b40-161">To delete the execution history of a scheduled job, use the **ClearExecutionHistory** parameter of the scheduled job.</span></span>

<span data-ttu-id="00b40-162">Met de volgende opdracht wordt de uitvoerings geschiedenis van de geplande taak **ProcessJob** verwijderd.</span><span class="sxs-lookup"><span data-stu-id="00b40-162">The following command deletes the execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="00b40-163">De `Remove-Job` cmdlet verwijdert ook taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="00b40-163">Also, the `Remove-Job` cmdlet deletes job results.</span></span> <span data-ttu-id="00b40-164">Wanneer u gebruikt `Remove-Job` om een geplande taak te verwijderen, worden alle exemplaren van de taak op de schijf verwijderd, inclusief de uitvoerings geschiedenis en alle taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="00b40-164">When you use `Remove-Job` to delete a scheduled job, it deletes all instances of the job on disk, including the execution history and all job results.</span></span>

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a><span data-ttu-id="00b40-165">Taken die zijn gestart met behulp van de cmdlet Start-Job worden niet op schijf opgeslagen</span><span class="sxs-lookup"><span data-stu-id="00b40-165">Jobs started by using the Start-Job cmdlet are not saved to disk</span></span>

<span data-ttu-id="00b40-166">Wanneer u gebruikt `Start-Job` om een geplande taak te starten in plaats van een taak trigger te gebruiken, `Start-Job` wordt een standaard achtergrond taak gestart.</span><span class="sxs-lookup"><span data-stu-id="00b40-166">When you use `Start-Job` to start a scheduled job, instead of using a job trigger, `Start-Job` starts a standard background job.</span></span> <span data-ttu-id="00b40-167">De achtergrond taak en de bijbehorende resultaten worden niet opgeslagen in de uitvoerings geschiedenis van de taak op schijf.</span><span class="sxs-lookup"><span data-stu-id="00b40-167">The background job and its results are not stored in the execution history of the job on disk.</span></span>

<span data-ttu-id="00b40-168">U kunt de- `Get-Job` cmdlet gebruiken om de taak en de `Receive-Job` cmdlet op te halen om de resultaten van de taak op te halen, maar de resultaten zijn pas beschikbaar nadat u ze hebt ontvangen, tenzij u de para meter Keep van de `Receive-Job` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00b40-168">You can use the `Get-Job` cmdlet to get the job and the `Receive-Job` cmdlet to get the job results, but the results are available only until you receive them, unless you use the Keep parameter of the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="00b40-169">Achtergrond taken en de bijbehorende resultaten zijn ook specifieke sessies; ze bestaan alleen in de sessie waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="00b40-169">Also, background jobs and their results are session-specific; they exist only in the session in which they are created.</span></span> <span data-ttu-id="00b40-170">Als u de taak verwijdert met `Remove-Job` , sluit u de sessie of sluit Power shell, het taak exemplaar en de resultaten ervan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="00b40-170">If you delete the job with `Remove-Job`, close the session or close PowerShell, the job instance and its results are deleted.</span></span>

## <a name="scheduled-job-doesnt-run"></a><span data-ttu-id="00b40-171">De geplande taak wordt niet uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="00b40-171">Scheduled job doesn't run</span></span>

<span data-ttu-id="00b40-172">Geplande taken worden niet automatisch uitgevoerd als de taak wordt geactiveerd of de geplande taak is uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="00b40-172">Scheduled jobs don't run automatically if the job triggers or the scheduled job are disabled.</span></span>

<span data-ttu-id="00b40-173">Gebruik de `Get-ScheduledJob` cmdlet om de geplande taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="00b40-173">Use the `Get-ScheduledJob` cmdlet to get the scheduled job.</span></span> <span data-ttu-id="00b40-174">Controleer of de waarde van de eigenschap **enabled** van de geplande taak **waar** is.</span><span class="sxs-lookup"><span data-stu-id="00b40-174">Verify that the value of the **Enabled** property of the scheduled job is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

<span data-ttu-id="00b40-175">Gebruik de `Get-JobTrigger` cmdlet om de taak triggers van de geplande taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="00b40-175">Use the `Get-JobTrigger` cmdlet to get the job triggers of the scheduled job.</span></span>
<span data-ttu-id="00b40-176">Controleer of de waarde van de eigenschap **enabled** van de taak trigger **True** is.</span><span class="sxs-lookup"><span data-stu-id="00b40-176">Verify that the value of the **Enabled** property of the job trigger is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a><span data-ttu-id="00b40-177">Geplande taken worden niet automatisch uitgevoerd als de taak triggers ongeldig zijn</span><span class="sxs-lookup"><span data-stu-id="00b40-177">Scheduled jobs don't run automatically if job triggers are invalid</span></span>

<span data-ttu-id="00b40-178">Een taak trigger kan bijvoorbeeld een datum in het verleden of een datum die niet plaatsvindt, opgeven, zoals de vijfde maandag van de maand.</span><span class="sxs-lookup"><span data-stu-id="00b40-178">For example, a job trigger might specify a date in the past or a date that does not occur, such as the 5th Monday of the month.</span></span>

<span data-ttu-id="00b40-179">Geplande taken worden niet automatisch uitgevoerd als er niet aan de voor waarden van de taak trigger of aan de taak opties wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="00b40-179">Scheduled jobs do not run automatically if the conditions of the job trigger or the job options are not satisfied.</span></span>

<span data-ttu-id="00b40-180">Bijvoorbeeld een geplande taak die alleen wordt uitgevoerd wanneer een bepaalde gebruiker zich aanmeldt bij de computer, wordt niet uitgevoerd als de gebruiker zich niet aanmeldt of alleen op afstand verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="00b40-180">For example, a scheduled job that runs only when a particular user logs on to the computer will not run if that user does not log on or only connects remotely.</span></span>

<span data-ttu-id="00b40-181">Bekijk de opties van de geplande taak en zorg ervoor dat ze zijn voldaan.</span><span class="sxs-lookup"><span data-stu-id="00b40-181">Examine the options of the scheduled job and make sure that they are satisfied.</span></span>
<span data-ttu-id="00b40-182">Bijvoorbeeld een geplande taak waarvoor de computer inactief moet zijn of een netwerk verbinding vereist, of een lange **IdleDuration** heeft of een korte **IdleTimeout** kan nooit worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="00b40-182">For example, a scheduled job that requires that the computer be idle or requires a network connection, or has a long **IdleDuration** or a brief **IdleTimeout** might never run.</span></span>

<span data-ttu-id="00b40-183">Gebruik de `Get-ScheduledJobOption` cmdlet om de taak opties en de bijbehorende waarden te controleren.</span><span class="sxs-lookup"><span data-stu-id="00b40-183">Use the `Get-ScheduledJobOption` cmdlet to examine the job options and their values.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="00b40-184">Zie [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)voor beschrijvingen van de opties voor geplande taken.</span><span class="sxs-lookup"><span data-stu-id="00b40-184">For descriptions of the scheduled job options, see [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

### <a name="the-scheduled-job-instance-might-have-failed"></a><span data-ttu-id="00b40-185">De geplande taak kan zijn mislukt</span><span class="sxs-lookup"><span data-stu-id="00b40-185">The scheduled job instance might have failed</span></span>

<span data-ttu-id="00b40-186">Als een geplande taak mislukt, Power shell rapporteert deze onmiddellijk door een fout bericht te genereren.</span><span class="sxs-lookup"><span data-stu-id="00b40-186">If a scheduled job command fails, PowerShell reports it immediately by generating an error message.</span></span> <span data-ttu-id="00b40-187">Als de taak echter mislukt wanneer taak planner probeert deze uit te voeren, is de fout niet beschikbaar voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="00b40-187">However, if the job fails when Task Scheduler tries to run it, the error is not available to PowerShell.</span></span>

<span data-ttu-id="00b40-188">Gebruik de volgende methoden om taak fouten te detecteren en te corrigeren:</span><span class="sxs-lookup"><span data-stu-id="00b40-188">Use the following methods to detect and correct job failures:</span></span>

<span data-ttu-id="00b40-189">Controleer het gebeurtenis logboek van de taak planner op fouten.</span><span class="sxs-lookup"><span data-stu-id="00b40-189">Check the Task Scheduler event log for errors.</span></span> <span data-ttu-id="00b40-190">Als u het logboek wilt controleren, gebruikt u Logboeken of een Power shell-opdracht zoals de volgende:</span><span class="sxs-lookup"><span data-stu-id="00b40-190">To check the log, use Event Viewer or a PowerShell command such as the following:</span></span>

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

<span data-ttu-id="00b40-191">Controleer de taak record in taak planner.</span><span class="sxs-lookup"><span data-stu-id="00b40-191">Check the job record in Task Scheduler.</span></span> <span data-ttu-id="00b40-192">Geplande power shell-taken worden opgeslagen in de volgende geplande map voor de taak:</span><span class="sxs-lookup"><span data-stu-id="00b40-192">PowerShell scheduled jobs are stored in the following Task Scheduled folder:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a><span data-ttu-id="00b40-193">De geplande taak wordt mogelijk niet uitgevoerd vanwege onvoldoende machtigingen</span><span class="sxs-lookup"><span data-stu-id="00b40-193">The scheduled job might not run because of insufficient permission</span></span>

<span data-ttu-id="00b40-194">Geplande taken worden uitgevoerd met de machtigingen van de gebruiker die de taak heeft gemaakt of de machtigingen van de gebruiker die is opgegeven door de para meter **Credential** in de `Register-ScheduledJob` or- `Set-ScheduledJob` opdracht.</span><span class="sxs-lookup"><span data-stu-id="00b40-194">Scheduled jobs run with the permissions of the user who created the job or the permissions of the user who is specified by the **Credential** parameter in the `Register-ScheduledJob` or `Set-ScheduledJob` command.</span></span>

<span data-ttu-id="00b40-195">Als die gebruiker geen machtiging heeft om de opdrachten of scripts uit te voeren, mislukt de taak.</span><span class="sxs-lookup"><span data-stu-id="00b40-195">If that user does not have permission to run the commands or scripts, the job fails.</span></span>

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a><span data-ttu-id="00b40-196">Kan de geplande taak niet ophalen of de geplande taak is beschadigd</span><span class="sxs-lookup"><span data-stu-id="00b40-196">Can't get scheduled job or scheduled job is corrupted</span></span>

<span data-ttu-id="00b40-197">In zeldzame gevallen kunnen geplande taken beschadigd raken of interne tegen strijdigheden bevatten die niet kunnen worden opgelost.</span><span class="sxs-lookup"><span data-stu-id="00b40-197">On rare occasions, scheduled jobs can become corrupted or contain internal contradictions that cannot be resolved.</span></span> <span data-ttu-id="00b40-198">Dit gebeurt meestal wanneer de XML-bestanden voor de geplande taak hand matig worden bewerkt, wat resulteert in ongeldige XML.</span><span class="sxs-lookup"><span data-stu-id="00b40-198">Typically, this happens when the XML files for the scheduled job are manually edited, resulting in invalid XML.</span></span>

<span data-ttu-id="00b40-199">Wanneer een geplande taak is beschadigd, probeert Power shell de geplande taak, de uitvoerings geschiedenis en de resultaten van de schijf te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="00b40-199">When a scheduled job is corrupted, PowerShell attempts to delete the scheduled job, its execution history, and its results from disk.</span></span>

<span data-ttu-id="00b40-200">Als het niet mogelijk is om de geplande taak te verwijderen, ontvangt u een fout bericht over een beschadigde taak telkens wanneer u de `Get-ScheduledJob` cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="00b40-200">If it cannot remove the scheduled job, you will get a corrupted job error message each time you run the `Get-ScheduledJob` cmdlet.</span></span>

<span data-ttu-id="00b40-201">Als u een beschadigde geplande taak wilt verwijderen, gebruikt u een van de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="00b40-201">To remove a corrupted scheduled job, use either one of the following methods:</span></span>

<span data-ttu-id="00b40-202">Verwijder de `<ScheduledJobName>` map voor de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="00b40-202">Delete the `<ScheduledJobName>` directory for the scheduled job.</span></span> <span data-ttu-id="00b40-203">Verwijder de **ScheduledJob** -map niet.</span><span class="sxs-lookup"><span data-stu-id="00b40-203">Don't delete the **ScheduledJob** directory.</span></span>

<span data-ttu-id="00b40-204">De locatie van de map:</span><span class="sxs-lookup"><span data-stu-id="00b40-204">The directory's location:</span></span>

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

<span data-ttu-id="00b40-205">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="00b40-205">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

<span data-ttu-id="00b40-206">Taak planner gebruiken om de geplande taak te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="00b40-206">Use Task Scheduler to delete the scheduled job.</span></span> <span data-ttu-id="00b40-207">Geplande power shell-taken worden weer gegeven in het volgende pad van de taak planner:</span><span class="sxs-lookup"><span data-stu-id="00b40-207">PowerShell scheduled tasks appear in the following Task Scheduler path:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a><span data-ttu-id="00b40-208">Taak-cmdlets kunnen geplande taken niet consistent vinden</span><span class="sxs-lookup"><span data-stu-id="00b40-208">Job cmdlets can't consistently find scheduled jobs</span></span>

<span data-ttu-id="00b40-209">Wanneer de **PSScheduledJob** -module zich niet in de huidige sessie bevindt, kunnen de taak-cmdlets geen geplande taken ophalen, starten of de resultaten ophalen.</span><span class="sxs-lookup"><span data-stu-id="00b40-209">When the **PSScheduledJob** module isn't in the current session, the job cmdlets cannot get scheduled jobs, start them, or get their results.</span></span>

<span data-ttu-id="00b40-210">Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of voert u een cmdlet in de module, zoals de cmdlet, uit of haalt u deze op `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="00b40-210">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or run or get any cmdlet in the module, such as the `Get-ScheduledJob` cmdlet.</span></span>
<span data-ttu-id="00b40-211">Vanaf Power Shell 3,0 worden modules automatisch geïmporteerd wanneer u een cmdlet in de module ophaalt of gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00b40-211">Beginning in PowerShell 3.0, modules are imported automatically when you get or use any cmdlet in the module.</span></span>

<span data-ttu-id="00b40-212">Wanneer de **PSScheduledJob** -module zich niet in de huidige sessie bevindt, is de volgende opdracht volgorde mogelijk.</span><span class="sxs-lookup"><span data-stu-id="00b40-212">When the **PSScheduledJob** module isn't in the current session, the following command sequence is possible.</span></span>

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

<span data-ttu-id="00b40-213">Dit probleem treedt op omdat de `Get-ScheduledJob` opdracht de **PSScheduledJob** -module automatisch importeert en vervolgens de opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="00b40-213">This behavior occurs because the `Get-ScheduledJob` command automatically imports the **PSScheduledJob** module, and then runs the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="00b40-214">Zie ook</span><span class="sxs-lookup"><span data-stu-id="00b40-214">See also</span></span>

[<span data-ttu-id="00b40-215">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="00b40-215">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="00b40-216">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="00b40-216">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="00b40-217">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="00b40-217">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

<span data-ttu-id="00b40-218">[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets</span><span class="sxs-lookup"><span data-stu-id="00b40-218">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="00b40-219">Taak planner</span><span class="sxs-lookup"><span data-stu-id="00b40-219">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
