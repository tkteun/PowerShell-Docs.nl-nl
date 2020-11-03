---
description: Hierin worden geplande taken beschreven en wordt uitgelegd hoe u geplande taken in Power shell en in taak planner kunt gebruiken en beheren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252414"
---
# <a name="about-scheduled-jobs"></a><span data-ttu-id="a6693-104">Over geplande taken</span><span class="sxs-lookup"><span data-stu-id="a6693-104">About Scheduled Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="a6693-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="a6693-105">Short description</span></span>

<span data-ttu-id="a6693-106">Hierin worden geplande taken beschreven en wordt uitgelegd hoe u geplande taken in Power shell en in taak planner kunt gebruiken en beheren.</span><span class="sxs-lookup"><span data-stu-id="a6693-106">Describes scheduled jobs and explains how to use and manage scheduled jobs in PowerShell and in Task Scheduler.</span></span>

## <a name="long-description"></a><span data-ttu-id="a6693-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="a6693-107">Long description</span></span>

<span data-ttu-id="a6693-108">Geplande power shell-taken zijn een nuttige hybride van Power shell-achtergrond taken en taak planner taken.</span><span class="sxs-lookup"><span data-stu-id="a6693-108">PowerShell scheduled jobs are a useful hybrid of PowerShell background jobs and Task Scheduler tasks.</span></span>

