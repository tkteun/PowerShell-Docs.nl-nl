---
description: Hierin wordt beschreven hoe u achtergrond taken uitvoert op externe computers.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: fb2270ea5c0acdcf2c506e687787d22c73e2cb2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252651"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="93ab8-104">Over externe taken</span><span class="sxs-lookup"><span data-stu-id="93ab8-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="93ab8-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="93ab8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="93ab8-106">Hierin wordt beschreven hoe u achtergrond taken uitvoert op externe computers.</span><span class="sxs-lookup"><span data-stu-id="93ab8-106">Describes how to run background jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="93ab8-107">GEDETAILLEERDE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="93ab8-107">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="93ab8-108">Een achtergrond taak is een opdracht die asynchroon wordt uitgevoerd zonder interactie met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="93ab8-108">A background job is a command that runs asynchronously without interacting with the current session.</span></span> <span data-ttu-id="93ab8-109">De opdracht prompt wordt onmiddellijk geretourneerd en u kunt de sessie blijven gebruiken terwijl de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="93ab8-109">The command prompt returns immediately, and you can continue to use the session while the job runs.</span></span>

<span data-ttu-id="93ab8-110">Achtergrond taken worden standaard uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-110">By default, background jobs run on the local computer.</span></span> <span data-ttu-id="93ab8-111">U kunt echter verschillende procedures gebruiken om achtergrond taken uit te voeren op externe computers.</span><span class="sxs-lookup"><span data-stu-id="93ab8-111">However, you can use several different procedures to run background jobs on remote computers.</span></span>

<span data-ttu-id="93ab8-112">In dit onderwerp wordt uitgelegd hoe u een achtergrond taak kunt uitvoeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-112">This topic explains how to run a background job on a remote computer.</span></span> <span data-ttu-id="93ab8-113">Zie [about_Jobs](about_Jobs.md)voor meer informatie over het uitvoeren van achtergrond taken op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-113">For information about how to run background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span> <span data-ttu-id="93ab8-114">Zie [about_Job_Details](about_Job_Details.md)voor meer informatie over achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="93ab8-114">For more information about background jobs, see [about_Job_Details](about_Job_Details.md).</span></span>

## <a name="remote-background-jobs"></a><span data-ttu-id="93ab8-115">EXTERNE ACHTERGROND TAKEN</span><span class="sxs-lookup"><span data-stu-id="93ab8-115">REMOTE BACKGROUND JOBS</span></span>

<span data-ttu-id="93ab8-116">U kunt achtergrond taken uitvoeren op externe computers door drie verschillende methoden te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="93ab8-116">You can run background jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="93ab8-117">Start een interactieve sessie met een externe computer en start een taak in de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="93ab8-117">Start an interactive session with a remote computer, and start a job in the interactive session.</span></span> <span data-ttu-id="93ab8-118">De procedures zijn hetzelfde als het uitvoeren van een lokale taak, hoewel alle acties worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-118">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="93ab8-119">Een achtergrond taak uitvoeren op een externe computer die de resultaten retourneert naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-119">Run a background job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="93ab8-120">Gebruik deze methode als u de resultaten van achtergrond taken wilt verzamelen en deze wilt onderhouden op een centrale locatie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-120">Use this method when you want to collect the results of background jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="93ab8-121">Een achtergrond taak uitvoeren op een externe computer die de resultaten onderhoudt op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-121">Run a background job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="93ab8-122">Gebruik deze methode wanneer de taak gegevens veiliger worden onderhouden op de oorspronkelijke computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-122">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-background-job-in-an-interactive-session"></a><span data-ttu-id="93ab8-123">EEN ACHTERGROND TAAK STARTEN IN EEN INTERACTIEVE SESSIE</span><span class="sxs-lookup"><span data-stu-id="93ab8-123">START A BACKGROUND JOB IN AN INTERACTIVE SESSION</span></span>

