---
description: Hierin wordt beschreven hoe u taken uitvoert op externe computers.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 1a4ae0478ff3da84a872ffda93ddf799d2e0c2d9
ms.sourcegitcommit: f6cc3752463b254f6ba7fc14c1e4532ad33f06bb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2021
ms.locfileid: "107216847"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="5c55b-104">Over externe taken</span><span class="sxs-lookup"><span data-stu-id="5c55b-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="5c55b-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="5c55b-105">Short Description</span></span>
<span data-ttu-id="5c55b-106">Hierin wordt beschreven hoe u taken uitvoert op externe computers.</span><span class="sxs-lookup"><span data-stu-id="5c55b-106">Describes how to run jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="5c55b-107">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="5c55b-107">Detailed Description</span></span>

<span data-ttu-id="5c55b-108">Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken.</span><span class="sxs-lookup"><span data-stu-id="5c55b-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="5c55b-109">Er zijn drie typen taken die door Power shell worden geboden ter ondersteuning van gelijktijdigheid.</span><span class="sxs-lookup"><span data-stu-id="5c55b-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="5c55b-110">`RemoteJob` -Opdrachten en scripts worden uitgevoerd in een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-110">`RemoteJob` - Commands and scripts run in a remote session.</span></span>
- <span data-ttu-id="5c55b-111">`BackgroundJob` -Opdrachten en scripts worden in een afzonderlijk proces op de lokale computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5c55b-111">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="5c55b-112">Zie [About Jobs](about_Jobs.md) (Taken) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-112">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="5c55b-113">`PSTaskJob` of `ThreadJob` -opdrachten en scripts worden uitgevoerd in een afzonderlijke thread binnen hetzelfde proces op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="5c55b-114">Zie [about_Thread_Jobs](/powershell/module/Microsoft.PowerShell.Core/About/about_Thread_Jobs)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-114">For more information, see [about_Thread_Jobs](/powershell/module/Microsoft.PowerShell.Core/About/about_Thread_Jobs).</span></span>

<span data-ttu-id="5c55b-115">Scripts op afstand uitvoeren op een afzonderlijke machine of in een afzonderlijk proces, bieden een uitstekende isolatie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-115">Running scripts remotely, on a separate machine or in a separate process, provide great isolation.</span></span> <span data-ttu-id="5c55b-116">Fouten die optreden in de externe taak hebben geen invloed op andere actieve taken of de bovenliggende sessie die de taak heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="5c55b-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="5c55b-117">De externe laag voegt echter overhead toe, inclusief object serialisatie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="5c55b-118">Alle objecten worden geserialiseerd en gedeserialiseerd wanneer ze worden door gegeven tussen de bovenliggende sessie en de externe (taak) sessie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="5c55b-119">Serialisatie van grote complexe gegevens objecten kan grote hoeveel heden reken-en geheugen bronnen verbruiken en grote hoeveel heden gegevens via het netwerk overzetten.</span><span class="sxs-lookup"><span data-stu-id="5c55b-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5c55b-120">Met de bovenliggende sessie die de taak heeft gemaakt, wordt ook de taak status bewaakt en worden de pijplijn gegevens verzameld.</span><span class="sxs-lookup"><span data-stu-id="5c55b-120">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="5c55b-121">Het onderliggende proces van de taak wordt beëindigd door de bovenliggende bewerking zodra de taak de status voltooid heeft bereikt.</span><span class="sxs-lookup"><span data-stu-id="5c55b-121">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="5c55b-122">Als de bovenliggende sessie wordt beëindigd, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-122">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="5c55b-123">Er zijn twee manieren om deze situatie te omzeilen:</span><span class="sxs-lookup"><span data-stu-id="5c55b-123">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="5c55b-124">Gebruiken `Invoke-Command` om taken te maken die worden uitgevoerd in sessies zonder verbinding.</span><span class="sxs-lookup"><span data-stu-id="5c55b-124">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="5c55b-125">Zie de sectie [ontkoppelde processen](#how-to-run-as-a-detached-process) van dit artikel.</span><span class="sxs-lookup"><span data-stu-id="5c55b-125">See the [detached processes](#how-to-run-as-a-detached-process) section of this article.</span></span>
1. <span data-ttu-id="5c55b-126">Gebruiken `Start-Process` om een nieuw proces te maken in plaats van een taak.</span><span class="sxs-lookup"><span data-stu-id="5c55b-126">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="5c55b-127">Zie [start-process](xref:Microsoft.PowerShell.Management.Start-Process)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-127">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="remote-jobs"></a><span data-ttu-id="5c55b-128">Externe taken</span><span class="sxs-lookup"><span data-stu-id="5c55b-128">Remote Jobs</span></span>

