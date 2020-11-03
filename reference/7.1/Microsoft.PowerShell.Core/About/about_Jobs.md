---
description: Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: b28eb480e3f994696738d6053ea7e2622a743ce5
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2020
ms.locfileid: "93253074"
---
# <a name="about-jobs"></a><span data-ttu-id="05c10-104">Over taken</span><span class="sxs-lookup"><span data-stu-id="05c10-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="05c10-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="05c10-105">Short description</span></span>
<span data-ttu-id="05c10-106">Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="05c10-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="05c10-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="05c10-107">Long description</span></span>

<span data-ttu-id="05c10-108">Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken.</span><span class="sxs-lookup"><span data-stu-id="05c10-108">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="05c10-109">Power shell biedt drie oplossingen op basis van taken voor ondersteuning van gelijktijdigheid.</span><span class="sxs-lookup"><span data-stu-id="05c10-109">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="05c10-110">Taak</span><span class="sxs-lookup"><span data-stu-id="05c10-110">Job</span></span>            |<span data-ttu-id="05c10-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="05c10-111">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="05c10-112">Opdracht en script worden uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="05c10-112">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="05c10-113">Opdracht en script worden uitgevoerd in een afzonderlijk proces op de lokale</span><span class="sxs-lookup"><span data-stu-id="05c10-113">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="05c10-114">machine.</span><span class="sxs-lookup"><span data-stu-id="05c10-114">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="05c10-115">Opdracht en script worden uitgevoerd in een afzonderlijke thread binnen hetzelfde</span><span class="sxs-lookup"><span data-stu-id="05c10-115">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="05c10-116">verwerken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="05c10-116">process on the local machine.</span></span>                                |

<span data-ttu-id="05c10-117">Elk type taak heeft voor delen en nadelen.</span><span class="sxs-lookup"><span data-stu-id="05c10-117">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="05c10-118">Het uitvoeren van een script op afstand op een afzonderlijke machine of in een afzonderlijk proces heeft een goede isolatie.</span><span class="sxs-lookup"><span data-stu-id="05c10-118">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="05c10-119">Fouten zijn niet van invloed op andere actieve taken of de client die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="05c10-119">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="05c10-120">Maar de externe laag voegt overhead toe, inclusief object serialisatie.</span><span class="sxs-lookup"><span data-stu-id="05c10-120">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="05c10-121">Alle objecten die zijn door gegeven aan en van de externe sessie, moeten worden geserialiseerd en vervolgens worden gedeserialiseerd wanneer deze tussen de client en de doel sessie worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="05c10-121">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="05c10-122">De serialisatie-bewerking kan veel reken-en geheugen bronnen gebruiken voor grote complexe gegevens objecten.</span><span class="sxs-lookup"><span data-stu-id="05c10-122">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

<span data-ttu-id="05c10-123">In dit onderwerp wordt uitgelegd hoe u achtergrond taken uitvoert in Power shell op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="05c10-123">This topic explains how to run background jobs in PowerShell on a local computer.</span></span> <span data-ttu-id="05c10-124">Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie over het uitvoeren van achtergrond taken op externe computers.</span><span class="sxs-lookup"><span data-stu-id="05c10-124">For information about running background jobs on remote computers, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span> <span data-ttu-id="05c10-125">Zie [about_Thread_Jobs](about_Thread_Jobs.md)voor meer informatie over thread taken.</span><span class="sxs-lookup"><span data-stu-id="05c10-125">For more information about thread jobs, see [about_Thread_Jobs](about_Thread_Jobs.md).</span></span>

<span data-ttu-id="05c10-126">Wanneer u een achtergrond taak start, wordt de opdracht prompt onmiddellijk geretourneerd, zelfs als de taak een lange tijd in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="05c10-126">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="05c10-127">U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="05c10-127">You can continue to work in the session without interruption while the job runs.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="05c10-128">De taak-cmdlets</span><span class="sxs-lookup"><span data-stu-id="05c10-128">The job cmdlets</span></span>

