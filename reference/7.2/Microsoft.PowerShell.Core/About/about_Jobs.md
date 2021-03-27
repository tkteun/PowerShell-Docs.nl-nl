---
description: Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.
Locale: en-US
ms.date: 03/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 189476d98f92b8d53251b16bd27e45f4a980ab0e
ms.sourcegitcommit: ca5a89977913bad9efec6bcc23a792d113ec0396
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/27/2021
ms.locfileid: "105630963"
---
# <a name="about-jobs"></a><span data-ttu-id="ea8c4-103">Over taken</span><span class="sxs-lookup"><span data-stu-id="ea8c4-103">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="ea8c4-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="ea8c4-104">Short description</span></span>
<span data-ttu-id="ea8c4-105">Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-105">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="ea8c4-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="ea8c4-106">Long description</span></span>

<span data-ttu-id="ea8c4-107">Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-107">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="ea8c4-108">Er zijn drie typen taken die door Power shell worden geboden ter ondersteuning van gelijktijdigheid.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-108">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="ea8c4-109">`RemoteJob` -Opdrachten en scripts worden uitgevoerd op een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-109">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="ea8c4-110">Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-110">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="ea8c4-111">`BackgroundJob` -Opdrachten en scripts worden in een afzonderlijk proces op de lokale computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-111">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="ea8c4-112">`PSTaskJob` of `ThreadJob` -opdrachten en scripts worden uitgevoerd in een afzonderlijke thread binnen hetzelfde proces op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-112">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="ea8c4-113">Zie [about_Thread_Jobs](about_Thread_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-113">For more information, see [about_Thread_Jobs](about_Thread_Jobs.md).</span></span>

<span data-ttu-id="ea8c4-114">Het uitvoeren van scripts op afstand, op een afzonderlijke machine of in een afzonderlijk proces, biedt een uitstekende isolatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-114">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="ea8c4-115">Fouten die optreden in de externe taak hebben geen invloed op andere actieve taken of de bovenliggende sessie die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-115">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="ea8c4-116">De externe laag voegt echter overhead toe, inclusief object serialisatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-116">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="ea8c4-117">Alle objecten worden geserialiseerd en gedeserialiseerd wanneer ze worden door gegeven tussen de bovenliggende sessie en de externe (taak) sessie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-117">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="ea8c4-118">Serialisatie van grote complexe gegevens objecten kan grote hoeveel heden reken-en geheugen bronnen verbruiken en grote hoeveel heden gegevens via het netwerk overzetten.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-118">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="ea8c4-119">Thread-gebaseerde taken zijn niet zo krachtig als externe en achtergrond taken, omdat ze in hetzelfde proces op verschillende threads worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-119">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="ea8c4-120">Als één taak een kritieke fout heeft die het proces vastloopt, worden alle andere taken in het proces beëindigd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-120">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="ea8c4-121">Thread-gebaseerde taken vereisen echter minder overhead.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-121">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="ea8c4-122">Ze gebruiken geen externe laag of serialisatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-122">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="ea8c4-123">De resultaat objecten worden geretourneerd als verwijzingen naar live-objecten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-123">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="ea8c4-124">Zonder deze overhead worden thread-gebaseerde taken sneller uitgevoerd en worden minder resources gebruikt dan de andere taak typen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-124">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea8c4-125">Met de bovenliggende sessie die de taak heeft gemaakt, wordt ook de taak status bewaakt en worden de pijplijn gegevens verzameld.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-125">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="ea8c4-126">Het onderliggende proces van de taak wordt beëindigd door de bovenliggende bewerking zodra de taak de status voltooid heeft bereikt.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-126">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="ea8c4-127">Als de bovenliggende sessie wordt beëindigd, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-127">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="ea8c4-128">Er zijn twee manieren om deze situatie te omzeilen:</span><span class="sxs-lookup"><span data-stu-id="ea8c4-128">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="ea8c4-129">Gebruiken `Invoke-Command` om taken te maken die worden uitgevoerd in sessies zonder verbinding.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-129">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="ea8c4-130">Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-130">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="ea8c4-131">Gebruiken `Start-Process` om een nieuw proces te maken in plaats van een taak.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-131">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="ea8c4-132">Zie [start-process](xref:Microsoft.PowerShell.Management.Start-Process)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-132">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="ea8c4-133">De taak-cmdlets</span><span class="sxs-lookup"><span data-stu-id="ea8c4-133">The job cmdlets</span></span>

|<span data-ttu-id="ea8c4-134">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea8c4-134">Cmdlet</span></span>          |<span data-ttu-id="ea8c4-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ea8c4-135">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="ea8c4-136">Hiermee wordt een achtergrond taak op een lokale computer gestart.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-136">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="ea8c4-137">Hiermee worden de achtergrond taken opgehaald die zijn gestart in de</span><span class="sxs-lookup"><span data-stu-id="ea8c4-137">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="ea8c4-138">huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-138">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="ea8c4-139">Hiermee worden de resultaten van achtergrond taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-139">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="ea8c4-140">Hiermee stopt u een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-140">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="ea8c4-141">Onderdrukt de opdracht prompt totdat een of alle taken zijn</span><span class="sxs-lookup"><span data-stu-id="ea8c4-141">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="ea8c4-142">aangevuld.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-142">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="ea8c4-143">Hiermee verwijdert u een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-143">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="ea8c4-144">Met de para meter **AsJob** maakt u een achtergrond taak op een</span><span class="sxs-lookup"><span data-stu-id="ea8c4-144">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="ea8c4-145">externe computer.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-145">remote computer.</span></span> <span data-ttu-id="ea8c4-146">U kunt gebruiken `Invoke-Command` om uit te voeren</span><span class="sxs-lookup"><span data-stu-id="ea8c4-146">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="ea8c4-147">elke taak opdracht op afstand, inclusief `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="ea8c4-147">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="ea8c4-148">Een taak op de lokale computer starten</span><span class="sxs-lookup"><span data-stu-id="ea8c4-148">How to start a job on the local computer</span></span>

<span data-ttu-id="ea8c4-149">Als u een achtergrond taak op de lokale computer wilt starten, gebruikt u de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-149">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="ea8c4-150">Als u een `Start-Job` opdracht wilt schrijven, moet u de opdracht sluiten die de taak in accolades () wordt uitgevoerd `{}` .</span><span class="sxs-lookup"><span data-stu-id="ea8c4-150">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="ea8c4-151">Gebruik de para meter **script Block** om de opdracht op te geven.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-151">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="ea8c4-152">Met de volgende opdracht wordt een achtergrond taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-152">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="ea8c4-153">Wanneer u een achtergrond taak start, wordt de opdracht prompt onmiddellijk geretourneerd, zelfs als de taak een lange tijd in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-153">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="ea8c4-154">U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-154">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="ea8c4-155">`Start-Job`Met de opdracht wordt een object geretourneerd dat de taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-155">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="ea8c4-156">Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-156">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="ea8c4-157">U kunt het taak object opslaan in een variabele en dit vervolgens gebruiken met de andere **taak** -cmdlets om de achtergrond taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-157">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="ea8c4-158">Met de volgende opdracht wordt een taak object gestart en wordt het resulterende taak object in de `$job` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-158">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="ea8c4-159">Vanaf Power shell 6,0 kunt u de operator background ( `&` ) aan het einde van een pijp lijn gebruiken om een achtergrond taak te starten.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-159">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="ea8c4-160">Zie [achtergrond operator](about_Operators.md#background-operator-)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-160">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="ea8c4-161">Het gebruik van de operator background is functioneel equivalent aan het gebruik `Start-Job` van de cmdlet in het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-161">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="ea8c4-162">Taak objecten ophalen</span><span class="sxs-lookup"><span data-stu-id="ea8c4-162">Getting job objects</span></span>

<span data-ttu-id="ea8c4-163">De `Get-Job` cmdlet retourneert objecten die de achtergrond taken vertegenwoordigen die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-163">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="ea8c4-164">Zonder para meters `Get-Job` retourneert alle taken die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-164">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="ea8c4-165">Het taak object bevat de status van de taak, die aangeeft of de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-165">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="ea8c4-166">Een voltooide taak heeft de status **voltooid** of **mislukt**.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-166">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="ea8c4-167">Een taak kan ook worden **geblokkeerd** of **uitgevoerd**.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-167">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="ea8c4-168">U kunt het taak object opslaan in een variabele en gebruiken om de taak te vertegenwoordigen in een latere opdracht.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-168">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="ea8c4-169">Met de volgende opdracht wordt de taak met ID 1 opgehaald en opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-169">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="ea8c4-170">De resultaten van een taak ophalen</span><span class="sxs-lookup"><span data-stu-id="ea8c4-170">Getting the results of a job</span></span>

<span data-ttu-id="ea8c4-171">Wanneer u een achtergrond taak uitvoert, worden de resultaten niet onmiddellijk weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-171">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="ea8c4-172">Als u de resultaten van een achtergrond taak wilt weer geven, gebruikt u de `Receive-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-172">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="ea8c4-173">In het volgende voor beeld worden de `Receive-Job` resultaten van de taak met behulp van het taak object in de variabele opgehaald met de cmdlet `$job` .</span><span class="sxs-lookup"><span data-stu-id="ea8c4-173">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

<span data-ttu-id="ea8c4-174">U kunt de resultaten van een taak opslaan in een variabele.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-174">You can save the results of a job in a variable.</span></span> <span data-ttu-id="ea8c4-175">Met de volgende opdracht worden de resultaten van de taak in de variabele opgeslagen in `$job` de `$results` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="ea8c4-176">Gedeeltelijke taak resultaten ophalen en bewaren</span><span class="sxs-lookup"><span data-stu-id="ea8c4-176">Getting and keeping partial job results</span></span>

<span data-ttu-id="ea8c4-177">De `Receive-Job` cmdlet haalt de resultaten van een achtergrond taak op.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-177">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="ea8c4-178">Als de taak is voltooid, worden `Receive-Job` alle taak resultaten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-178">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="ea8c4-179">Als de taak nog wordt uitgevoerd, worden `Receive-Job` de resultaten opgehaald die tot nu toe zijn gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-179">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="ea8c4-180">U kunt `Receive-Job` de opdrachten opnieuw uitvoeren om de resterende resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-180">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="ea8c4-181">`Receive-Job`De resultaten worden standaard verwijderd uit de cache waarin de taak resultaten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-181">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="ea8c4-182">Wanneer u het `Receive-Job` opnieuw uitvoert, krijgt u alleen de nieuwe resultaten die na de eerste uitvoering zijn aangekomen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-182">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="ea8c4-183">Met de volgende opdrachten worden de resultaten weer gegeven van `Receive-Job` opdrachten die worden uitgevoerd voordat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-183">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

<span data-ttu-id="ea8c4-184">Gebruik de para meter **Keep** om te voor komen dat `Receive-Job` de geretourneerde taak resultaten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-184">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="ea8c4-185">Met de volgende opdrachten wordt het effect van het gebruik van de para meter **Keep** voor een taak die nog niet is voltooid weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-185">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a><span data-ttu-id="ea8c4-186">Wachten op de resultaten</span><span class="sxs-lookup"><span data-stu-id="ea8c4-186">Waiting for the results</span></span>

<span data-ttu-id="ea8c4-187">Als u een opdracht uitvoert die veel tijd in beslag neemt, kunt u de eigenschappen van het taak object gebruiken om te bepalen wanneer de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-187">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="ea8c4-188">De volgende opdracht gebruikt het `Get-Job` object om alle achtergrond taken in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-188">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="ea8c4-189">De resultaten worden weer gegeven in een tabel.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-189">The results appear in a table.</span></span> <span data-ttu-id="ea8c4-190">De status van de taak wordt weer gegeven in de kolom **status** .</span><span class="sxs-lookup"><span data-stu-id="ea8c4-190">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="ea8c4-191">In dit geval toont de **status** eigenschap dat taak 2 nog steeds wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-191">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="ea8c4-192">Als u de `Receive-Job` cmdlet nu wilt gebruiken om de resultaten van de taak te verkrijgen, zijn de resultaten niet volledig.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-192">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="ea8c4-193">U kunt de `Receive-Job` cmdlet herhaaldelijk gebruiken om alle resultaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-193">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="ea8c4-194">Gebruik de eigenschap **State** om te bepalen wanneer de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-194">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="ea8c4-195">U kunt ook de **wait** -para meter van de `Receive-Job` cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-195">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="ea8c4-196">Wanneer u deze para meter gebruiken, wordt de opdracht prompt niet door de cmdlet geretourneerd totdat de taak is voltooid en alle resultaten beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-196">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="ea8c4-197">U kunt ook de `Wait-Job` cmdlet gebruiken om te wachten op de resultaten van de taak.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-197">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="ea8c4-198">`Wait-Job` Hiermee kunt u wachten op een of meer specifieke taak of voor alle taken.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-198">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="ea8c4-199">De volgende opdracht gebruikt de `Wait-Job` cmdlet om te wachten op een taak met **id**</span><span class="sxs-lookup"><span data-stu-id="ea8c4-199">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="ea8c4-200">Als gevolg hiervan wordt de Power shell-prompt onderdrukt totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-200">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="ea8c4-201">U kunt ook wachten op een vooraf bepaalde periode.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-201">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="ea8c4-202">Met deze opdracht wordt de para meter **time-out** gebruikt om de wacht tijd van 120 seconden te beperken.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-202">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="ea8c4-203">Wanneer de tijd is verlopen, wordt de opdracht prompt weer gegeven, maar wordt de taak nog steeds op de achtergrond uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-203">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="ea8c4-204">Een taak stoppen</span><span class="sxs-lookup"><span data-stu-id="ea8c4-204">Stopping a job</span></span>

<span data-ttu-id="ea8c4-205">Als u een achtergrond taak wilt stoppen, gebruikt u de `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-205">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="ea8c4-206">Met de volgende opdracht wordt een taak gestart om elk item in het logboek voor systeem gebeurtenissen op te halen.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-206">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="ea8c4-207">Het taak object wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-207">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="ea8c4-208">Met de volgende opdracht wordt de taak gestopt.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-208">The following command stops the job.</span></span> <span data-ttu-id="ea8c4-209">Er wordt een pijplijn operator ( `|` ) gebruikt om de taak in de `$job` variabele naar te verzenden `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="ea8c4-209">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="ea8c4-210">Een taak verwijderen</span><span class="sxs-lookup"><span data-stu-id="ea8c4-210">Deleting a job</span></span>

<span data-ttu-id="ea8c4-211">Als u een achtergrond taak wilt verwijderen, gebruikt u de `Remove-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-211">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="ea8c4-212">Met de volgende opdracht wordt de taak verwijderd uit de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-212">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="ea8c4-213">Een mislukte taak onderzoeken</span><span class="sxs-lookup"><span data-stu-id="ea8c4-213">Investigating a failed job</span></span>

<span data-ttu-id="ea8c4-214">Taken kunnen om verschillende redenen mislukken.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-214">Jobs can fail for many reasons.</span></span> <span data-ttu-id="ea8c4-215">het taak object bevat een eigenschap **reason** die informatie bevat over de oorzaak van de fout.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-215">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="ea8c4-216">In het volgende voor beeld wordt een taak gestart zonder de vereiste referenties.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-216">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="ea8c4-217">Controleer de eigenschap **reason** om de fout te vinden waardoor de taak is mislukt.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-217">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="ea8c4-218">In dit geval is de taak mislukt, omdat de externe computer expliciete referenties vereist om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-218">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="ea8c4-219">De eigenschap **reason** bevat het volgende bericht:</span><span class="sxs-lookup"><span data-stu-id="ea8c4-219">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="ea8c4-220">Verbinding maken met de externe server is mislukt met het volgende fout bericht: de toegang is geweigerd.</span><span class="sxs-lookup"><span data-stu-id="ea8c4-220">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="ea8c4-221">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ea8c4-221">See also</span></span>

- [<span data-ttu-id="ea8c4-222">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="ea8c4-222">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="ea8c4-223">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="ea8c4-223">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="ea8c4-224">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="ea8c4-224">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="ea8c4-225">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ea8c4-225">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="ea8c4-226">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="ea8c4-226">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="ea8c4-227">Begin taak</span><span class="sxs-lookup"><span data-stu-id="ea8c4-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="ea8c4-228">Get-job</span><span class="sxs-lookup"><span data-stu-id="ea8c4-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="ea8c4-229">Receive-job</span><span class="sxs-lookup"><span data-stu-id="ea8c4-229">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="ea8c4-230">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="ea8c4-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="ea8c4-231">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="ea8c4-231">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="ea8c4-232">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="ea8c4-232">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="ea8c4-233">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="ea8c4-233">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