<span data-ttu-id="5c55b-129">U kunt taken uitvoeren op externe computers door drie verschillende methoden te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5c55b-129">You can run jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="5c55b-130">Een interactieve sessie starten op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-130">Start an interactive session on a remote computer.</span></span> <span data-ttu-id="5c55b-131">Start vervolgens een taak in de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-131">Then start a job in the interactive session.</span></span> <span data-ttu-id="5c55b-132">De procedures zijn hetzelfde als het uitvoeren van een lokale taak, hoewel alle acties worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-132">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="5c55b-133">Een taak uitvoeren op een externe computer die de resultaten retourneert naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-133">Run a job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="5c55b-134">Gebruik deze methode als u de resultaten van taken wilt verzamelen en deze wilt onderhouden op een centrale locatie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-134">Use this method when you want to collect the results of jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="5c55b-135">Een taak uitvoeren op een externe computer die de resultaten onderhoudt op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-135">Run a job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="5c55b-136">Gebruik deze methode wanneer de taak gegevens veiliger worden onderhouden op de oorspronkelijke computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-136">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-job-in-an-interactive-session"></a><span data-ttu-id="5c55b-137">Een taak starten in een interactieve sessie</span><span class="sxs-lookup"><span data-stu-id="5c55b-137">Start a job in an interactive session</span></span>

<span data-ttu-id="5c55b-138">U kunt een interactieve sessie starten met een externe computer en vervolgens een taak starten tijdens de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-138">You can start an interactive session with a remote computer and then start a job during the interactive session.</span></span> <span data-ttu-id="5c55b-139">Zie about_Remote voor meer informatie over interactieve sessies en Zie `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5c55b-139">For more information about interactive sessions, see about_Remote, and see `Enter-PSSession`.</span></span>

<span data-ttu-id="5c55b-140">De procedure voor het starten van een taak in een interactieve sessie is bijna identiek aan de procedure voor het starten van een achtergrond taak op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-140">The procedure for starting a job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="5c55b-141">Alle bewerkingen vinden echter plaats op de externe computer, niet op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-141">However, all of the operations occur on the remote computer, not the local computer.</span></span>

1. <span data-ttu-id="5c55b-142">Gebruik de `Enter-PSSession` cmdlet om een interactieve sessie met een externe computer te starten.</span><span class="sxs-lookup"><span data-stu-id="5c55b-142">Use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="5c55b-143">U kunt de para meter ComputerName van gebruiken `Enter-PSSession` om een tijdelijke verbinding voor de interactieve sessie tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-143">You can use the ComputerName parameter of `Enter-PSSession` to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="5c55b-144">U kunt ook de sessie parameter gebruiken om de interactieve sessie uit te voeren in een Power shell-sessie (PSSession).</span><span class="sxs-lookup"><span data-stu-id="5c55b-144">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

   <span data-ttu-id="5c55b-145">Met de volgende opdracht wordt een interactieve sessie op de Server01-computer gestart.</span><span class="sxs-lookup"><span data-stu-id="5c55b-145">The following command starts an interactive session on the Server01 computer.</span></span>

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   <span data-ttu-id="5c55b-146">De opdracht prompt wordt weer gegeven om aan te geven dat u nu verbinding hebt met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-146">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

   ```
   Server01\C:>
   ```