<span data-ttu-id="93ab8-124">U kunt een interactieve sessie starten met een externe computer en vervolgens een achtergrond taak starten tijdens de interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="93ab8-124">You can start an interactive session with a remote computer and then start a background job during the interactive session.</span></span> <span data-ttu-id="93ab8-125">Zie about_Remote voor meer informatie over interactieve sessies en zie Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="93ab8-125">For more information about interactive sessions, see about_Remote, and see Enter-PSSession.</span></span>

<span data-ttu-id="93ab8-126">De procedure voor het starten van een achtergrond taak in een interactieve sessie is bijna identiek aan de procedure voor het starten van een achtergrond taak op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-126">The procedure for starting a background job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="93ab8-127">Alle bewerkingen vinden echter plaats op de externe computer, niet op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-127">However, all of the operations occur on the remote computer, not the local computer.</span></span>

#### <a name="step-1-enter-pssession"></a><span data-ttu-id="93ab8-128">STAP 1: ENTER-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="93ab8-128">STEP 1: ENTER-PSSESSION</span></span>

<span data-ttu-id="93ab8-129">Gebruik de cmdlet Enter-PSSession om een interactieve sessie met een externe computer te starten.</span><span class="sxs-lookup"><span data-stu-id="93ab8-129">Use the Enter-PSSession cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="93ab8-130">U kunt de para meter ComputerName van Enter-PSSession gebruiken om een tijdelijke verbinding voor de interactieve sessie tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-130">You can use the ComputerName parameter of Enter-PSSession to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="93ab8-131">U kunt ook de sessie parameter gebruiken om de interactieve sessie uit te voeren in een Power shell-sessie (PSSession).</span><span class="sxs-lookup"><span data-stu-id="93ab8-131">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

<span data-ttu-id="93ab8-132">Met de volgende opdracht wordt een interactieve sessie op de Server01-computer gestart.</span><span class="sxs-lookup"><span data-stu-id="93ab8-132">The following command starts an interactive session on the Server01 computer.</span></span>

```powershell
C:\PS> Enter-PSSession -computername Server01
```

<span data-ttu-id="93ab8-133">De opdracht prompt wordt weer gegeven om aan te geven dat u nu verbinding hebt met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-133">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

```
Server01\C:>
```

#### <a name="step-2-start-job"></a><span data-ttu-id="93ab8-134">STAP 2: START-JOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-134">STEP 2: START-JOB</span></span>

<span data-ttu-id="93ab8-135">Als u een achtergrond taak in de sessie wilt starten, gebruikt u de cmdlet Start-Job.</span><span class="sxs-lookup"><span data-stu-id="93ab8-135">To start a background job in the session, use the Start-Job cmdlet.</span></span>

<span data-ttu-id="93ab8-136">Met de volgende opdracht wordt een achtergrond taak uitgevoerd waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de Server01-computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="93ab8-136">The following command runs a background job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="93ab8-137">De cmdlet Start-Job retourneert een object dat de taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="93ab8-137">The Start-Job cmdlet returns an object that represents the job.</span></span>

<span data-ttu-id="93ab8-138">Met deze opdracht wordt het taak object in de \$ taak variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-138">This command saves the job object in the \$job variable.</span></span>

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

<span data-ttu-id="93ab8-139">Terwijl de taak wordt uitgevoerd, kunt u de interactieve sessie gebruiken om andere opdrachten uit te voeren, waaronder andere achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="93ab8-139">While the job runs, you can use the interactive session to run other commands, including other background jobs.</span></span> <span data-ttu-id="93ab8-140">U moet de interactieve sessie echter laten openen totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="93ab8-140">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="93ab8-141">Als u de sessie beëindigt, wordt de taak onderbroken en gaan de resultaten verloren.</span><span class="sxs-lookup"><span data-stu-id="93ab8-141">If you end the session, the job is interrupted, and the results are lost.</span></span>

#### <a name="step-3-get-job"></a><span data-ttu-id="93ab8-142">STAP 3: GET-JOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-142">STEP 3: GET-JOB</span></span>