|<span data-ttu-id="05c10-129">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="05c10-129">Cmdlet</span></span>          |<span data-ttu-id="05c10-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="05c10-130">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="05c10-131">Hiermee wordt een achtergrond taak op een lokale computer gestart.</span><span class="sxs-lookup"><span data-stu-id="05c10-131">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="05c10-132">Hiermee worden de achtergrond taken opgehaald die zijn gestart in de</span><span class="sxs-lookup"><span data-stu-id="05c10-132">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="05c10-133">huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="05c10-133">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="05c10-134">Hiermee worden de resultaten van achtergrond taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05c10-134">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="05c10-135">Hiermee stopt u een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="05c10-135">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="05c10-136">Onderdrukt de opdracht prompt totdat een of alle taken zijn</span><span class="sxs-lookup"><span data-stu-id="05c10-136">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="05c10-137">aangevuld.</span><span class="sxs-lookup"><span data-stu-id="05c10-137">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="05c10-138">Hiermee verwijdert u een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="05c10-138">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="05c10-139">Met de para meter **AsJob** maakt u een achtergrond taak op een</span><span class="sxs-lookup"><span data-stu-id="05c10-139">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="05c10-140">externe computer.</span><span class="sxs-lookup"><span data-stu-id="05c10-140">remote computer.</span></span> <span data-ttu-id="05c10-141">U kunt gebruiken `Invoke-Command` om uit te voeren</span><span class="sxs-lookup"><span data-stu-id="05c10-141">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="05c10-142">elke taak opdracht op afstand, inclusief `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="05c10-142">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="05c10-143">Een taak op de lokale computer starten</span><span class="sxs-lookup"><span data-stu-id="05c10-143">How to start a job on the local computer</span></span>

<span data-ttu-id="05c10-144">Als u een achtergrond taak op de lokale computer wilt starten, gebruikt u de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05c10-144">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="05c10-145">Als u een `Start-Job` opdracht wilt schrijven, moet u de opdracht sluiten die de taak in accolades () wordt uitgevoerd `{}` .</span><span class="sxs-lookup"><span data-stu-id="05c10-145">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="05c10-146">Gebruik de para meter **script Block** om de opdracht op te geven.</span><span class="sxs-lookup"><span data-stu-id="05c10-146">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="05c10-147">Met de volgende opdracht wordt een achtergrond taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="05c10-147">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="05c10-148">`Start-Job`Met de opdracht wordt een object geretourneerd dat de taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="05c10-148">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="05c10-149">Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.</span><span class="sxs-lookup"><span data-stu-id="05c10-149">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="05c10-150">Sla het taak object op in een variabele en gebruik het vervolgens met de andere taak-cmdlets om de achtergrond taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="05c10-150">Save the job object in a variable, and then use it with the other Job cmdlets to manage the background job.</span></span> <span data-ttu-id="05c10-151">Met de volgende opdracht wordt een taak object gestart en wordt het resulterende taak object in de `$job` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="05c10-151">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="05c10-152">Vanaf Power shell 6,0 kunt u een amersand ( `&` ) aan het einde van een pijp lijn gebruiken om een achtergrond taak te starten.</span><span class="sxs-lookup"><span data-stu-id="05c10-152">Beginning in PowerShell 6.0, you can use an amersand (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="05c10-153">De volgende opdracht is functioneel gelijk aan de bovenstaande opdracht.</span><span class="sxs-lookup"><span data-stu-id="05c10-153">The following command is functionally equivalent to the command above.</span></span>

```powershell
$job = Get-Process &
```

<span data-ttu-id="05c10-154">Het en-teken ( `&` ) wordt de operator achtergrond genoemd.</span><span class="sxs-lookup"><span data-stu-id="05c10-154">The ampersand (`&`) is called the background operator.</span></span> <span data-ttu-id="05c10-155">Zie [achtergrond operator](about_Operators.md#background-operator-)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="05c10-155">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="05c10-156">U kunt ook de- `Get-Job` cmdlet gebruiken om objecten op te halen die de taken vertegenwoordigen die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="05c10-156">You can also use the `Get-Job` cmdlet to get objects that represent the jobs started in the current session.</span></span> <span data-ttu-id="05c10-157">`Get-Job` retourneert hetzelfde taak object dat `Start-Job` retourneert.</span><span class="sxs-lookup"><span data-stu-id="05c10-157">`Get-Job` returns the same job object that `Start-Job` returns.</span></span>

## <a name="getting-job-objects"></a><span data-ttu-id="05c10-158">Taak objecten ophalen</span><span class="sxs-lookup"><span data-stu-id="05c10-158">Getting job objects</span></span>

<span data-ttu-id="05c10-159">Als u object wilt ophalen dat de achtergrond taken vertegenwoordigt die in de huidige sessie zijn gestart, gebruikt u de `Get-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05c10-159">To get object that represent the background jobs that were started in the current session, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="05c10-160">Zonder para meters `Get-Job` retourneert alle taken die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="05c10-160">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