1. <span data-ttu-id="5c55b-147">Als u een externe taak in de sessie wilt starten, gebruikt u de `Start-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5c55b-147">To start a remote job in the session, use the `Start-Job` cmdlet.</span></span> <span data-ttu-id="5c55b-148">Met de volgende opdracht wordt een externe taak uitgevoerd waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de Server01-computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5c55b-148">The following command runs a remote job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="5c55b-149">De `Start-Job` cmdlet retourneert een object dat de taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5c55b-149">The `Start-Job` cmdlet returns an object that represents the job.</span></span>

   <span data-ttu-id="5c55b-150">Met deze opdracht wordt het taak object in de `$job` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-150">This command saves the job object in the `$job` variable.</span></span>

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   <span data-ttu-id="5c55b-151">Terwijl de taak wordt uitgevoerd, kunt u de interactieve sessie gebruiken om andere opdrachten uit te voeren, waaronder andere taken.</span><span class="sxs-lookup"><span data-stu-id="5c55b-151">While the job runs, you can use the interactive session to run other commands, including other jobs.</span></span> <span data-ttu-id="5c55b-152">U moet de interactieve sessie echter laten openen totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="5c55b-152">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="5c55b-153">Als u de sessie beëindigt, wordt de taak onderbroken en gaan de resultaten verloren.</span><span class="sxs-lookup"><span data-stu-id="5c55b-153">If you end the session, the job is interrupted, and the results are lost.</span></span>

1. <span data-ttu-id="5c55b-154">Als u wilt weten of de taak is voltooid, geeft u de waarde van de `$job` variabele weer of gebruikt `Get-Job` u de cmdlet om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-154">To find out if the job is complete, display the value of the `$job` variable, or use the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="5c55b-155">De volgende opdracht gebruikt de `Get-Job` cmdlet om de taak weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5c55b-155">The following command uses the `Get-Job` cmdlet to display the job.</span></span>

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   <span data-ttu-id="5c55b-156">`Get-Job`In de uitvoer ziet u dat de taak wordt uitgevoerd op de ' localhost ' computer omdat de taak is gestart op en wordt uitgevoerd op dezelfde computer (in dit geval Server01).</span><span class="sxs-lookup"><span data-stu-id="5c55b-156">The `Get-Job` output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

1. <span data-ttu-id="5c55b-157">Gebruik de cmdlet om de resultaten van de taak te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="5c55b-157">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="5c55b-158">U kunt de resultaten weer geven in de interactieve sessie of opslaan in een bestand op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-158">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="5c55b-159">Met de volgende opdracht worden de resultaten van de taak in de variabele $job opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5c55b-159">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="5c55b-160">De opdracht maakt gebruik van de omleidings operator ( `>` ) om de resultaten van de taak op te slaan in het PsLog.txt bestand op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-160">The command uses the redirection operator (`>`) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. <span data-ttu-id="5c55b-161">Gebruik de cmdlet om de interactieve sessie te beëindigen `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5c55b-161">To end the interactive session, use the `Exit-PSSession` cmdlet.</span></span> <span data-ttu-id="5c55b-162">De opdracht prompt wordt weer gegeven om aan te geven dat u terug bent in de oorspronkelijke sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-162">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. <span data-ttu-id="5c55b-163">Als u de inhoud van het `PsLog.txt` bestand op de Server01-computer op elk gewenst moment wilt weer geven, start u een andere interactieve sessie of voert u een externe opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="5c55b-163">To view the contents of the `PsLog.txt` file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="5c55b-164">Dit type opdracht wordt het beste uitgevoerd in een PSSession (een permanente verbinding) voor het geval u meerdere opdrachten wilt gebruiken om de gegevens in het bestand te onderzoeken en te beheren `PsLog.txt` .</span><span class="sxs-lookup"><span data-stu-id="5c55b-164">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the `PsLog.txt` file.</span></span> <span data-ttu-id="5c55b-165">Zie [about_PSSessions](about_PSSessions.md)voor meer informatie over PSSessions.</span><span class="sxs-lookup"><span data-stu-id="5c55b-165">For more information about PSSessions, see [about_PSSessions](about_PSSessions.md).</span></span>

   <span data-ttu-id="5c55b-166">De volgende opdrachten gebruiken de `New-PSSession` cmdlet om een **PSSession** te maken die is verbonden met de Server01-computer, en ze gebruiken de `Invoke-Command` cmdlet om een `Get-Content` opdracht uit te voeren in de PSSession om de inhoud van het bestand weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5c55b-166">The following commands use the `New-PSSession` cmdlet to create a **PSSession** that is connected to the Server01 computer, and they use the `Invoke-Command` cmdlet to run a `Get-Content` command in the PSSession to view the contents of the file.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="5c55b-167">Een externe taak starten die de resultaten retourneert naar de lokale computer (AsJob)</span><span class="sxs-lookup"><span data-stu-id="5c55b-167">Start a remote job that returns the results to the local computer (AsJob)</span></span>