<span data-ttu-id="93ab8-143">Als u wilt weten of de taak is voltooid, geeft u de waarde van de \$ taak variabele weer of gebruikt u de cmdlet Get-Job om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-143">To find out if the job is complete, display the value of the \$job variable, or use the Get-Job cmdlet to get the job.</span></span> <span data-ttu-id="93ab8-144">De volgende opdracht maakt gebruik van de cmdlet Get-Job om de taak weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93ab8-144">The following command uses the Get-Job cmdlet to display the job.</span></span>

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

<span data-ttu-id="93ab8-145">In de Get-Job uitvoer ziet u dat de taak wordt uitgevoerd op de computer ' localhost ' omdat de taak is gestart op en wordt uitgevoerd op dezelfde computer (in dit geval Server01).</span><span class="sxs-lookup"><span data-stu-id="93ab8-145">The Get-Job output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

#### <a name="step-4-receive-job"></a><span data-ttu-id="93ab8-146">STAP 4: RECEIVE-JOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-146">STEP 4: RECEIVE-JOB</span></span>

<span data-ttu-id="93ab8-147">Gebruik de cmdlet Receive-Job om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-147">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="93ab8-148">U kunt de resultaten weer geven in de interactieve sessie of opslaan in een bestand op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-148">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="93ab8-149">Met de volgende opdracht worden de resultaten van de taak in de variabele $job opgehaald.</span><span class="sxs-lookup"><span data-stu-id="93ab8-149">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="93ab8-150">De opdracht maakt gebruik van de omleidings operator (>) om de resultaten van de taak op te slaan in het PsLog.txt bestand op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-150">The command uses the redirection operator (>) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a><span data-ttu-id="93ab8-151">STAP 5: AFSLUITEN-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="93ab8-151">STEP 5: EXIT-PSSESSION</span></span>

<span data-ttu-id="93ab8-152">Gebruik de cmdlet Exit-PSSession om de interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-152">To end the interactive session, use the Exit-PSSession cmdlet.</span></span> <span data-ttu-id="93ab8-153">De opdracht prompt wordt weer gegeven om aan te geven dat u terug bent in de oorspronkelijke sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-153">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a><span data-ttu-id="93ab8-154">STAP 6: INVOKE-OPDRACHT: GET-CONTENT</span><span class="sxs-lookup"><span data-stu-id="93ab8-154">STEP 6: INVOKE-COMMAND: GET-CONTENT</span></span>

<span data-ttu-id="93ab8-155">Als u de inhoud van het PsLog.txt-bestand op de Server01-computer op elk gewenst moment wilt weer geven, start u een andere interactieve sessie of voert u een externe opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="93ab8-155">To view the contents of the PsLog.txt file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="93ab8-156">Dit type opdracht wordt het beste uitgevoerd in een PSSession (een permanente verbinding) voor het geval u meerdere opdrachten wilt gebruiken om de gegevens in het PsLog.txt-bestand te onderzoeken en te beheren.</span><span class="sxs-lookup"><span data-stu-id="93ab8-156">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the PsLog.txt file.</span></span> <span data-ttu-id="93ab8-157">Zie about_PSSessions voor meer informatie over PSSessions.</span><span class="sxs-lookup"><span data-stu-id="93ab8-157">For more information about PSSessions, see about_PSSessions.</span></span>

<span data-ttu-id="93ab8-158">De volgende opdrachten gebruiken de New-PSSession cmdlet om een PSSession te maken die is verbonden met de Server01-computer, en ze gebruiken de Invoke-Command cmdlet om een Get-Content opdracht uit te voeren in de PSSession om de inhoud van het bestand weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93ab8-158">The following commands use the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer, and they use the Invoke-Command cmdlet to run a Get-Content command in the PSSession to view the contents of the file.</span></span>

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="93ab8-159">Een externe taak starten die de resultaten retourneert naar de lokale COMPUTER \( ASJOB\)</span><span class="sxs-lookup"><span data-stu-id="93ab8-159">START A REMOTE JOB THAT RETURNS THE RESULTS TO THE LOCAL COMPUTER \(ASJOB\)</span></span>