<span data-ttu-id="05c10-161">Met de volgende opdracht worden bijvoorbeeld de taken in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05c10-161">For example, the following command gets the jobs in the current session.</span></span>

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

<span data-ttu-id="05c10-162">U kunt het taak object ook opslaan in een variabele en gebruiken om de taak te vertegenwoordigen in een latere opdracht.</span><span class="sxs-lookup"><span data-stu-id="05c10-162">You can also save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="05c10-163">Met de volgende opdracht wordt de taak met ID 1 opgehaald en opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="05c10-163">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

<span data-ttu-id="05c10-164">Het taak object bevat de status van de taak, die aangeeft of de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="05c10-164">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="05c10-165">Een voltooide taak heeft de status **voltooid** of **mislukt**.</span><span class="sxs-lookup"><span data-stu-id="05c10-165">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="05c10-166">Een taak kan ook worden **geblokkeerd** of **uitgevoerd**.</span><span class="sxs-lookup"><span data-stu-id="05c10-166">A job might also be **blocked** or **running**.</span></span>

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="05c10-167">De resultaten van een taak ophalen</span><span class="sxs-lookup"><span data-stu-id="05c10-167">Getting the results of a job</span></span>

<span data-ttu-id="05c10-168">Wanneer u een achtergrond taak uitvoert, worden de resultaten niet onmiddellijk weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="05c10-168">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="05c10-169">In plaats daarvan `Start-Job` retourneert de cmdlet een taak object dat de taak vertegenwoordigt, maar bevat het geen resultaten.</span><span class="sxs-lookup"><span data-stu-id="05c10-169">Instead, the `Start-Job` cmdlet returns a job object that represents the job, but it does not contain the results.</span></span> <span data-ttu-id="05c10-170">Als u de resultaten van een achtergrond taak wilt weer geven, gebruikt u de `Receive-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05c10-170">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="05c10-171">De volgende opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="05c10-171">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="05c10-172">Er wordt een taak object gebruikt dat in de variabele is opgeslagen `$job` om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="05c10-172">It uses a job object saved in the `$job` variable to identify the job.</span></span>

```powershell
Receive-Job -Job $job
```

<span data-ttu-id="05c10-173">`Receive-Job`Met de cmdlet worden de resultaten van de taak geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="05c10-173">The `Receive-Job` cmdlet returns the results of the job.</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

<span data-ttu-id="05c10-174">U kunt de resultaten van een taak ook opslaan in een variabele.</span><span class="sxs-lookup"><span data-stu-id="05c10-174">You can also save the results of a job in a variable.</span></span> <span data-ttu-id="05c10-175">Met de volgende opdracht worden de resultaten van de taak in de variabele opgeslagen in `$job` de `$results` variabele.</span><span class="sxs-lookup"><span data-stu-id="05c10-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

<span data-ttu-id="05c10-176">En u kunt de resultaten van de taak opslaan in een bestand met behulp van de omleidings operator ( `>` ) of de `Out-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05c10-176">And, you can save the results of the job in a file by using the redirection operator (`>`) or the `Out-File` cmdlet.</span></span> <span data-ttu-id="05c10-177">De volgende opdracht maakt gebruik van de omleidings operator om de resultaten van de taak in de `$job` variabele in het bestand op te slaan `Results.txt` .</span><span class="sxs-lookup"><span data-stu-id="05c10-177">The following command uses the redirection operator to save the results of the job in the `$job` variable in the `Results.txt` file.</span></span>

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="05c10-178">Gedeeltelijke taak resultaten ophalen en bewaren</span><span class="sxs-lookup"><span data-stu-id="05c10-178">Getting and keeping partial job results</span></span>

<span data-ttu-id="05c10-179">De `Receive-Job` cmdlet haalt de resultaten van een achtergrond taak op.</span><span class="sxs-lookup"><span data-stu-id="05c10-179">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="05c10-180">Als de taak is voltooid, worden `Receive-Job` alle taak resultaten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05c10-180">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="05c10-181">Als de taak nog wordt uitgevoerd, worden `Receive-Job` de resultaten opgehaald die tot nu toe zijn gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="05c10-181">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="05c10-182">U kunt `Receive-Job` de opdrachten opnieuw uitvoeren om de resterende resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="05c10-182">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="05c10-183">Wanneer `Receive-Job` de resultaten worden geretourneerd, worden deze resultaten standaard verwijderd uit de cache waarin de taak resultaten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="05c10-183">When `Receive-Job` returns results, by default, it deletes those results from the cache where job results are stored.</span></span> <span data-ttu-id="05c10-184">Als u een andere `Receive-Job` opdracht uitvoert, worden alleen de resultaten weer geven die nog niet zijn ontvangen.</span><span class="sxs-lookup"><span data-stu-id="05c10-184">If you run another `Receive-Job` command, you get only the results that are not yet received.</span></span>

