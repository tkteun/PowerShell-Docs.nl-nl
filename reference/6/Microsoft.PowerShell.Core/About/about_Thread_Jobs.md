---
description: Bevat informatie over Power shell-thread taken. Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 4951ac2c14c0685fbf2ead16bc52c64096231260
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2020
ms.locfileid: "93253078"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="e13b0-105">Over thread-taken</span><span class="sxs-lookup"><span data-stu-id="e13b0-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="e13b0-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="e13b0-106">Short description</span></span>

<span data-ttu-id="e13b0-107">Bevat informatie over Power shell-thread taken.</span><span class="sxs-lookup"><span data-stu-id="e13b0-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="e13b0-108">Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.</span><span class="sxs-lookup"><span data-stu-id="e13b0-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="e13b0-109">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="e13b0-109">Long description</span></span>

<span data-ttu-id="e13b0-110">In dit artikel wordt uitgelegd hoe u thread taken uitvoert in Power shell op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e13b0-110">This article explains how to run thread jobs in PowerShell on a local computer.</span></span>
<span data-ttu-id="e13b0-111">Zie [about_Jobs](about_Jobs.md)voor meer informatie over het uitvoeren van achtergrond taken op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e13b0-111">For information about running background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span>

<span data-ttu-id="e13b0-112">Start een thread-taak met behulp van de- `Start-ThreadJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e13b0-112">Start a thread job by using the `Start-ThreadJob` cmdlet.</span></span> <span data-ttu-id="e13b0-113">Deze cmdlet is beschikbaar in de **ThreadJob** -module die wordt geleverd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="e13b0-113">This cmdlet is available in the **ThreadJob** module that ships with PowerShell.</span></span>
<span data-ttu-id="e13b0-114">`Start-ThreadJob` retourneert een enkel taak object waarmee de uitgevoerde opdracht of het script wordt ingekapseld en kan worden gebruikt met alle Power shell-taken voor het bewerken van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e13b0-114">`Start-ThreadJob` returns a single job object that encapsulates the running command or script, and can be used with all PowerShell job manipulating cmdlets.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="e13b0-115">De taak-cmdlets</span><span class="sxs-lookup"><span data-stu-id="e13b0-115">The job cmdlets</span></span>

|<span data-ttu-id="e13b0-116">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e13b0-116">Cmdlet</span></span>           |<span data-ttu-id="e13b0-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e13b0-117">Description</span></span>                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|<span data-ttu-id="e13b0-118">Hiermee wordt een thread taak op een lokale computer gestart.</span><span class="sxs-lookup"><span data-stu-id="e13b0-118">Starts a thread job on a local computer.</span></span>               |
|`Get-Job`        |<span data-ttu-id="e13b0-119">Hiermee worden de taken opgehaald die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="e13b0-119">Gets the jobs that were started in the current session.</span></span>|
|`Receive-Job`    |<span data-ttu-id="e13b0-120">Hiermee worden de resultaten van taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e13b0-120">Gets the results of jobs.</span></span>                              |
|`Stop-Job`       |<span data-ttu-id="e13b0-121">Hiermee stopt u een actieve taak.</span><span class="sxs-lookup"><span data-stu-id="e13b0-121">Stops a running job.</span></span>                                   |
|`Wait-Job`       |<span data-ttu-id="e13b0-122">Onderdrukt de opdracht prompt totdat een of alle taken zijn</span><span class="sxs-lookup"><span data-stu-id="e13b0-122">Suppresses the command prompt until one or all jobs are</span></span>|
|                 |<span data-ttu-id="e13b0-123">aangevuld.</span><span class="sxs-lookup"><span data-stu-id="e13b0-123">complete.</span></span>                                              |
|`Remove-Job`     |<span data-ttu-id="e13b0-124">Hiermee verwijdert u een taak.</span><span class="sxs-lookup"><span data-stu-id="e13b0-124">Deletes a job.</span></span>                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a><span data-ttu-id="e13b0-125">Een thread-taak op de lokale computer starten</span><span class="sxs-lookup"><span data-stu-id="e13b0-125">How to start a thread job on the local computer</span></span>

<span data-ttu-id="e13b0-126">Als u een thread-taak op de lokale computer wilt starten, gebruikt u de `Start-ThreadJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e13b0-126">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet.</span></span>