<span data-ttu-id="93ab8-160">Als u een achtergrond taak wilt starten op een externe computer die de opdracht resultaten retourneert naar de lokale computer, gebruikt u de para meter AsJob van een cmdlet zoals de cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="93ab8-160">To start a background job on a remote computer that returns the command results to the local computer, use the AsJob parameter of a cmdlet such as the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="93ab8-161">Wanneer u de para meter AsJob gebruikt, wordt het taak object daad werkelijk gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-161">When you use the AsJob parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="93ab8-162">Wanneer de taak is voltooid, worden de resultaten geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-162">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="93ab8-163">U kunt de cmdlets gebruiken die het zelfstandige taak onderdeel (de taak-cmdlets) bevatten om elke taak te beheren die door elke cmdlet wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="93ab8-163">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="93ab8-164">Veel van de cmdlets met AsJob-para meters gebruiken geen externe communicatie van Power shell, zodat u ze zelfs kunt gebruiken op computers die niet zijn geconfigureerd voor externe communicatie en die niet voldoen aan de vereisten voor externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="93ab8-164">Many of the cmdlets that have AsJob parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

#### <a name="step-1-invoke-command--asjob"></a><span data-ttu-id="93ab8-165">STAP 1: INVOKE-COMMAND-ASJOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-165">STEP 1: INVOKE-COMMAND -ASJOB</span></span>

<span data-ttu-id="93ab8-166">De volgende opdracht maakt gebruik van de AsJob-para meter van Invoke-Command om een achtergrond taak op de Server01-computer te starten.</span><span class="sxs-lookup"><span data-stu-id="93ab8-166">The following command uses the AsJob parameter of Invoke-Command to start a background job on the Server01 computer.</span></span> <span data-ttu-id="93ab8-167">De taak voert een Get-Eventlog opdracht uit waarmee de gebeurtenissen in het systeem logboek worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="93ab8-167">The job runs a Get-Eventlog command that gets the events in the System log.</span></span> <span data-ttu-id="93ab8-168">U kunt de para meter JobName gebruiken om een weergave naam toe te wijzen aan de taak.</span><span class="sxs-lookup"><span data-stu-id="93ab8-168">You can use the JobName parameter to assign a display name to the job.</span></span>

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

<span data-ttu-id="93ab8-169">De resultaten van de opdracht lijken op de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-169">The results of the command resemble the following sample output.</span></span>

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

<span data-ttu-id="93ab8-170">Wanneer de para meter AsJob wordt gebruikt, retourneert Invoke-Command hetzelfde type taak object dat Start-Job retourneert.</span><span class="sxs-lookup"><span data-stu-id="93ab8-170">When the AsJob parameter is used, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="93ab8-171">U kunt het taak object opslaan in een variabele, maar u kunt ook een Get-Job opdracht gebruiken om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-171">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="93ab8-172">Houd er rekening mee dat de waarde van de eigenschap locatie laat zien dat de taak is uitgevoerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-172">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

#### <a name="step-2-get-job"></a><span data-ttu-id="93ab8-173">STAP 2: GET-JOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-173">STEP 2: GET-JOB</span></span>

<span data-ttu-id="93ab8-174">Voor het beheren van een taak die is gestart met behulp van de para meter AsJob van de cmdlet Invoke-Command, gebruikt u de taak-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="93ab8-174">To manage a job started by using the AsJob parameter of the Invoke-Command cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="93ab8-175">Omdat het taak object dat de externe taak vertegenwoordigt, zich op de lokale computer bevindt, hoeft u geen externe opdrachten uit te voeren om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="93ab8-175">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

