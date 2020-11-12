---
description: Bevat informatie over Power shell-thread taken. Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: ba6251a195d3efdebd427b3f705386336b069211
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524479"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="23b22-105">Over thread-taken</span><span class="sxs-lookup"><span data-stu-id="23b22-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="23b22-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="23b22-106">Short description</span></span>

<span data-ttu-id="23b22-107">Bevat informatie over Power shell-thread taken.</span><span class="sxs-lookup"><span data-stu-id="23b22-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="23b22-108">Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.</span><span class="sxs-lookup"><span data-stu-id="23b22-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="23b22-109">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="23b22-109">Long description</span></span>

<span data-ttu-id="23b22-110">Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken.</span><span class="sxs-lookup"><span data-stu-id="23b22-110">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="23b22-111">Er zijn drie typen taken die door Power shell worden geboden ter ondersteuning van gelijktijdigheid.</span><span class="sxs-lookup"><span data-stu-id="23b22-111">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="23b22-112">`RemoteJob` -Opdrachten en scripts worden uitgevoerd in een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="23b22-112">`RemoteJob` - Commands and scripts run in a remote session.</span></span> <span data-ttu-id="23b22-113">Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23b22-113">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="23b22-114">`BackgroundJob` -Opdrachten en scripts worden in een afzonderlijk proces op de lokale computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-114">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="23b22-115">Zie [About Jobs](about_Jobs.md) (Taken) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23b22-115">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="23b22-116">`PSTaskJob` of `ThreadJob` -opdrachten en scripts worden uitgevoerd in een afzonderlijke thread binnen hetzelfde proces op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="23b22-116">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span>

<span data-ttu-id="23b22-117">Thread-gebaseerde taken zijn niet zo krachtig als externe en achtergrond taken, omdat ze in hetzelfde proces op verschillende threads worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-117">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="23b22-118">Als één taak een kritieke fout heeft die het proces vastloopt, worden alle andere taken in het proces beëindigd.</span><span class="sxs-lookup"><span data-stu-id="23b22-118">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="23b22-119">Thread-gebaseerde taken vereisen echter minder overhead.</span><span class="sxs-lookup"><span data-stu-id="23b22-119">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="23b22-120">Ze gebruiken geen externe laag of serialisatie.</span><span class="sxs-lookup"><span data-stu-id="23b22-120">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="23b22-121">De resultaat objecten worden geretourneerd als verwijzingen naar live-objecten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="23b22-121">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="23b22-122">Zonder deze overhead worden thread-gebaseerde taken sneller uitgevoerd en worden minder resources gebruikt dan de andere taak typen.</span><span class="sxs-lookup"><span data-stu-id="23b22-122">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23b22-123">Met de bovenliggende sessie die de taak heeft gemaakt, wordt ook de taak status bewaakt en worden de pijplijn gegevens verzameld.</span><span class="sxs-lookup"><span data-stu-id="23b22-123">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="23b22-124">Het onderliggende proces van de taak wordt beëindigd door de bovenliggende bewerking zodra de taak de status voltooid heeft bereikt.</span><span class="sxs-lookup"><span data-stu-id="23b22-124">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="23b22-125">Als de bovenliggende sessie wordt beëindigd, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="23b22-125">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="23b22-126">Er zijn twee manieren om deze situatie te omzeilen:</span><span class="sxs-lookup"><span data-stu-id="23b22-126">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="23b22-127">Gebruiken `Invoke-Command` om taken te maken die worden uitgevoerd in sessies zonder verbinding.</span><span class="sxs-lookup"><span data-stu-id="23b22-127">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="23b22-128">Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23b22-128">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="23b22-129">Gebruiken `Start-Process` om een nieuw proces te maken in plaats van een taak.</span><span class="sxs-lookup"><span data-stu-id="23b22-129">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="23b22-130">Zie [start-process](xref:Microsoft.PowerShell.Management.Start-Process)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="23b22-130">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="how-to-start-and-manage-thread-based-jobs"></a><span data-ttu-id="23b22-131">Thread-gebaseerde taken starten en beheren</span><span class="sxs-lookup"><span data-stu-id="23b22-131">How to start and manage thread-based jobs</span></span>