<span data-ttu-id="a6693-109">Net als Power shell-achtergrond taken worden geplande taken asynchroon uitgevoerd op de achtergrond.</span><span class="sxs-lookup"><span data-stu-id="a6693-109">Like PowerShell background jobs, scheduled jobs run asynchronously in the background.</span></span> <span data-ttu-id="a6693-110">Exemplaren van geplande taken die zijn uitgevoerd, kunnen worden beheerd met behulp van de taak-cmdlets, zoals `Start-Job` ,, `Get-Job` `Stop-Job` en `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="a6693-110">Instances of scheduled jobs that have run can be managed by using the job cmdlets, such as `Start-Job`, `Get-Job`, `Stop-Job`, and `Receive-Job`.</span></span>

<span data-ttu-id="a6693-111">Geplande taken worden als taak planner-taken opgeslagen op schijf.</span><span class="sxs-lookup"><span data-stu-id="a6693-111">Like Task Scheduler tasks, scheduled jobs are saved to disk.</span></span> <span data-ttu-id="a6693-112">U kunt de taken weer geven en beheren in Task Scheduler, inschakelen en uitschakelen als dat nodig is, ze uitvoeren of gebruiken als sjablonen, een eenmalige of terugkerende planning instellen voor het starten van de taken of voor waarden opgeven waaronder de taken worden gestart.</span><span class="sxs-lookup"><span data-stu-id="a6693-112">You can view and manage the jobs in Task Scheduler, enable and disable them as needed, run them or use them as templates, establish a one-time or recurring schedules for starting the jobs, or set conditions under which the jobs start.</span></span>

<span data-ttu-id="a6693-113">Daarnaast worden de resultaten van geplande-taak exemplaren opgeslagen op schijf in een gemakkelijk toegankelijke indeling, die een actief logboek van de taak uitvoer biedt.</span><span class="sxs-lookup"><span data-stu-id="a6693-113">In addition, the results of scheduled job instances are saved to disk in an easily accessible format, providing a running log of job output.</span></span> <span data-ttu-id="a6693-114">Geplande taken worden geleverd met een aangepaste set cmdlets voor het beheren ervan.</span><span class="sxs-lookup"><span data-stu-id="a6693-114">Scheduled jobs come with a customized set of cmdlets for managing them.</span></span> <span data-ttu-id="a6693-115">Met de cmdlets kunt u geplande taken, taak triggers en taak opties maken, bewerken, beheren, uitschakelen en opnieuw inschakelen.</span><span class="sxs-lookup"><span data-stu-id="a6693-115">The cmdlets let you create, edit, manage, disable, and re-enable scheduled jobs, job triggers and job options.</span></span>

<span data-ttu-id="a6693-116">Deze uitgebreide en flexibele set hulpprogram ma's maken geplande taken een essentieel onderdeel van een groot aantal professionele Power shell-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="a6693-116">This comprehensive and flexible set of tools make scheduled jobs an essential component of many professional PowerShell IT solutions.</span></span>

<span data-ttu-id="a6693-117">De geplande taak-cmdlets zijn opgenomen in de **PSScheduledJob** -module die is geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a6693-117">The scheduled job cmdlets are included in the **PSScheduledJob** module that is installed with PowerShell.</span></span> <span data-ttu-id="a6693-118">Deze module werd geïntroduceerd in Power Shell 3,0 en werkt in Power Shell 3,0 en latere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="a6693-118">This module was introduced in PowerShell 3.0 and works in PowerShell 3.0 and later versions of PowerShell.</span></span> <span data-ttu-id="a6693-119">Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.</span><span class="sxs-lookup"><span data-stu-id="a6693-119">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

<span data-ttu-id="a6693-120">Zie [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="a6693-120">For more information about PowerShell background jobs, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

<span data-ttu-id="a6693-121">Zie [taak planner](/windows/desktop/TaskSchd/task-scheduler-reference)voor meer informatie over taak planner.</span><span class="sxs-lookup"><span data-stu-id="a6693-121">For more information about Task Scheduler, see [Task Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference).</span></span>

> [!NOTE]
> <span data-ttu-id="a6693-122">U kunt geplande power shell-taken weer geven en beheren in taak planner.</span><span class="sxs-lookup"><span data-stu-id="a6693-122">You can view and manage PowerShell scheduled jobs in Task Scheduler.</span></span> <span data-ttu-id="a6693-123">De cmdlets voor Power shell-taken en geplande taken werken alleen voor geplande taken die in Power shell zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a6693-123">The PowerShell jobs and scheduled job cmdlets work only on scheduled jobs that are created in PowerShell.</span></span>

## <a name="quick-start"></a><span data-ttu-id="a6693-124">Snel starten</span><span class="sxs-lookup"><span data-stu-id="a6693-124">Quick start</span></span>

<span data-ttu-id="a6693-125">In dit voor beeld wordt een geplande taak gemaakt die elke dag om 3:00 uur wordt gestart en de `Get-Process` cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a6693-125">This example creates a scheduled job that starts every day at 3:00 AM and runs the `Get-Process` cmdlet.</span></span> <span data-ttu-id="a6693-126">De taak wordt gestart, zelfs als de computer op een accu werkt.</span><span class="sxs-lookup"><span data-stu-id="a6693-126">The job starts even if the computer is running on batteries.</span></span>

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

<span data-ttu-id="a6693-127">De `Get-ScheduledJob` cmdlet haalt de geplande taken op de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="a6693-127">The `Get-ScheduledJob` cmdlet gets the scheduled jobs on the local computer.</span></span>

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

<span data-ttu-id="a6693-128">`Get-JobTrigger` Hiermee worden de taak triggers van **ProcessJob** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a6693-128">`Get-JobTrigger` gets the job triggers of **ProcessJob**.</span></span> <span data-ttu-id="a6693-129">De invoer parameters geven de geplande taak op, niet de trigger, omdat triggers worden opgeslagen in een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="a6693-129">The input parameters specify the scheduled job, not the trigger, because triggers are saved in a scheduled job.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

<span data-ttu-id="a6693-130">In dit voor beeld wordt de para meter **ContinueIfGoingOnBattery** van de `Set-ScheduledJob` cmdlet gebruikt om de eigenschap **StopIfGoingOnBatteries** van **ProcessJob** te wijzigen in **False**.</span><span class="sxs-lookup"><span data-stu-id="a6693-130">This example uses the **ContinueIfGoingOnBattery** parameter of the `Set-ScheduledJob` cmdlet to change the **StopIfGoingOnBatteries** property of **ProcessJob** to **False**.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
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

<span data-ttu-id="a6693-131">De `Get-ScheduledJob` cmdlet krijgt de geplande taak **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="a6693-131">The `Get-ScheduledJob` cmdlet gets the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

<span data-ttu-id="a6693-132">De `Get-Job` cmdlet haalt alle exemplaren op van de geplande **ProcessJob** -taak die tot nu toe is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a6693-132">The `Get-Job` cmdlet gets all instances of the **ProcessJob** scheduled job that have run thus far.</span></span> <span data-ttu-id="a6693-133">De `Get-Job` cmdlet haalt alleen geplande taken op wanneer de **PSScheduledJob** -module in de huidige sessie wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a6693-133">The `Get-Job` cmdlet gets scheduled jobs only when the **PSScheduledJob** module is imported into the current session.</span></span>

> [!TIP]
> <span data-ttu-id="a6693-134">U ziet dat u de geplande taak-cmdlets gebruikt om geplande taken te beheren, maar u kunt de taak-cmdlets gebruiken om exemplaren van geplande taken te beheren.</span><span class="sxs-lookup"><span data-stu-id="a6693-134">Notice that you use the scheduled job cmdlets to manage scheduled jobs, but you use the job cmdlets to manage instances of scheduled jobs.</span></span>

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

<span data-ttu-id="a6693-135">De `Receive-Job` cmdlet haalt de resultaten van het meest recente exemplaar van de geplande **ProcessJob** -taak (id = 51) op.</span><span class="sxs-lookup"><span data-stu-id="a6693-135">The `Receive-Job` cmdlet gets the results of the most recent instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Receive-Job -ID 51
```