<span data-ttu-id="5c55b-168">Als u een taak wilt starten op een externe computer die de opdracht resultaten retourneert naar de lokale computer, gebruikt u de para meter **AsJob** van een cmdlet zoals de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5c55b-168">To start a job on a remote computer that returns the command results to the local computer, use the **AsJob** parameter of a cmdlet such as the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="5c55b-169">Wanneer u de para meter **AsJob** gebruikt, wordt het taak object daad werkelijk gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-169">When you use the **AsJob** parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="5c55b-170">Wanneer de taak is voltooid, worden de resultaten geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-170">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="5c55b-171">U kunt de cmdlets gebruiken die het zelfstandige taak onderdeel (de taak-cmdlets) bevatten om elke taak te beheren die door elke cmdlet wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="5c55b-171">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="5c55b-172">Veel van de cmdlets met **AsJob** -para meters gebruiken geen externe communicatie van Power shell, zodat u ze zelfs kunt gebruiken op computers die niet zijn geconfigureerd voor externe communicatie en die niet voldoen aan de vereisten voor externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-172">Many of the cmdlets that have **AsJob** parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

1. <span data-ttu-id="5c55b-173">De volgende opdracht maakt gebruik van de para meter **AsJob** van `Invoke-Command` om een taak op de Server01-computer te starten.</span><span class="sxs-lookup"><span data-stu-id="5c55b-173">The following command uses the **AsJob** parameter of `Invoke-Command` to start a job on the Server01 computer.</span></span> <span data-ttu-id="5c55b-174">De taak voert een `Get-Eventlog` opdracht uit waarmee de gebeurtenissen in het systeem logboek worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5c55b-174">The job runs a `Get-Eventlog` command that gets the events in the System log.</span></span> <span data-ttu-id="5c55b-175">U kunt de para meter JobName gebruiken om een weergave naam toe te wijzen aan de taak.</span><span class="sxs-lookup"><span data-stu-id="5c55b-175">You can use the JobName parameter to assign a display name to the job.</span></span>

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   <span data-ttu-id="5c55b-176">De resultaten van de opdracht lijken op de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-176">The results of the command resemble the following sample output.</span></span>

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   <span data-ttu-id="5c55b-177">Wanneer de para meter **AsJob** wordt gebruikt, `Invoke-Command` retourneert hetzelfde type taak object dat `Start-Job` retourneert.</span><span class="sxs-lookup"><span data-stu-id="5c55b-177">When the **AsJob** parameter is used, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="5c55b-178">U kunt het taak object opslaan in een variabele, maar u kunt ook een `Get-Job` opdracht gebruiken om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-178">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="5c55b-179">Houd er rekening mee dat de waarde van de eigenschap locatie laat zien dat de taak is uitgevoerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-179">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