<span data-ttu-id="e13b0-127">Als u een `Start-ThreadJob` opdracht wilt schrijven, plaatst u de opdracht of het script waarmee de taak wordt uitgevoerd in accolades ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="e13b0-127">To write a `Start-ThreadJob` command, enclose the command or script the job runs in curly braces (`{ }`).</span></span>

<span data-ttu-id="e13b0-128">Met de volgende opdracht wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e13b0-128">The following command starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="e13b0-129">`Start-ThreadJob`Met de opdracht wordt een `ThreadJob` object geretourneerd dat de actieve taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e13b0-129">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="e13b0-130">Het taak object bevat nuttige informatie over de taak, inclusief de huidige uitvoerings status.</span><span class="sxs-lookup"><span data-stu-id="e13b0-130">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="e13b0-131">De resultaten van de taak worden verzameld wanneer de resultaten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e13b0-131">It collects the results of the job as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="e13b0-132">Wachten tot een taak is voltooid en taak resultaten ophalen</span><span class="sxs-lookup"><span data-stu-id="e13b0-132">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="e13b0-133">U kunt Power shell-taak-cmdlets gebruiken, zoals `Wait-Job` en `Receive-Job` wachten tot een taak is voltooid en vervolgens alle resultaten retour neren die zijn gegenereerd door de taak.</span><span class="sxs-lookup"><span data-stu-id="e13b0-133">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="e13b0-134">Met de volgende opdracht wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` , wordt gewacht tot de opdracht is voltooid en worden alle gegevens resultaten weer gegeven die zijn gegenereerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="e13b0-134">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

## <a name="powershell-concurrency-and-jobs"></a><span data-ttu-id="e13b0-135">Gelijktijdigheid en taken voor Power shell</span><span class="sxs-lookup"><span data-stu-id="e13b0-135">PowerShell concurrency and jobs</span></span>

<span data-ttu-id="e13b0-136">Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken.</span><span class="sxs-lookup"><span data-stu-id="e13b0-136">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="e13b0-137">Power shell biedt drie oplossingen op basis van taken voor ondersteuning van gelijktijdigheid.</span><span class="sxs-lookup"><span data-stu-id="e13b0-137">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="e13b0-138">Taak</span><span class="sxs-lookup"><span data-stu-id="e13b0-138">Job</span></span>            |<span data-ttu-id="e13b0-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e13b0-139">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="e13b0-140">Opdracht en script worden uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="e13b0-140">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="e13b0-141">Opdracht en script worden uitgevoerd in een afzonderlijk proces op de lokale</span><span class="sxs-lookup"><span data-stu-id="e13b0-141">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="e13b0-142">machine.</span><span class="sxs-lookup"><span data-stu-id="e13b0-142">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="e13b0-143">Opdracht en script worden uitgevoerd in een afzonderlijke thread binnen hetzelfde</span><span class="sxs-lookup"><span data-stu-id="e13b0-143">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="e13b0-144">verwerken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e13b0-144">process on the local machine.</span></span>                                |

<span data-ttu-id="e13b0-145">Elk type taak heeft voor delen en nadelen.</span><span class="sxs-lookup"><span data-stu-id="e13b0-145">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="e13b0-146">Het uitvoeren van een script op afstand op een afzonderlijke machine of in een afzonderlijk proces heeft een goede isolatie.</span><span class="sxs-lookup"><span data-stu-id="e13b0-146">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="e13b0-147">Fouten zijn niet van invloed op andere actieve taken of de client die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="e13b0-147">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="e13b0-148">Maar de externe laag voegt overhead toe, inclusief object serialisatie.</span><span class="sxs-lookup"><span data-stu-id="e13b0-148">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="e13b0-149">Alle objecten die zijn door gegeven aan en van de externe sessie, moeten worden geserialiseerd en vervolgens worden gedeserialiseerd wanneer deze tussen de client en de doel sessie worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="e13b0-149">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="e13b0-150">De serialisatie-bewerking kan veel reken-en geheugen bronnen gebruiken voor grote complexe gegevens objecten.</span><span class="sxs-lookup"><span data-stu-id="e13b0-150">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