<span data-ttu-id="a6693-136">Hoewel de `Receive-Job` opdracht de para meter **Keep** niet bevat, worden de resultaten van de taak op schijf opgeslagen totdat u ze verwijdert of het maximum aantal resultaten wordt overschreden.</span><span class="sxs-lookup"><span data-stu-id="a6693-136">Even though the `Receive-Job` command did not include the **Keep** parameter, the results of the job are saved on disk until you delete them or the maximum number of results are exceeded.</span></span>

<span data-ttu-id="a6693-137">De taak resultaten zijn niet meer beschikbaar in deze sessie, maar als u een nieuwe sessie start of een nieuw Power shell-venster opent, zijn de resultaten van de taak weer beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="a6693-137">The job results are no longer available in this session, but if you start a new session or open a new PowerShell window, the results of the job are available again.</span></span>

<span data-ttu-id="a6693-138">De volgende opdracht maakt gebruik van de para meter **definitienaam** van de `Start-Job` cmdlet om de geplande taak **ProcessJob** te starten.</span><span class="sxs-lookup"><span data-stu-id="a6693-138">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the **ProcessJob** scheduled job.</span></span>

<span data-ttu-id="a6693-139">Taken die zijn gestart met behulp van de `Start-Job` cmdlet zijn standaard-Power shell-achtergrond taken, geen exemplaren van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="a6693-139">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="a6693-140">Net als bij alle achtergrond taken worden deze taken onmiddellijk gestart, niet onderhevig aan taak opties of worden beïnvloed door taak triggers, en de uitvoer ervan wordt niet opgeslagen in de uitvoermap van de geplande projectmap.</span><span class="sxs-lookup"><span data-stu-id="a6693-140">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers, and their output is not saved in the output directory of the scheduled job directory.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="a6693-141">De `Unregister-ScheduledJob` cmdlet verwijdert de geplande taak **ProcessJob** en alle opgeslagen resultaten van de bijbehorende taak exemplaren.</span><span class="sxs-lookup"><span data-stu-id="a6693-141">The `Unregister-ScheduledJob` cmdlet deletes the **ProcessJob** scheduled job and all saved results of its job instances.</span></span>

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a><span data-ttu-id="a6693-142">Concepten van geplande taken</span><span class="sxs-lookup"><span data-stu-id="a6693-142">Scheduled jobs concepts</span></span>

<span data-ttu-id="a6693-143">Een geplande taak voert opdrachten of een script uit.</span><span class="sxs-lookup"><span data-stu-id="a6693-143">A scheduled job runs commands or a script.</span></span> <span data-ttu-id="a6693-144">Een geplande taak kan taak triggers bevatten waarmee de taak-en taak opties worden gestart die de voor waarden voor het uitvoeren van de taak instellen.</span><span class="sxs-lookup"><span data-stu-id="a6693-144">A scheduled job can include job triggers that start the job and job options that set conditions for running the job.</span></span>

<span data-ttu-id="a6693-145">Een taak trigger start een geplande taak automatisch.</span><span class="sxs-lookup"><span data-stu-id="a6693-145">A job trigger starts a scheduled job automatically.</span></span> <span data-ttu-id="a6693-146">Een taak trigger kan een eenmalige of terugkerende planning bevatten of een gebeurtenis opgeven, bijvoorbeeld wanneer een gebruiker zich aanmeldt of als Windows wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a6693-146">A job trigger can include a one-time or recurring schedule or specify an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="a6693-147">Een geplande taak kan een of meer taak triggers hebben en u kunt taak triggers maken, toevoegen, inschakelen, uitschakelen en ophalen.</span><span class="sxs-lookup"><span data-stu-id="a6693-147">A scheduled job can have one or more job triggers, and you can create, add, enable, disable, and get job triggers.</span></span>

<span data-ttu-id="a6693-148">Taak triggers zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="a6693-148">Job triggers are optional.</span></span> <span data-ttu-id="a6693-149">U kunt geplande taken onmiddellijk starten met behulp van de `Start-Job cmdlet` , of door de para meter **RunNow** toe te voegen aan de `Register-ScheduledJob` opdracht.</span><span class="sxs-lookup"><span data-stu-id="a6693-149">You can start scheduled jobs immediately by using the `Start-Job cmdlet`, or by adding the **RunNow** parameter to your `Register-ScheduledJob` command.</span></span>

<span data-ttu-id="a6693-150">Met taak opties stelt u de voor waarden in voor het uitvoeren van een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="a6693-150">Job options set the conditions for running a scheduled job.</span></span> <span data-ttu-id="a6693-151">Elke geplande taak heeft één taak opties-object.</span><span class="sxs-lookup"><span data-stu-id="a6693-151">Every scheduled job has one job options object.</span></span> <span data-ttu-id="a6693-152">U kunt taak opties objecten maken en bewerken en toevoegen aan een of meer geplande taken.</span><span class="sxs-lookup"><span data-stu-id="a6693-152">You can create and edit job options objects and add them to one or more scheduled jobs.</span></span>