<span data-ttu-id="23b22-132">Er zijn twee manieren om thread-gebaseerde taken te starten:</span><span class="sxs-lookup"><span data-stu-id="23b22-132">There are two ways to start thread-based jobs:</span></span>

- <span data-ttu-id="23b22-133">`Start-ThreadJob` -uit de **ThreadJob** -module</span><span class="sxs-lookup"><span data-stu-id="23b22-133">`Start-ThreadJob` - from the **ThreadJob** module</span></span>
- <span data-ttu-id="23b22-134">`ForEach-Object -Parallel -AsJob` -de parallelle functie is toegevoegd in Power shell 7,0</span><span class="sxs-lookup"><span data-stu-id="23b22-134">`ForEach-Object -Parallel -AsJob` - the parallel feature was added in PowerShell 7.0</span></span>

<span data-ttu-id="23b22-135">Gebruik dezelfde **taak** -cmdlets die worden beschreven in [about_Jobs](about_Jobs.md) om thread-gebaseerde taken te beheren.</span><span class="sxs-lookup"><span data-stu-id="23b22-135">Use the same **Job** cmdlets described in [about_Jobs](about_Jobs.md) to manage thread-based jobs.</span></span>

### <a name="using-start-threadjob"></a><span data-ttu-id="23b22-136">`Start-ThreadJob` gebruiken</span><span class="sxs-lookup"><span data-stu-id="23b22-136">Using `Start-ThreadJob`</span></span>

<span data-ttu-id="23b22-137">De **ThreadJob** -module wordt eerst geleverd met Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="23b22-137">The **ThreadJob** module first shipped with PowerShell 6.</span></span> <span data-ttu-id="23b22-138">Het kan ook worden geïnstalleerd via de PowerShell Gallery voor Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="23b22-138">It can also be installed from the PowerShell Gallery for Windows PowerShell 5.1.</span></span>

<span data-ttu-id="23b22-139">Als u een thread-taak op de lokale computer wilt starten, gebruikt u de `Start-ThreadJob` cmdlet met een opdracht of een script dat is inge sloten in accolades ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="23b22-139">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet with a command or script enclosed in curly braces (`{ }`).</span></span>

<span data-ttu-id="23b22-140">In het volgende voor beeld wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="23b22-140">The following example starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="23b22-141">`Start-ThreadJob`Met de opdracht wordt een `ThreadJob` object geretourneerd dat de actieve taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="23b22-141">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="23b22-142">Het taak object bevat nuttige informatie over de taak, inclusief de huidige uitvoerings status.</span><span class="sxs-lookup"><span data-stu-id="23b22-142">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="23b22-143">De resultaten van de taak worden verzameld wanneer de resultaten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-143">It collects the results of the job as the results are being generated.</span></span>

### <a name="using-foreach-object--parallel--asjob"></a><span data-ttu-id="23b22-144">`ForEach-Object -Parallel -AsJob` gebruiken</span><span class="sxs-lookup"><span data-stu-id="23b22-144">Using `ForEach-Object -Parallel -AsJob`</span></span>

<span data-ttu-id="23b22-145">Power shell 7,0 een nieuwe para meter is toegevoegd aan de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23b22-145">PowerShell 7.0 added a new parameter set to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="23b22-146">Met de nieuwe para meters kunt u script blokken uitvoeren in parallelle threads als Power shell-taken.</span><span class="sxs-lookup"><span data-stu-id="23b22-146">The new parameters allow you to run script blocks in parallel threads as PowerShell jobs.</span></span>