## <a name="powershell-thread-based-jobs"></a><span data-ttu-id="e13b0-151">Taken op basis van Power shell-thread</span><span class="sxs-lookup"><span data-stu-id="e13b0-151">PowerShell thread based jobs</span></span>

<span data-ttu-id="e13b0-152">Thread-gebaseerde taken zijn niet zo krachtig als externe en achtergrond taken, omdat ze in hetzelfde proces worden uitgevoerd op verschillende threads.</span><span class="sxs-lookup"><span data-stu-id="e13b0-152">Thread based jobs are not as robust as Remote and Background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="e13b0-153">Als één taak een kritieke fout heeft waardoor het proces wordt afgebroken, mislukken alle andere taken in het proces ook.</span><span class="sxs-lookup"><span data-stu-id="e13b0-153">If one job has a critical error that crashes the process, then all other jobs in the process will also fail.</span></span>

<span data-ttu-id="e13b0-154">Thread-gebaseerde taken hebben echter veel minder overhead.</span><span class="sxs-lookup"><span data-stu-id="e13b0-154">However, thread-based jobs have much less overhead.</span></span> <span data-ttu-id="e13b0-155">Ze hoeven geen externe laag of serialisatie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e13b0-155">They don't need to use the remoting layer or serialization.</span></span> <span data-ttu-id="e13b0-156">Het resultaat is dat thread-gebaseerde taken veel sneller worden uitgevoerd en veel minder resources gebruiken dan de andere taak typen.</span><span class="sxs-lookup"><span data-stu-id="e13b0-156">The result is that thread-based jobs tend to run much faster and use far less resources than the other job types.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="e13b0-157">Thread-taak prestaties</span><span class="sxs-lookup"><span data-stu-id="e13b0-157">Thread job performance</span></span>

<span data-ttu-id="e13b0-158">Thread taken zijn sneller en lichter gewicht dan andere typen taken.</span><span class="sxs-lookup"><span data-stu-id="e13b0-158">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="e13b0-159">Maar ze hebben nog steeds overhead die erg groot kan zijn in vergelijking met werk dat door de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e13b0-159">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="e13b0-160">Power Shell voert opdrachten en scripts uit in een sessie.</span><span class="sxs-lookup"><span data-stu-id="e13b0-160">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="e13b0-161">Er kan slechts één opdracht of script tegelijk in een sessie worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e13b0-161">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="e13b0-162">Bij het uitvoeren van meerdere taken wordt elke taak in een afzonderlijke sessie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e13b0-162">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="e13b0-163">Elke sessie draagt bij aan de overhead.</span><span class="sxs-lookup"><span data-stu-id="e13b0-163">Each session contributes to the overhead.</span></span>

<span data-ttu-id="e13b0-164">Thread taken bieden de beste prestaties wanneer het werk dat ze uitvoeren, groter is dan de overhead van de sessie die wordt gebruikt om de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e13b0-164">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="e13b0-165">Er zijn twee gevallen voor die voldoen aan deze criteria.</span><span class="sxs-lookup"><span data-stu-id="e13b0-165">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="e13b0-166">Werk is het berekenen van intensieve uitvoering van een script op meerdere thread taken kan profiteren van meerdere processor kernen en sneller worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e13b0-166">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="e13b0-167">Het werk bestaat uit een belang rijke wacht tijd: een script dat wacht op een time-out voor I/O-of externe aanroep resultaten.</span><span class="sxs-lookup"><span data-stu-id="e13b0-167">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="e13b0-168">Parallelle uitvoeringen worden gewoonlijk sneller uitgevoerd dan bij een opeenvolgende uitvoering.</span><span class="sxs-lookup"><span data-stu-id="e13b0-168">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