<span data-ttu-id="93ab8-176">Gebruik een Get-Job opdracht om te bepalen of de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="93ab8-176">To determine whether the job is complete, use a Get-Job command.</span></span> <span data-ttu-id="93ab8-177">Met de volgende opdracht worden alle taken opgehaald die in de huidige sessie zijn gestart.</span><span class="sxs-lookup"><span data-stu-id="93ab8-177">The following command gets all of the jobs that were started in the current session.</span></span>

```powershell
get-job
```

<span data-ttu-id="93ab8-178">Omdat de externe taak is gestart in de huidige sessie, haalt een lokale Get-Job opdracht de taak op.</span><span class="sxs-lookup"><span data-stu-id="93ab8-178">Because the remote job was started in the current session, a local Get-Job command gets the job.</span></span> <span data-ttu-id="93ab8-179">De eigenschap State van het taak object geeft aan dat de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="93ab8-179">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a><span data-ttu-id="93ab8-180">STAP 3: RECEIVE-JOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-180">STEP 3: RECEIVE-JOB</span></span>

<span data-ttu-id="93ab8-181">Gebruik de cmdlet Receive-Job om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-181">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="93ab8-182">Omdat de resultaten van de taak automatisch worden teruggestuurd naar de computer waarop het taak object zich bevindt, kunt u de resultaten ophalen met een lokale Receive-Job opdracht.</span><span class="sxs-lookup"><span data-stu-id="93ab8-182">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local Receive-Job command.</span></span>

<span data-ttu-id="93ab8-183">De volgende opdracht maakt gebruik van de cmdlet Receive-Job om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-183">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="93ab8-184">De sessie-ID wordt gebruikt om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="93ab8-184">It uses the session ID to identify the job.</span></span> <span data-ttu-id="93ab8-185">Met deze opdracht worden de taak resultaten opgeslagen in de variabele $results.</span><span class="sxs-lookup"><span data-stu-id="93ab8-185">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="93ab8-186">U kunt de resultaten ook omleiden naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="93ab8-186">You can also redirect the results to a file.</span></span>

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="93ab8-187">EEN EXTERNE TAAK STARTEN DIE DE RESULTATEN OP DE EXTERNE COMPUTER BEWAART</span><span class="sxs-lookup"><span data-stu-id="93ab8-187">START A REMOTE JOB THAT KEEPS THE RESULTS ON THE REMOTE COMPUTER</span></span>

<span data-ttu-id="93ab8-188">Als u een achtergrond taak wilt starten op een externe computer die de opdracht resultaten op de externe computer houdt, gebruikt u de cmdlet Invoke-Command om een Start-Job opdracht uit te voeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-188">To start a background job on a remote computer that keeps the command results on the remote computer, use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span> <span data-ttu-id="93ab8-189">U kunt deze methode gebruiken om achtergrond taken uit te voeren op meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="93ab8-189">You can use this method to run background jobs on multiple computers.</span></span>

<span data-ttu-id="93ab8-190">Wanneer u een Start-Job opdracht op afstand uitvoert, wordt het taak object op de externe computer gemaakt en worden de taak resultaten op de externe computer bewaard.</span><span class="sxs-lookup"><span data-stu-id="93ab8-190">When you run a Start-Job command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="93ab8-191">Vanuit het perspectief van de taak zijn alle bewerkingen lokaal.</span><span class="sxs-lookup"><span data-stu-id="93ab8-191">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="93ab8-192">U hoeft alleen opdrachten op afstand uit te voeren om een lokale taak op de externe computer te beheren.</span><span class="sxs-lookup"><span data-stu-id="93ab8-192">You are just running commands remotely to manage a local job on the remote computer.</span></span>

#### <a name="step-1-invoke-command-start-job"></a><span data-ttu-id="93ab8-193">STAP 1: INVOKE-OPDRACHT STARTEN-TAAK</span><span class="sxs-lookup"><span data-stu-id="93ab8-193">STEP 1: INVOKE-COMMAND START-JOB</span></span>