<span data-ttu-id="05c10-185">Met de volgende opdrachten worden de resultaten weer gegeven van `Receive-Job` opdrachten die worden uitgevoerd voordat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="05c10-185">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="05c10-186">Als u wilt voor komen `Receive-Job` dat de taak resultaten worden verwijderd die zijn geretourneerd, gebruikt u de para meter **Keep** .</span><span class="sxs-lookup"><span data-stu-id="05c10-186">To prevent `Receive-Job` from deleting the job results that it has returned, use the **Keep** parameter.</span></span> <span data-ttu-id="05c10-187">Als gevolg hiervan worden `Receive-Job` alle resultaten geretourneerd die tot dat moment zijn gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="05c10-187">As a result, `Receive-Job` returns all of the results that have been generated until that time.</span></span>

<span data-ttu-id="05c10-188">Met de volgende opdrachten wordt het effect van het gebruik van de para meter **Keep** voor een taak die nog niet is voltooid weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="05c10-188">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

## <a name="waiting-for-the-results"></a><span data-ttu-id="05c10-189">Wachten op de resultaten</span><span class="sxs-lookup"><span data-stu-id="05c10-189">Waiting for the results</span></span>

<span data-ttu-id="05c10-190">Als u een opdracht uitvoert die veel tijd in beslag neemt, kunt u de eigenschappen van het taak object gebruiken om te bepalen wanneer de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="05c10-190">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="05c10-191">De volgende opdracht gebruikt het `Get-Job` object om alle achtergrond taken in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="05c10-191">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="05c10-192">De resultaten worden weer gegeven in een tabel.</span><span class="sxs-lookup"><span data-stu-id="05c10-192">The results appear in a table.</span></span> <span data-ttu-id="05c10-193">De status van de taak wordt weer gegeven in de kolom **status** .</span><span class="sxs-lookup"><span data-stu-id="05c10-193">The status of the job appears in the **State** column.</span></span>

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="05c10-194">In dit geval toont de status eigenschap dat taak 2 nog steeds wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="05c10-194">In this case, the State property reveals that Job 2 is still running.</span></span> <span data-ttu-id="05c10-195">Als u de `Receive-Job` cmdlet nu wilt gebruiken om de resultaten van de taak te verkrijgen, zijn de resultaten niet volledig.</span><span class="sxs-lookup"><span data-stu-id="05c10-195">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="05c10-196">U kunt de `Receive-Job` cmdlet herhaaldelijk gebruiken om alle resultaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="05c10-196">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="05c10-197">Elke keer dat u deze gebruikt, ontvangt u standaard alleen de resultaten die nog niet zijn ontvangen, maar u kunt de para meter **behouden** van de `Receive-Job` cmdlet gebruiken om de resultaten te bewaren, zelfs als deze al zijn ontvangen.</span><span class="sxs-lookup"><span data-stu-id="05c10-197">By default, each time you use it, you get only the results that were not already received, but you can use the **Keep** parameter of the `Receive-Job` cmdlet to retain the results, even though they were already received.</span></span>

<span data-ttu-id="05c10-198">U kunt de gedeeltelijke resultaten naar een bestand schrijven en vervolgens nieuwere resultaten toevoegen wanneer ze binnenkomen of u kunt wachten en de status van de taak later controleren.</span><span class="sxs-lookup"><span data-stu-id="05c10-198">You can write the partial results to a file and then append newer results as they arrive or you can wait and check the state of the job later.</span></span>

<span data-ttu-id="05c10-199">U kunt de **wait** -para meter van de `Receive-Job` cmdlet gebruiken. de opdracht prompt wordt niet geretourneerd totdat de taak is voltooid en alle resultaten beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="05c10-199">You can use the **Wait** parameter of the `Receive-Job` cmdlet, which does not return the command prompt until the job is complete and all results are available.</span></span>

<span data-ttu-id="05c10-200">U kunt ook de `Wait-Job` cmdlet gebruiken om te wachten op de resultaten van de taak.</span><span class="sxs-lookup"><span data-stu-id="05c10-200">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="05c10-201">`Wait-Job` Hiermee kunt u wachten op een bepaalde taak, voor alle taken of voor het volt ooien van de taken.</span><span class="sxs-lookup"><span data-stu-id="05c10-201">`Wait-Job` lets you wait for a particular job, for all jobs, or for any of the jobs to be completed.</span></span>