<span data-ttu-id="e13b0-169">In het eerste voor beeld ziet u een foreach-lus waarmee 1000-thread taken worden gemaakt voor het schrijven van eenvoudige teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="e13b0-169">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="e13b0-170">Als gevolg van de taak overhead duurt het meer dan 33 seconden om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="e13b0-170">Due to job overhead, it takes over 33 seconds to complete.</span></span>

<span data-ttu-id="e13b0-171">In het tweede voor beeld wordt de `ForEach` cmdlet uitgevoerd om dezelfde 1000 bewerkingen uit te voeren en elke teken reeks schrijven wordt sequentieel uitgevoerd zonder taak overhead.</span><span class="sxs-lookup"><span data-stu-id="e13b0-171">The second example runs the `ForEach` cmdlet to do the same 1000 operations and each string write is executed sequentially without any job overhead.</span></span> <span data-ttu-id="e13b0-172">Deze is in een paar 25 milliseconden voltooid.</span><span class="sxs-lookup"><span data-stu-id="e13b0-172">It completes in a mere 25 milliseconds.</span></span>

```powershell
$logNames.count
10

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

<span data-ttu-id="e13b0-173">In het bovenstaande voor beeld worden Maxi maal 5000 vermeldingen verzameld voor 10 afzonderlijke systeem Logboeken.</span><span class="sxs-lookup"><span data-stu-id="e13b0-173">In the above example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="e13b0-174">Omdat het script een aantal logboeken moet lezen, is het zinvol om de bewerkingen parallel uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e13b0-174">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span> <span data-ttu-id="e13b0-175">En de taak wordt twee keer zo snel voltooid als wanneer het script op de juiste wijze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e13b0-175">And the job completes over twice as fast as when the script is run sequentially.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="e13b0-176">Thread-taken en-variabelen</span><span class="sxs-lookup"><span data-stu-id="e13b0-176">Thread jobs and variables</span></span>

<span data-ttu-id="e13b0-177">Variabelen worden op verschillende manieren door gegeven aan thread taken.</span><span class="sxs-lookup"><span data-stu-id="e13b0-177">Variables are passed into thread jobs in various ways.</span></span>

<span data-ttu-id="e13b0-178">`Start-ThreadJob` kan variabelen accepteren die worden verzonden naar de cmdlet, door gegeven aan het script blok via het `$using` sleutel woord of door gegeven via de para meter **argument List** .</span><span class="sxs-lookup"><span data-stu-id="e13b0-178">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="e13b0-179">Omdat thread-taken in hetzelfde proces worden uitgevoerd, moet elk referentie type dat naar de taak wordt door gegeven, zorgvuldig worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="e13b0-179">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="e13b0-180">Als het geen thread-safe object is, mag het nooit worden toegewezen aan en moet de methode en eigenschappen nooit worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e13b0-180">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

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

<span data-ttu-id="e13b0-181">In het bovenstaande voor beeld wordt een thread safe dotNet-object door gegeven `ConcurrentDictionary` aan alle onderliggende taken om proces objecten met unieke namen te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="e13b0-181">The above example passes a thread safe dotNet `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="e13b0-182">Omdat het een thread-safe object is, kan het veilig worden gebruikt terwijl de taken gelijktijdig in het proces worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e13b0-182">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

## <a name="see-also"></a><span data-ttu-id="e13b0-183">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e13b0-183">See also</span></span>

- [<span data-ttu-id="e13b0-184">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="e13b0-184">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="e13b0-185">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="e13b0-185">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="e13b0-186">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="e13b0-186">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="e13b0-187">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e13b0-187">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="e13b0-188">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e13b0-188">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="e13b0-189">Begin taak</span><span class="sxs-lookup"><span data-stu-id="e13b0-189">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="e13b0-190">Get-job</span><span class="sxs-lookup"><span data-stu-id="e13b0-190">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="e13b0-191">Receive-job</span><span class="sxs-lookup"><span data-stu-id="e13b0-191">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="e13b0-192">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="e13b0-192">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="e13b0-193">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="e13b0-193">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="e13b0-194">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="e13b0-194">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