1. <span data-ttu-id="5c55b-180">Voor het beheren van een taak die is gestart met behulp van de para meter **AsJob** van de `Invoke-Command` cmdlet, gebruikt u de taak-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5c55b-180">To manage a job started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="5c55b-181">Omdat het taak object dat de externe taak vertegenwoordigt, zich op de lokale computer bevindt, hoeft u geen externe opdrachten uit te voeren om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="5c55b-181">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

   <span data-ttu-id="5c55b-182">Gebruik een opdracht om te bepalen of de taak is voltooid `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="5c55b-182">To determine whether the job is complete, use a `Get-Job` command.</span></span> <span data-ttu-id="5c55b-183">Met de volgende opdracht worden alle taken opgehaald die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="5c55b-183">The following command gets all of the jobs that were started in the current session.</span></span>

   ```powershell
   Get-Job
   ```

   <span data-ttu-id="5c55b-184">Omdat de externe taak is gestart in de huidige sessie, haalt een lokale `Get-Job` opdracht de taak op.</span><span class="sxs-lookup"><span data-stu-id="5c55b-184">Because the remote job was started in the current session, a local `Get-Job` command gets the job.</span></span> <span data-ttu-id="5c55b-185">De eigenschap State van het taak object geeft aan dat de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="5c55b-185">The State property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. <span data-ttu-id="5c55b-186">Gebruik de cmdlet om de resultaten van de taak te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="5c55b-186">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="5c55b-187">Omdat de resultaten van de taak automatisch worden teruggestuurd naar de computer waarop het taak object zich bevindt, kunt u de resultaten ophalen met een lokale `Receive-Job` opdracht.</span><span class="sxs-lookup"><span data-stu-id="5c55b-187">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local `Receive-Job` command.</span></span>

   <span data-ttu-id="5c55b-188">De volgende opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-188">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="5c55b-189">De sessie-ID wordt gebruikt om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="5c55b-189">It uses the session ID to identify the job.</span></span> <span data-ttu-id="5c55b-190">Met deze opdracht worden de taak resultaten opgeslagen in de variabele $results.</span><span class="sxs-lookup"><span data-stu-id="5c55b-190">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="5c55b-191">U kunt de resultaten ook omleiden naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="5c55b-191">You can also redirect the results to a file.</span></span>

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="5c55b-192">Een externe taak starten die de resultaten op de externe computer bewaart</span><span class="sxs-lookup"><span data-stu-id="5c55b-192">Start a remote job that keeps the results on the remote computer</span></span>

<span data-ttu-id="5c55b-193">Als u een taak wilt starten op een externe computer die de opdracht resultaten op de externe computer houdt, gebruikt u de `Invoke-Command` cmdlet om een `Start-Job` opdracht op een externe computer uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5c55b-193">To start a job on a remote computer that keeps the command results on the remote computer, use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="5c55b-194">U kunt deze methode gebruiken om taken uit te voeren op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="5c55b-194">You can use this method to run jobs on multiple computers.</span></span>

<span data-ttu-id="5c55b-195">Wanneer u een `Start-Job` opdracht op afstand uitvoert, wordt het taak object op de externe computer gemaakt en worden de taak resultaten op de externe computer bewaard.</span><span class="sxs-lookup"><span data-stu-id="5c55b-195">When you run a `Start-Job` command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="5c55b-196">Vanuit het perspectief van de taak zijn alle bewerkingen lokaal.</span><span class="sxs-lookup"><span data-stu-id="5c55b-196">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="5c55b-197">U hoeft alleen opdrachten op afstand uit te voeren om een lokale taak op de externe computer te beheren.</span><span class="sxs-lookup"><span data-stu-id="5c55b-197">You are just running commands remotely to manage a local job on the remote computer.</span></span>

1. <span data-ttu-id="5c55b-198">Gebruik de `Invoke-Command` cmdlet om een opdracht uit te voeren `Start-Job` op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-198">Use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span>

   <span data-ttu-id="5c55b-199">Voor deze opdracht is een PSSession (een permanente verbinding) vereist.</span><span class="sxs-lookup"><span data-stu-id="5c55b-199">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="5c55b-200">Als u de para meter ComputerName van gebruikt `Invoke-Command` om een tijdelijke verbinding tot stand te brengen, `Invoke-Command` wordt de opdracht als voltooid beschouwd wanneer het taak object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5c55b-200">If you use the ComputerName parameter of `Invoke-Command` to establish a temporary connection, the `Invoke-Command` command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="5c55b-201">Als gevolg hiervan wordt de tijdelijke verbinding gesloten en wordt de taak geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="5c55b-201">As a result, the temporary connection is closed, and the job is canceled.</span></span>

   <span data-ttu-id="5c55b-202">De volgende opdracht maakt gebruik van de `New-PSSession` cmdlet om een PSSession te maken die is verbonden met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-202">The following command uses the `New-PSSession` cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="5c55b-203">Met de opdracht slaat u de PSSession op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="5c55b-203">The command saves the PSSession in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   <span data-ttu-id="5c55b-204">De volgende opdracht maakt gebruik `Invoke-Command` van de cmdlet om een opdracht uit te voeren `Start-Job` in de PSSession.</span><span class="sxs-lookup"><span data-stu-id="5c55b-204">The next command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the PSSession.</span></span> <span data-ttu-id="5c55b-205">De `Start-Job` opdracht en de `Get-Eventlog` opdracht staan tussen accolades.</span><span class="sxs-lookup"><span data-stu-id="5c55b-205">The `Start-Job` command and the `Get-Eventlog` command are enclosed in braces.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   <span data-ttu-id="5c55b-206">De resultaten zijn vergelijkbaar met de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-206">The results resemble the following sample output.</span></span>

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   <span data-ttu-id="5c55b-207">Wanneer u een `Start-Job` opdracht extern uitvoert, `Invoke-Command` retourneert hetzelfde type taak object dat `Start-Job` retourneert.</span><span class="sxs-lookup"><span data-stu-id="5c55b-207">When you run a `Start-Job` command remotely, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="5c55b-208">U kunt het taak object opslaan in een variabele, maar u kunt ook een `Get-Job` opdracht gebruiken om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-208">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="5c55b-209">Houd er rekening mee dat de waarde van de eigenschap **locatie** aangeeft dat de taak is uitgevoerd op de lokale computer, ook wel ' localhost ' genoemd, hoewel de taak is uitgevoerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-209">Note that the value of the **Location** property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="5c55b-210">Omdat het taak object op de Server01-computer wordt gemaakt en de taak wordt uitgevoerd op dezelfde computer, wordt deze als een lokale achtergrond taak beschouwd.</span><span class="sxs-lookup"><span data-stu-id="5c55b-210">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

1. <span data-ttu-id="5c55b-211">Als u een externe taak wilt beheren, gebruikt u de **taak** -cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5c55b-211">To manage a remote job, use the **Job** cmdlets.</span></span> <span data-ttu-id="5c55b-212">Omdat het taak object zich op de externe computer bevindt, moet u externe opdrachten uitvoeren om de taak resultaten op te halen, te stoppen, te wachten of op te halen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-212">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

   <span data-ttu-id="5c55b-213">Als u wilt zien of de taak is voltooid, gebruikt u een `Invoke-Command` opdracht voor `Get-Job` het uitvoeren van een opdracht in de PSSession die is verbonden met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-213">To see if the job is complete, use an `Invoke-Command` command to run a `Get-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   <span data-ttu-id="5c55b-214">De opdracht retourneert een taak object.</span><span class="sxs-lookup"><span data-stu-id="5c55b-214">The command returns a job object.</span></span> <span data-ttu-id="5c55b-215">De eigenschap **State** van het taak object geeft aan dat de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="5c55b-215">The **State** property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. <span data-ttu-id="5c55b-216">Als u de resultaten van de taak wilt ophalen, gebruikt u de `Invoke-Command` cmdlet om een `Receive-Job` opdracht uit te voeren in de PSSession die is verbonden met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-216">To get the results of the job, use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   <span data-ttu-id="5c55b-217">De volgende opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-217">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="5c55b-218">De sessie-ID wordt gebruikt om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="5c55b-218">It uses the session ID to identify the job.</span></span> <span data-ttu-id="5c55b-219">Met deze opdracht worden de taak resultaten in de `$results` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-219">This command saves the job results in the `$results` variable.</span></span> <span data-ttu-id="5c55b-220">Hierbij wordt de para meter ' Keep ' gebruikt `Receive-Job` om het resultaat in de taak cache op de externe computer te blijven.</span><span class="sxs-lookup"><span data-stu-id="5c55b-220">It uses the Keep parameter of `Receive-Job` to keep the result in the job cache on the remote computer.</span></span>

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   <span data-ttu-id="5c55b-221">U kunt de resultaten ook omleiden naar een bestand op de lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-221">You can also redirect the results to a file on the local or remote computer.</span></span>
   <span data-ttu-id="5c55b-222">De volgende opdracht maakt gebruik van een omleidings operator om de resultaten op te slaan in een bestand op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-222">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a><span data-ttu-id="5c55b-223">Uitvoeren als een ontkoppeld proces</span><span class="sxs-lookup"><span data-stu-id="5c55b-223">How to run as a detached process</span></span>