<span data-ttu-id="23b22-147">U kunt gegevens door sluizen naar `ForEach-Object -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="23b22-147">You can pipe data to `ForEach-Object -Parallel`.</span></span> <span data-ttu-id="23b22-148">De gegevens worden door gegeven aan het script blok dat parallel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-148">The data is passed to the script block that is run in parallel.</span></span> <span data-ttu-id="23b22-149">De `-AsJob` para meter maakt taken objecten voor elk van de parallelle threads.</span><span class="sxs-lookup"><span data-stu-id="23b22-149">The `-AsJob` parameter creates jobs objects for each of the parallel threads.</span></span>

<span data-ttu-id="23b22-150">Met de volgende opdracht wordt een taak gestart die onderliggende taken bevat voor elke invoer waarde die is opgenomen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="23b22-150">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="23b22-151">Elke onderliggende taak voert de `Write-Output` opdracht uit met een gesluisde invoer waarde als het argument.</span><span class="sxs-lookup"><span data-stu-id="23b22-151">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="23b22-152">`ForEach-Object -Parallel`Met de opdracht wordt een `PSTaskJob` object geretourneerd dat onderliggende taken bevat voor elke invoer waarde van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="23b22-152">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="23b22-153">Het taak object bevat nuttige informatie over de uitvoerings status van de onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="23b22-153">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="23b22-154">De resultaten van de onderliggende taken worden verzameld wanneer de resultaten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-154">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="23b22-155">Wachten tot een taak is voltooid en taak resultaten ophalen</span><span class="sxs-lookup"><span data-stu-id="23b22-155">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="23b22-156">U kunt Power shell-taak-cmdlets gebruiken, zoals `Wait-Job` en `Receive-Job` wachten tot een taak is voltooid en vervolgens alle resultaten retour neren die zijn gegenereerd door de taak.</span><span class="sxs-lookup"><span data-stu-id="23b22-156">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="23b22-157">Met de volgende opdracht wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` , wordt gewacht tot de opdracht is voltooid en worden alle gegevens resultaten weer gegeven die zijn gegenereerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="23b22-157">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="23b22-158">Met de volgende opdracht wordt een taak gestart die een `Write-Output` opdracht uitvoert voor elke gepipede invoer, wordt gewacht tot alle onderliggende taken zijn voltooid en worden alle gegevens resultaten geretourneerd die zijn gegenereerd door de onderliggende taken.</span><span class="sxs-lookup"><span data-stu-id="23b22-158">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="23b22-159">`Receive-Job`Met de cmdlet worden de resultaten van de onderliggende taken geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-159">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="23b22-160">Omdat elke onderliggende taak parallel wordt uitgevoerd, wordt de volg orde van de gegenereerde resultaten niet gegarandeerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-160">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="23b22-161">Thread-taak prestaties</span><span class="sxs-lookup"><span data-stu-id="23b22-161">Thread job performance</span></span>

<span data-ttu-id="23b22-162">Thread taken zijn sneller en lichter gewicht dan andere typen taken.</span><span class="sxs-lookup"><span data-stu-id="23b22-162">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="23b22-163">Maar ze hebben nog steeds overhead die erg groot kan zijn in vergelijking met werk dat door de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-163">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="23b22-164">Power Shell voert opdrachten en scripts uit in een sessie.</span><span class="sxs-lookup"><span data-stu-id="23b22-164">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="23b22-165">Er kan slechts één opdracht of script tegelijk in een sessie worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-165">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="23b22-166">Bij het uitvoeren van meerdere taken wordt elke taak in een afzonderlijke sessie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-166">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="23b22-167">Elke sessie draagt bij aan de overhead.</span><span class="sxs-lookup"><span data-stu-id="23b22-167">Each session contributes to the overhead.</span></span>

<span data-ttu-id="23b22-168">Thread taken bieden de beste prestaties wanneer het werk dat ze uitvoeren, groter is dan de overhead van de sessie die wordt gebruikt om de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="23b22-168">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="23b22-169">Er zijn twee gevallen voor die voldoen aan deze criteria.</span><span class="sxs-lookup"><span data-stu-id="23b22-169">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="23b22-170">Werk is het berekenen van intensieve uitvoering van een script op meerdere thread taken kan profiteren van meerdere processor kernen en sneller worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-170">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="23b22-171">Het werk bestaat uit een belang rijke wacht tijd: een script dat wacht op een time-out voor I/O-of externe aanroep resultaten.</span><span class="sxs-lookup"><span data-stu-id="23b22-171">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="23b22-172">Parallelle uitvoeringen worden gewoonlijk sneller uitgevoerd dan bij een opeenvolgende uitvoering.</span><span class="sxs-lookup"><span data-stu-id="23b22-172">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

<span data-ttu-id="23b22-173">In het eerste voor beeld ziet u een foreach-lus waarmee 1000-thread taken worden gemaakt voor het schrijven van eenvoudige teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="23b22-173">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="23b22-174">Als gevolg van de taak overhead duurt het meer dan 36 seconden om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="23b22-174">Due to job overhead, it takes over 36 seconds to complete.</span></span>