<span data-ttu-id="93ab8-194">Gebruik de cmdlet Invoke-Command om een Start-Job opdracht uit te voeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-194">Use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span>

<span data-ttu-id="93ab8-195">Voor deze opdracht is een PSSession (een permanente verbinding) vereist.</span><span class="sxs-lookup"><span data-stu-id="93ab8-195">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="93ab8-196">Als u de para meter ComputerName van Invoke-Command gebruikt om een tijdelijke verbinding tot stand te brengen, wordt de Invoke-Command-opdracht als voltooid beschouwd wanneer het taak object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="93ab8-196">If you use the ComputerName parameter of Invoke-Command to establish a temporary connection, the Invoke-Command command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="93ab8-197">Als gevolg hiervan wordt de tijdelijke verbinding gesloten en wordt de taak geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="93ab8-197">As a result, the temporary connection is closed, and the job is canceled.</span></span>

<span data-ttu-id="93ab8-198">De volgende opdracht maakt gebruik van de New-PSSession cmdlet om een PSSession te maken die is verbonden met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-198">The following command uses the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="93ab8-199">Met de opdracht slaat u de PSSession op in de \$ variabele s.</span><span class="sxs-lookup"><span data-stu-id="93ab8-199">The command saves the PSSession in the \$s variable.</span></span>

```powershell
$s = new-pssession -computername Server01
```

<span data-ttu-id="93ab8-200">De volgende opdracht maakt gebruik van de cmdlet Invoke-Command om een Start-Job opdracht uit te voeren in de PSSession.</span><span class="sxs-lookup"><span data-stu-id="93ab8-200">The next command uses the Invoke-Command cmdlet to run a Start-Job command in the PSSession.</span></span> <span data-ttu-id="93ab8-201">De Start-Job opdracht en de Get-Eventlog opdracht staan tussen accolades.</span><span class="sxs-lookup"><span data-stu-id="93ab8-201">The Start-Job command and the Get-Eventlog command are enclosed in braces.</span></span>

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

<span data-ttu-id="93ab8-202">De resultaten zijn vergelijkbaar met de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-202">The results resemble the following sample output.</span></span>

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

<span data-ttu-id="93ab8-203">Wanneer u een Start-Job opdracht op afstand uitvoert, Invoke-Command retourneert hetzelfde type taak object dat Start-Job retourneert.</span><span class="sxs-lookup"><span data-stu-id="93ab8-203">When you run a Start-Job command remotely, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="93ab8-204">U kunt het taak object opslaan in een variabele, maar u kunt ook een Get-Job opdracht gebruiken om de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-204">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="93ab8-205">Houd er rekening mee dat de waarde van de eigenschap locatie aangeeft dat de taak is uitgevoerd op de lokale computer, ook wel ' LocalHost ' genoemd, hoewel de taak is uitgevoerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-205">Note that the value of the Location property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="93ab8-206">Omdat het taak object op de Server01-computer wordt gemaakt en de taak wordt uitgevoerd op dezelfde computer, wordt deze als een lokale achtergrond taak beschouwd.</span><span class="sxs-lookup"><span data-stu-id="93ab8-206">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

#### <a name="step-2-invoke-command-get-job"></a><span data-ttu-id="93ab8-207">STAP 2: INVOKE-OPDRACHT GET-JOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-207">STEP 2: INVOKE-COMMAND GET-JOB</span></span>

<span data-ttu-id="93ab8-208">Als u een externe achtergrond taak wilt beheren, gebruikt u de taak-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="93ab8-208">To manage a remote background job, use the Job cmdlets.</span></span> <span data-ttu-id="93ab8-209">Omdat het taak object zich op de externe computer bevindt, moet u externe opdrachten uitvoeren om de taak resultaten op te halen, te stoppen, te wachten of op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-209">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