<span data-ttu-id="5c55b-224">Zoals eerder vermeld, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen, wanneer de bovenliggende sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="5c55b-224">As previously mentioned, when the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span> <span data-ttu-id="5c55b-225">U kunt externe toegang op de lokale computer gebruiken om taken uit te voeren die niet zijn gekoppeld aan de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-225">You can use remoting on the local machine to run jobs that are not attached to the current PowerShell session.</span></span>

<span data-ttu-id="5c55b-226">Maak een nieuwe Power shell-sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5c55b-226">Create a new PowerShell session on the local machine.</span></span> <span data-ttu-id="5c55b-227">Het gebruik `Invoke-Command` om een taak in deze sessie te starten.</span><span class="sxs-lookup"><span data-stu-id="5c55b-227">The use `Invoke-Command` to start a job in this session.</span></span> <span data-ttu-id="5c55b-228">`Invoke-Command` Hiermee kunt u de verbinding van een externe sessie verbreken en de bovenliggende sessie beëindigen.</span><span class="sxs-lookup"><span data-stu-id="5c55b-228">`Invoke-Command` allows you to disconnect a remote session and terminate the parent session.</span></span> <span data-ttu-id="5c55b-229">U kunt later een nieuwe Power shell-sessie starten en verbinding maken met de eerder verbroken sessie om de bewaking van de taak te hervatten.</span><span class="sxs-lookup"><span data-stu-id="5c55b-229">Later, you can start a new PowerShell session and connect to the previously disconnected session to resume monitoring the job.</span></span> <span data-ttu-id="5c55b-230">Alle gegevens die naar de oorspronkelijke Power shell-sessie zijn geretourneerd, gaan echter verloren wanneer de sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="5c55b-230">However, any data that was returned to the original PowerShell session is lost when that session is terminated.</span></span> <span data-ttu-id="5c55b-231">Alleen nieuwe gegevens objecten die zijn gegenereerd nadat de verbinding is verbroken, worden geretourneerd wanneer de verbinding is hersteld.</span><span class="sxs-lookup"><span data-stu-id="5c55b-231">Only new data objects generated after the disconnect are returned when re-connected.</span></span>

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