<span data-ttu-id="05c10-202">De volgende opdracht gebruikt de `Wait-Job` cmdlet om te wachten op een taak met **id**</span><span class="sxs-lookup"><span data-stu-id="05c10-202">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="05c10-203">Als gevolg hiervan wordt de Power shell-prompt onderdrukt totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="05c10-203">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="05c10-204">U kunt ook wachten op een vooraf bepaalde periode.</span><span class="sxs-lookup"><span data-stu-id="05c10-204">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="05c10-205">Met deze opdracht wordt de para meter **time-out** gebruikt om de wacht tijd van 120 seconden te beperken.</span><span class="sxs-lookup"><span data-stu-id="05c10-205">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="05c10-206">Wanneer de tijd is verlopen, wordt de opdracht prompt weer gegeven, maar wordt de taak nog steeds op de achtergrond uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="05c10-206">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="05c10-207">Een taak stoppen</span><span class="sxs-lookup"><span data-stu-id="05c10-207">Stopping a job</span></span>

<span data-ttu-id="05c10-208">Als u een achtergrond taak wilt stoppen, gebruikt u de `Stop-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05c10-208">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="05c10-209">Met de volgende opdracht wordt een taak gestart om elk item in het logboek voor systeem gebeurtenissen op te halen.</span><span class="sxs-lookup"><span data-stu-id="05c10-209">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="05c10-210">Het taak object wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="05c10-210">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="05c10-211">Met de volgende opdracht wordt de taak gestopt.</span><span class="sxs-lookup"><span data-stu-id="05c10-211">The following command stops the job.</span></span> <span data-ttu-id="05c10-212">Er wordt een pijplijn operator ( `|` ) gebruikt om de taak in de `$job` variabele naar te verzenden `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="05c10-212">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="05c10-213">Een taak verwijderen</span><span class="sxs-lookup"><span data-stu-id="05c10-213">Deleting a job</span></span>

<span data-ttu-id="05c10-214">Als u een achtergrond taak wilt verwijderen, gebruikt u de `Remove-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05c10-214">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="05c10-215">Met de volgende opdracht wordt de taak verwijderd uit de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="05c10-215">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="05c10-216">Een mislukte taak onderzoeken</span><span class="sxs-lookup"><span data-stu-id="05c10-216">Investigating a failed job</span></span>

<span data-ttu-id="05c10-217">Als u wilt weten waarom een taak is mislukt, gebruikt u de eigenschap **reason** van het object taak.</span><span class="sxs-lookup"><span data-stu-id="05c10-217">To find out why a job failed, use the **Reason** property of the job object.</span></span>

<span data-ttu-id="05c10-218">Met de volgende opdracht wordt een taak gestart zonder de vereiste referenties.</span><span class="sxs-lookup"><span data-stu-id="05c10-218">The following command starts a job without the required credentials.</span></span> <span data-ttu-id="05c10-219">Het taak object wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="05c10-219">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="05c10-220">De volgende opdracht gebruikt de eigenschap Reason om de fout te vinden waardoor de taak is mislukt.</span><span class="sxs-lookup"><span data-stu-id="05c10-220">The following command uses the Reason property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="05c10-221">In dit geval is de taak mislukt, omdat de externe computer expliciete referenties vereist om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="05c10-221">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="05c10-222">De waarde van de eigenschap **reason** is:</span><span class="sxs-lookup"><span data-stu-id="05c10-222">The value of the **Reason** property is:</span></span>

<span data-ttu-id="05c10-223">Verbinding maken met de externe server is mislukt met het volgende fout bericht: de toegang is geweigerd.</span><span class="sxs-lookup"><span data-stu-id="05c10-223">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="05c10-224">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05c10-224">See also</span></span>

- [<span data-ttu-id="05c10-225">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="05c10-225">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="05c10-226">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="05c10-226">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="05c10-227">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="05c10-227">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="05c10-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="05c10-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="05c10-229">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="05c10-229">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="05c10-230">Begin taak</span><span class="sxs-lookup"><span data-stu-id="05c10-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="05c10-231">Get-job</span><span class="sxs-lookup"><span data-stu-id="05c10-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="05c10-232">Receive-job</span><span class="sxs-lookup"><span data-stu-id="05c10-232">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="05c10-233">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="05c10-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="05c10-234">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="05c10-234">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="05c10-235">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="05c10-235">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="05c10-236">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="05c10-236">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