<span data-ttu-id="23b22-175">In het tweede voor beeld wordt de `ForEach` cmdlet uitgevoerd om dezelfde 1000 bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="23b22-175">The second example runs the `ForEach` cmdlet to do the same 1000 operations.</span></span>
<span data-ttu-id="23b22-176">Deze tijd `ForEach-Object` wordt opeenvolgend uitgevoerd op één thread, zonder dat er taak overhead nodig is.</span><span class="sxs-lookup"><span data-stu-id="23b22-176">This time, `ForEach-Object` runs sequentially, on a single thread, without any job overhead.</span></span> <span data-ttu-id="23b22-177">Deze is in een paar 7 milliseconden voltooid.</span><span class="sxs-lookup"><span data-stu-id="23b22-177">It completes in a mere 7 milliseconds.</span></span>

<span data-ttu-id="23b22-178">In het volgende voor beeld worden Maxi maal 5000 vermeldingen verzameld voor 10 afzonderlijke systeem Logboeken.</span><span class="sxs-lookup"><span data-stu-id="23b22-178">In the following example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="23b22-179">Omdat het script een aantal logboeken moet lezen, is het zinvol om de bewerkingen parallel uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="23b22-179">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span>

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

<span data-ttu-id="23b22-180">Het script wordt voltooid in de helft van het tijdstip waarop de taken parallel worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-180">The script completes in half the time when the jobs are run in parallel.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="23b22-181">Thread-taken en-variabelen</span><span class="sxs-lookup"><span data-stu-id="23b22-181">Thread jobs and variables</span></span>

<span data-ttu-id="23b22-182">Er zijn meerdere manieren om waarden door te geven aan de thread-gebaseerde taken.</span><span class="sxs-lookup"><span data-stu-id="23b22-182">There are multiple ways to pass values into the thread-based jobs.</span></span>

<span data-ttu-id="23b22-183">`Start-ThreadJob` kan variabelen accepteren die worden verzonden naar de cmdlet, door gegeven aan het script blok via het `$using` sleutel woord of door gegeven via de para meter **argument List** .</span><span class="sxs-lookup"><span data-stu-id="23b22-183">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="23b22-184">`ForEach-Object -Parallel` accepteert pipes in variabelen en variabelen die rechtstreeks aan het script blok worden door gegeven via het `$using` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="23b22-184">`ForEach-Object -Parallel` accepts piped in variables, and variables passed directly to the script block via the `$using` keyword.</span></span>

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="23b22-185">Omdat thread-taken in hetzelfde proces worden uitgevoerd, moet elk referentie type dat naar de taak wordt door gegeven, zorgvuldig worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="23b22-185">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="23b22-186">Als het geen thread-safe object is, mag het nooit worden toegewezen aan en moet de methode en eigenschappen nooit worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="23b22-186">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

<span data-ttu-id="23b22-187">In het volgende voor beeld wordt een thread-safe .NET-object door gegeven `ConcurrentDictionary` aan alle onderliggende taken om unieke benoemde proces objecten te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="23b22-187">The following example passes a thread-safe .NET `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="23b22-188">Omdat het een thread-safe object is, kan het veilig worden gebruikt terwijl de taken gelijktijdig in het proces worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="23b22-188">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

## <a name="see-also"></a><span data-ttu-id="23b22-189">Zie tevens</span><span class="sxs-lookup"><span data-stu-id="23b22-189">See also</span></span>

- [<span data-ttu-id="23b22-190">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="23b22-190">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="23b22-191">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="23b22-191">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="23b22-192">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="23b22-192">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="23b22-193">about_Remote</span><span class="sxs-lookup"><span data-stu-id="23b22-193">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="23b22-194">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="23b22-194">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="23b22-195">Begin taak</span><span class="sxs-lookup"><span data-stu-id="23b22-195">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="23b22-196">Get-job</span><span class="sxs-lookup"><span data-stu-id="23b22-196">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="23b22-197">Receive-job</span><span class="sxs-lookup"><span data-stu-id="23b22-197">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="23b22-198">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="23b22-198">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="23b22-199">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="23b22-199">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="23b22-200">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="23b22-200">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