<span data-ttu-id="5c55b-232">Voor dit voor beeld zijn de taken nog steeds gekoppeld aan een bovenliggende Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5c55b-232">For this example, the jobs are still attached to a parent PowerShell session.</span></span>
<span data-ttu-id="5c55b-233">De bovenliggende sessie is echter niet de oorspronkelijke Power shell-sessie waar `Invoke-Command` werd uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5c55b-233">However, the parent session is not the original PowerShell session where `Invoke-Command` was run.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c55b-234">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5c55b-234">See also</span></span>

- [<span data-ttu-id="5c55b-235">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="5c55b-235">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="5c55b-236">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="5c55b-236">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="5c55b-237">about_Remote</span><span class="sxs-lookup"><span data-stu-id="5c55b-237">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="5c55b-238">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="5c55b-238">about_Remote_Variables</span></span>](about_Remote_Variables.md)
- [<span data-ttu-id="5c55b-239">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="5c55b-239">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="5c55b-240">Begin taak</span><span class="sxs-lookup"><span data-stu-id="5c55b-240">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="5c55b-241">Get-job</span><span class="sxs-lookup"><span data-stu-id="5c55b-241">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="5c55b-242">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="5c55b-242">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="5c55b-243">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="5c55b-243">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="5c55b-244">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="5c55b-244">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="5c55b-245">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="5c55b-245">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="5c55b-246">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="5c55b-246">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="5c55b-247">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="5c55b-247">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