<span data-ttu-id="93ab8-210">Als u wilt zien of de taak is voltooid, gebruikt u een Invoke-Command opdracht om een Get-Job opdracht uit te voeren in de PSSession die is verbonden met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-210">To see if the job is complete, use an Invoke-Command command to run a Get-Job command in the PSSession that is connected to the Server01 computer.</span></span>

```powershell
invoke-command -session $s -scriptblock {get-job}
```

<span data-ttu-id="93ab8-211">De opdracht retourneert een taak object.</span><span class="sxs-lookup"><span data-stu-id="93ab8-211">The command returns a job object.</span></span> <span data-ttu-id="93ab8-212">De eigenschap State van het taak object geeft aan dat de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="93ab8-212">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a><span data-ttu-id="93ab8-213">STAP 3: INVOKE-OPDRACHT RECEIVE-JOB</span><span class="sxs-lookup"><span data-stu-id="93ab8-213">STEP 3: INVOKE-COMMAND RECEIVE-JOB</span></span>

<span data-ttu-id="93ab8-214">Als u de resultaten van de taak wilt weer geven, gebruikt u de cmdlet Invoke-Command om een Receive-Job opdracht uit te voeren in de PSSession die is verbonden met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-214">To get the results of the job, use the Invoke-Command cmdlet to run a Receive-Job command in the PSSession that is connected to the Server01 computer.</span></span>

<span data-ttu-id="93ab8-215">De volgende opdracht maakt gebruik van de cmdlet Receive-Job om de resultaten van de taak op te halen.</span><span class="sxs-lookup"><span data-stu-id="93ab8-215">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="93ab8-216">De sessie-ID wordt gebruikt om de taak te identificeren.</span><span class="sxs-lookup"><span data-stu-id="93ab8-216">It uses the session ID to identify the job.</span></span> <span data-ttu-id="93ab8-217">Met deze opdracht worden de taak resultaten opgeslagen in de \$ resultaten variabele.</span><span class="sxs-lookup"><span data-stu-id="93ab8-217">This command saves the job results in the \$results variable.</span></span> <span data-ttu-id="93ab8-218">De para meter ' Keep ' van Receive-Job wordt gebruikt om het resultaat in de taak cache op de externe computer te blijven gebruiken.</span><span class="sxs-lookup"><span data-stu-id="93ab8-218">It uses the Keep parameter of Receive-Job to keep the result in the job cache on the remote computer.</span></span>

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

<span data-ttu-id="93ab8-219">U kunt de resultaten ook omleiden naar een bestand op de lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-219">You can also redirect the results to a file on the local or remote computer.</span></span>
<span data-ttu-id="93ab8-220">De volgende opdracht maakt gebruik van een omleidings operator om de resultaten op te slaan in een bestand op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="93ab8-220">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a><span data-ttu-id="93ab8-221">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="93ab8-221">SEE ALSO</span></span>

[<span data-ttu-id="93ab8-222">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="93ab8-222">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="93ab8-223">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="93ab8-223">about_Job_Details</span></span>](about_Job_Details.md)

[<span data-ttu-id="93ab8-224">about_Remote</span><span class="sxs-lookup"><span data-stu-id="93ab8-224">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="93ab8-225">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="93ab8-225">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="93ab8-226">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="93ab8-226">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="93ab8-227">Begin taak</span><span class="sxs-lookup"><span data-stu-id="93ab8-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)

[<span data-ttu-id="93ab8-228">Get-job</span><span class="sxs-lookup"><span data-stu-id="93ab8-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)

[<span data-ttu-id="93ab8-229">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="93ab8-229">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)

[<span data-ttu-id="93ab8-230">Stoppen-taak</span><span class="sxs-lookup"><span data-stu-id="93ab8-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)

[<span data-ttu-id="93ab8-231">Verwijderen-taak</span><span class="sxs-lookup"><span data-stu-id="93ab8-231">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)

[<span data-ttu-id="93ab8-232">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="93ab8-232">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="93ab8-233">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="93ab8-233">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="93ab8-234">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="93ab8-234">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