<span data-ttu-id="a6693-153">Telkens wanneer een geplande taak wordt gestart, wordt een taak exemplaar gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a6693-153">Each time a scheduled job starts, a job instance is created.</span></span> <span data-ttu-id="a6693-154">Gebruik de Power shell-taak-cmdlets om het taak exemplaar te bekijken en te beheren.</span><span class="sxs-lookup"><span data-stu-id="a6693-154">Use the PowerShell job cmdlets to view and manage the job instance.</span></span>

<span data-ttu-id="a6693-155">Geplande taken worden op schijf opgeslagen en gebruiken de werk-cmdlet, `Register` in plaats van `New` .</span><span class="sxs-lookup"><span data-stu-id="a6693-155">Scheduled jobs are saved to disk and use the cmdlet verb, `Register`, instead of `New`.</span></span> <span data-ttu-id="a6693-156">De XML-bestanden bevinden zich op de lokale computer in de Directory `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .</span><span class="sxs-lookup"><span data-stu-id="a6693-156">The XML files are located on the local computer in the directory `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

<span data-ttu-id="a6693-157">In Power shell wordt een map voor elke geplande taak gemaakt en worden de opdracht opdrachten, taak triggers, taak opties en taak resultaten opgeslagen in de map geplande taak.</span><span class="sxs-lookup"><span data-stu-id="a6693-157">PowerShell creates a directory for each scheduled job and saves the job commands, job triggers, job options and job results in the scheduled job directory.</span></span> <span data-ttu-id="a6693-158">Taak triggers en taak opties worden niet onafhankelijk op schijf opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a6693-158">Job triggers and job options aren't saved to disk independently.</span></span>
<span data-ttu-id="a6693-159">Ze worden opgeslagen in de geplande XML-taak van elke geplande taak waarmee ze zijn verbonden.</span><span class="sxs-lookup"><span data-stu-id="a6693-159">They are saved in the scheduled job XML of each scheduled job with which they are associated.</span></span>

<span data-ttu-id="a6693-160">Geplande taken, taak triggers en taak opties worden weer gegeven in Power shell als objecten.</span><span class="sxs-lookup"><span data-stu-id="a6693-160">Scheduled jobs, job triggers, and job options appear in PowerShell as objects.</span></span>
<span data-ttu-id="a6693-161">De objecten zijn gekoppeld, waardoor ze eenvoudig kunnen worden gedetecteerd en gebruikt in opdrachten en scripts.</span><span class="sxs-lookup"><span data-stu-id="a6693-161">The objects are interlinked, which makes them easy to discover and use in commands and scripts.</span></span>

<span data-ttu-id="a6693-162">Geplande taken worden weer gegeven als **ScheduledJobDefinition** -objecten.</span><span class="sxs-lookup"><span data-stu-id="a6693-162">Scheduled jobs appear as **ScheduledJobDefinition** objects.</span></span> <span data-ttu-id="a6693-163">Het **ScheduledJobDefinition** -object heeft een **JobTriggers** -eigenschap die de taak triggers van de geplande taak bevat en een **optie** -eigenschap die de taak opties bevat.</span><span class="sxs-lookup"><span data-stu-id="a6693-163">The **ScheduledJobDefinition** object has a **JobTriggers** property that contains the job triggers of the scheduled job and an **Options** property that contains the job options.</span></span> <span data-ttu-id="a6693-164">De **ScheduledJobTriggers** -en **ScheduledJobOptions** -objecten die respectievelijk taak triggers en taak opties vertegenwoordigen, hebben elk een eigenschap **taak definitie** die de geplande taak bevat waarmee ze zijn verbonden.</span><span class="sxs-lookup"><span data-stu-id="a6693-164">The **ScheduledJobTriggers** and **ScheduledJobOptions** objects that represent job triggers and job options, respectively, each have a **JobDefinition** property that contains the scheduled job with which they are associated.</span></span> <span data-ttu-id="a6693-165">Deze recursieve interconnectie maakt het eenvoudig om de triggers en opties van een geplande taak te vinden en om de geplande taak waarmee een taak trigger of taak optie is gekoppeld, te zoeken, te scripteren en weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a6693-165">This recursive interconnection makes it easy to find the triggers and options of a scheduled job and to find, script, and display the scheduled job to which any job trigger or job option is associated.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6693-166">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a6693-166">See also</span></span>

[<span data-ttu-id="a6693-167">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="a6693-167">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="a6693-168">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="a6693-168">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="a6693-169">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="a6693-169">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

<span data-ttu-id="a6693-170">[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets</span><span class="sxs-lookup"><span data-stu-id="a6693-170">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="a6693-171">Taak planner</span><span class="sxs-lookup"><span data-stu-id="a6693-171">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
