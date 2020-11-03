---
description: Hierin wordt uitgelegd hoe u geplande taken maakt en beheert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252411"
---
# <a name="about-scheduled-jobs-basics"></a><span data-ttu-id="e0222-104">Over de basis beginselen van geplande taken</span><span class="sxs-lookup"><span data-stu-id="e0222-104">About Scheduled Jobs Basics</span></span>

## <a name="short-description"></a><span data-ttu-id="e0222-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0222-105">Short description</span></span>

<span data-ttu-id="e0222-106">Hierin wordt uitgelegd hoe u geplande taken maakt en beheert.</span><span class="sxs-lookup"><span data-stu-id="e0222-106">Explains how to create and manage scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="e0222-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0222-107">Long description</span></span>

<span data-ttu-id="e0222-108">Dit document bevat informatie over het uitvoeren van basis taken voor het maken en beheren van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="e0222-108">This document shows how to perform basic tasks of creating and managing scheduled jobs.</span></span> <span data-ttu-id="e0222-109">Zie [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)voor meer informatie over geavanceerde taken.</span><span class="sxs-lookup"><span data-stu-id="e0222-109">For information about more advanced tasks, see [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).</span></span>

<span data-ttu-id="e0222-110">Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.</span><span class="sxs-lookup"><span data-stu-id="e0222-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="how-to-create-a-scheduled-job"></a><span data-ttu-id="e0222-111">Een geplande taak maken</span><span class="sxs-lookup"><span data-stu-id="e0222-111">How to create a scheduled job</span></span>

<span data-ttu-id="e0222-112">Als u een geplande taak wilt maken, gebruikt u de `Register-ScheduledJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0222-112">To create a scheduled job, use the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="e0222-113">De cmdlet vereist een naam en de opdrachten of het script dat door de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e0222-113">The cmdlet requires a name and the commands or script that the job runs.</span></span> <span data-ttu-id="e0222-114">U kunt de taak onmiddellijk uitvoeren door de para meter **RunNow** toe te voegen, of een taak trigger te maken en taak opties in te stellen wanneer u de taak maakt of een bestaande taak bewerkt.</span><span class="sxs-lookup"><span data-stu-id="e0222-114">You can either run the job immediately by adding the **RunNow** parameter, or create a job trigger and set job options when you create the job, or edit an existing job.</span></span>

<span data-ttu-id="e0222-115">Als u een taak wilt maken waarmee een script wordt uitgevoerd, gebruikt u de **filepath** para meter om het pad naar het script bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="e0222-115">To create a job that runs a script, use the **FilePath** parameter to specify the path to the script file.</span></span> <span data-ttu-id="e0222-116">Als u een taak wilt maken die opdrachten uitvoert, gebruikt u de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="e0222-116">To create a job that runs commands, use the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="e0222-117">De `Register-ScheduledJob` cmdlet maakt de **ProcessJob** , waarmee een opdracht wordt uitgevoerd `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="e0222-117">The `Register-ScheduledJob` cmdlet creates the **ProcessJob** , which runs a `Get-Process` command.</span></span> <span data-ttu-id="e0222-118">Deze geplande taak heeft de standaard taak opties en geen taak trigger.</span><span class="sxs-lookup"><span data-stu-id="e0222-118">This scheduled job has the default job options and no job trigger.</span></span>

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a><span data-ttu-id="e0222-119">Een taak trigger maken</span><span class="sxs-lookup"><span data-stu-id="e0222-119">How to create a job trigger</span></span>

<span data-ttu-id="e0222-120">Taak triggers starten een geplande taak automatisch.</span><span class="sxs-lookup"><span data-stu-id="e0222-120">Job triggers start a scheduled job automatically.</span></span> <span data-ttu-id="e0222-121">Een taak trigger kan een eenmalige of terugkerende planning of een gebeurtenis zijn, zoals wanneer een gebruiker zich aanmeldt of als Windows wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e0222-121">A job trigger can be one-time or recurring schedule or an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="e0222-122">Elke taak kan nul, één of meerdere taak triggers hebben.</span><span class="sxs-lookup"><span data-stu-id="e0222-122">Each job can have zero, one, or multiple job triggers.</span></span>

<span data-ttu-id="e0222-123">Als u een taak trigger wilt maken, gebruikt u de `New-JobTrigger` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0222-123">To create a job trigger, use the `New-JobTrigger` cmdlet.</span></span> <span data-ttu-id="e0222-124">Met de volgende opdracht wordt een taak trigger gemaakt waarmee elke maandag en donderdag om 5:00 uur een taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e0222-124">The following command creates a job trigger that starts a job every Monday and Thursday at 5:00 AM.</span></span>
<span data-ttu-id="e0222-125">Met de opdracht wordt de taak trigger opgeslagen in de `$T` variabele.</span><span class="sxs-lookup"><span data-stu-id="e0222-125">The command saves the job trigger in the `$T` variable.</span></span>

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

<span data-ttu-id="e0222-126">Taak triggers zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="e0222-126">Job triggers are optional.</span></span> <span data-ttu-id="e0222-127">U kunt op elk gewenst moment een geplande taak starten door de para meter **RunNow** toe te voegen aan uw `Register-ScheduledJob` opdracht of door de- `Start-Job` cmdlets te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e0222-127">You can start a scheduled job at any time by adding the **RunNow** parameter to your `Register-ScheduledJob` command, or by using the `Start-Job` cmdlets.</span></span>

## <a name="how-to-add-a-job-trigger"></a><span data-ttu-id="e0222-128">Een taak trigger toevoegen</span><span class="sxs-lookup"><span data-stu-id="e0222-128">How to add a job trigger</span></span>

<span data-ttu-id="e0222-129">Wanneer u een taak trigger aan een geplande taak toevoegt, wordt de taak trigger toegevoegd aan het XML-bestand van de geplande taak voor de geplande taak en wordt het onderdeel van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-129">When you add a job trigger to a scheduled job, the job trigger is added to the scheduled job XML file for the scheduled job and becomes part of the scheduled job.</span></span>

<span data-ttu-id="e0222-130">U kunt een taak trigger toevoegen aan een geplande taak wanneer u de geplande taak maakt of een bestaande taak bewerkt.</span><span class="sxs-lookup"><span data-stu-id="e0222-130">You can add a job trigger to a scheduled job when you create the scheduled job, or edit an existing job.</span></span> <span data-ttu-id="e0222-131">U kunt de taak trigger van een geplande taak op elk gewenst moment wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e0222-131">You can change the job trigger of a scheduled job at any time.</span></span>

<span data-ttu-id="e0222-132">Power shell gebruikt enkele van dezelfde taak triggers die taak planner gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e0222-132">PowerShell uses some of the same job triggers that Task Scheduler uses.</span></span> <span data-ttu-id="e0222-133">Zie het Help-onderwerp voor de cmdlet [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) voor meer informatie over taak triggers.</span><span class="sxs-lookup"><span data-stu-id="e0222-133">For detailed information about job triggers, see the help topic for the [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) cmdlet.</span></span>

<span data-ttu-id="e0222-134">In het volgende voor beeld wordt splatting gebruikt om `$JobParms` de parameter waarden te maken die worden door gegeven aan de `Register-ScheduledJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0222-134">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="e0222-135">Zie [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e0222-135">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="e0222-136">`Register-ScheduledJob`Hiermee `@JobParms` maakt u een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-136">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="e0222-137">De **trigger** parameter wordt gebruikt om de taak trigger in de variabele op te geven `$T` .</span><span class="sxs-lookup"><span data-stu-id="e0222-137">It uses the **Trigger** parameter to specify the job trigger in the `$T` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="e0222-138">U kunt op elk gewenst moment ook een taak trigger toevoegen aan een bestaande geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-138">You can also add a job trigger to an existing scheduled job at any time.</span></span> <span data-ttu-id="e0222-139">De `Add-JobTrigger` cmdlet voegt de taak trigger in de `$T` variabele toe aan de geplande taak **ProcessJob** .</span><span class="sxs-lookup"><span data-stu-id="e0222-139">The `Add-JobTrigger` cmdlet adds the job trigger in the `$T` variable to the **ProcessJob** scheduled job.</span></span>

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

<span data-ttu-id="e0222-140">Als gevolg hiervan start de taak trigger de **ProcessJob** automatisch elke maandag en donderdag om 5:00 uur.</span><span class="sxs-lookup"><span data-stu-id="e0222-140">As a result, the job trigger starts the **ProcessJob** automatically every Monday and Thursday at 5:00 AM.</span></span>

## <a name="how-to-get-a-job-trigger"></a><span data-ttu-id="e0222-141">Een taak trigger ophalen</span><span class="sxs-lookup"><span data-stu-id="e0222-141">How to get a job trigger</span></span>

<span data-ttu-id="e0222-142">Gebruik de cmdlet om de taak trigger van een geplande taak op te halen `Get-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="e0222-142">To get the job trigger of a scheduled job, use the `Get-JobTrigger` cmdlet.</span></span> <span data-ttu-id="e0222-143">Gebruik de para meters **name** , **id** en **input object** om de geplande taak op te geven, niet de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="e0222-143">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job trigger.</span></span>

<span data-ttu-id="e0222-144">`Get-JobTrigger` Hiermee wordt de taak trigger van de **ProcessJob** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0222-144">`Get-JobTrigger` gets the job trigger of the **ProcessJob**.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a><span data-ttu-id="e0222-145">Taak opties maken</span><span class="sxs-lookup"><span data-stu-id="e0222-145">How to create job options</span></span>

<span data-ttu-id="e0222-146">Taak opties bepalen de voor waarden voor het starten en uitvoeren van de taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-146">Job options establish conditions for starting and running the job.</span></span> <span data-ttu-id="e0222-147">Elke taak heeft de standaard taak opties tenzij u deze wijzigt.</span><span class="sxs-lookup"><span data-stu-id="e0222-147">Every job has the default job options unless you change them.</span></span> <span data-ttu-id="e0222-148">Omdat taak opties kunnen voor komen dat een taak op het geplande tijdstip wordt uitgevoerd, is het belang rijk om de taak opties te begrijpen en deze zorgvuldig te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e0222-148">Because job options can prevent a job from running at the scheduled time, it is important to understand the job options and use them carefully.</span></span>

<span data-ttu-id="e0222-149">Power Shell maakt gebruik van dezelfde taak opties die taak planner gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e0222-149">PowerShell uses the same job options that Task Scheduler uses.</span></span> <span data-ttu-id="e0222-150">Zie het Help-onderwerp voor [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)voor meer informatie over de taak opties.</span><span class="sxs-lookup"><span data-stu-id="e0222-150">For detailed information about the job options, see the help topic for [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

<span data-ttu-id="e0222-151">Taak opties worden opgeslagen in het XML-bestand met de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-151">Job options are stored in the scheduled job XML file.</span></span> <span data-ttu-id="e0222-152">U kunt taak opties instellen wanneer u een geplande taak maakt of deze op elk gewenst moment wijzigt.</span><span class="sxs-lookup"><span data-stu-id="e0222-152">You can set job options when you create a scheduled job or change them at any time.</span></span>

<span data-ttu-id="e0222-153">De `New-ScheduledJobOption` cmdlet maakt een geplande taak optie waarbij de optie geplande taak **WakeToRun** is ingesteld op waar.</span><span class="sxs-lookup"><span data-stu-id="e0222-153">The `New-ScheduledJobOption` cmdlet creates a scheduled job option in which the **WakeToRun** scheduled job option is set to True.</span></span> <span data-ttu-id="e0222-154">Met de optie **WakeToRun** wordt de geplande taak uitgevoerd, zelfs als de computer zich in de slaap stand of sluimer stand bevindt op de geplande begin tijd.</span><span class="sxs-lookup"><span data-stu-id="e0222-154">The **WakeToRun** option runs the scheduled job even if the computer is in the Sleep or Hibernate state at the scheduled start time.</span></span> <span data-ttu-id="e0222-155">Met de opdracht worden de taak opties in de `$O` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e0222-155">The command saves the job options in the `$O` variable.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a><span data-ttu-id="e0222-156">Hoe kan ik taak opties ophalen?</span><span class="sxs-lookup"><span data-stu-id="e0222-156">How to get job options</span></span>

<span data-ttu-id="e0222-157">Als u de taak opties van een geplande taak wilt weer geven, gebruikt u de `Get-ScheduledJobOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0222-157">To get the job options of a scheduled job, use the `Get-ScheduledJobOption` cmdlet.</span></span> <span data-ttu-id="e0222-158">Gebruik de para meters **name** , **id** en **input object** om de geplande taak op te geven, niet de taak opties.</span><span class="sxs-lookup"><span data-stu-id="e0222-158">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job options.</span></span>

<span data-ttu-id="e0222-159">`Get-ScheduledJobOption` Hiermee worden de taak opties van de **ProcessJob** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0222-159">`Get-ScheduledJobOption` gets the job options of the **ProcessJob**.</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
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

## <a name="how-to-change-job-options"></a><span data-ttu-id="e0222-160">Taak opties wijzigen</span><span class="sxs-lookup"><span data-stu-id="e0222-160">How to change job options</span></span>

<span data-ttu-id="e0222-161">U kunt de taak opties van een geplande taak wijzigen wanneer u een geplande taak maakt of een bestaande taak bewerkt.</span><span class="sxs-lookup"><span data-stu-id="e0222-161">You can change the job options of a scheduled job when you create a scheduled job or edit an existing job.</span></span>

<span data-ttu-id="e0222-162">De splatted `$JobParms` worden door gegeven aan de `Add-JobTrigger` cmdlet om de proces taak te maken.</span><span class="sxs-lookup"><span data-stu-id="e0222-162">The splatted `$JobParms` are passed to the `Add-JobTrigger` cmdlet to create the process job.</span></span> <span data-ttu-id="e0222-163">De para meter **ScheduledJobOption** wordt gebruikt om de taak opties in de variabele op te geven `$O` .</span><span class="sxs-lookup"><span data-stu-id="e0222-163">It uses the **ScheduledJobOption** parameter to specify the job options in the `$O` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

<span data-ttu-id="e0222-164">U kunt de taak opties ook op elk gewenst moment wijzigen in een bestaande geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-164">You can also change the job options to an existing scheduled job at any time.</span></span>
<span data-ttu-id="e0222-165">De volgende opdracht gebruikt de `Set-ScheduledJobOption` cmdlet om de waarde van de **WakeToRun** -optie van de **ProcessJob** scheduledJob te wijzigen in **True**.</span><span class="sxs-lookup"><span data-stu-id="e0222-165">The following command uses the `Set-ScheduledJobOption` cmdlet to change the value of the **WakeToRun** option of the **ProcessJob** scheduledJob to **True**.</span></span>

<span data-ttu-id="e0222-166">De `Set` cmdlets in de **PSScheduledJob** -module, zoals de `Set-ScheduledJobOption` cmdlet, hebben geen **naam** **-of id-** para meters.</span><span class="sxs-lookup"><span data-stu-id="e0222-166">The `Set` cmdlets in the **PSScheduledJob** module, such as the `Set-ScheduledJobOption` cmdlet, don't have **Name** or **ID** parameters.</span></span> <span data-ttu-id="e0222-167">U kunt de para meter **input object** gebruiken om de geplande taak opties op te geven of een geplande taak vanuit `Get-ScheduledJobOption` cmdlet naar te pipeen `Set-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="e0222-167">You can use the **InputObject** parameter to specify the scheduled job options or pipe a scheduled job from `Get-ScheduledJobOption` cmdlet to `Set-ScheduledJobOption`.</span></span>

<span data-ttu-id="e0222-168">In dit voor beeld wordt de `Get-ScheduledJob` cmdlet gebruikt om de ProcessJob op te halen.</span><span class="sxs-lookup"><span data-stu-id="e0222-168">This example uses the `Get-ScheduledJob` cmdlet to get the ProcessJob.</span></span> <span data-ttu-id="e0222-169">De cmdlet wordt gebruikt `Get-ScheduledJobOption` voor het ophalen van de taak opties in de **ProcessJob** en de `Set-ScheduledJobOption` cmdlet om de **WakeToRun** -taak optie in de ProcessJob te wijzigen in waar.</span><span class="sxs-lookup"><span data-stu-id="e0222-169">It uses the `Get-ScheduledJobOption` cmdlet to get the job options in the **ProcessJob** and the `Set-ScheduledJobOption` cmdlet to change the **WakeToRun** job option in the ProcessJob to True.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a><span data-ttu-id="e0222-170">Geplande taak instanties ophalen</span><span class="sxs-lookup"><span data-stu-id="e0222-170">How to get scheduled job instances</span></span>

<span data-ttu-id="e0222-171">Wanneer een geplande taak wordt gestart, maakt Power shell een taak exemplaar dat lijkt op een standaard-Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-171">When a scheduled job is started, PowerShell creates a job instance that is similar to a standard PowerShell background job.</span></span> <span data-ttu-id="e0222-172">U kunt de taak-cmdlets gebruiken, zoals `Get-Job` `Stop-Job` en `Receive-Job` voor het beheren van de taak exemplaren.</span><span class="sxs-lookup"><span data-stu-id="e0222-172">You can use the job cmdlets, such as `Get-Job`, `Stop-Job` and `Receive-Job` to manage the job instances.</span></span>

> [!NOTE]
> <span data-ttu-id="e0222-173">Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="e0222-173">To use the job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="e0222-174">Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="e0222-174">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="e0222-175">Als u alle instanties van Power shell-geplande taken en alle actieve standaard taken wilt ophalen, gebruikt u de `Get-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0222-175">To get all instances of PowerShell scheduled jobs, and all active standard jobs, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="e0222-176">`Import-Module`Met de cmdlet wordt de **PSScheduledJob** -module geïmporteerd en worden `Get-Job` de taken op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0222-176">The `Import-Module` cmdlet imports the **PSScheduledJob** module and `Get-Job` gets the jobs on the local computer.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job
```

<span data-ttu-id="e0222-177">`Get-Job` Hiermee worden de exemplaren van **ProcessJob** op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e0222-177">`Get-Job` gets instances of **ProcessJob** on the local computer.</span></span>

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

<span data-ttu-id="e0222-178">In de standaard weergave wordt de begin tijd niet weer gegeven. Dit onderscheidt meestal het aantal exemplaren van dezelfde geplande taak.</span><span class="sxs-lookup"><span data-stu-id="e0222-178">The default display does not show the start time, which typically distinguishes instances of the same scheduled job.</span></span>

<span data-ttu-id="e0222-179">De `Get-Job` cmdlet verzendt objecten uit de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e0222-179">The `Get-Job` cmdlet sends objects down the pipeline.</span></span> <span data-ttu-id="e0222-180">`Format-Table`Met de cmdlet worden de eigenschappen **name** , **id** en **BeginTime** van de geplande taak weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e0222-180">The `Format-Table` cmdlet displays the **Name** , **ID** , and **BeginTime** properties of the scheduled job.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
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

## <a name="get-scheduled-job-results"></a><span data-ttu-id="e0222-181">Geplande taak resultaten ophalen</span><span class="sxs-lookup"><span data-stu-id="e0222-181">Get scheduled job results</span></span>

<span data-ttu-id="e0222-182">Gebruik de cmdlet om de resultaten van een exemplaar van een geplande taak op te halen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="e0222-182">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e0222-183">Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="e0222-183">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="e0222-184">Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="e0222-184">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="e0222-185">In deze voor beelden worden de resultaten opgehaald van het nieuwste exemplaar van de geplande **ProcessJob** -taak (ID = 51).</span><span class="sxs-lookup"><span data-stu-id="e0222-185">This examples gets the results of the newest instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

<span data-ttu-id="e0222-186">De resultaten van geplande taken worden op schijf opgeslagen, dus de para meter **behouden** van `Receive-Job` is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="e0222-186">The results of scheduled jobs are saved on disk, so the **Keep** parameter of `Receive-Job` is not required.</span></span> <span data-ttu-id="e0222-187">Zonder de para meter **Keep** kunt u echter de resultaten van een geplande taak slechts één keer in elke Power shell-sessie ophalen.</span><span class="sxs-lookup"><span data-stu-id="e0222-187">However, without the **Keep** parameter, you can get the results of a scheduled job only once in each PowerShell session.</span></span> <span data-ttu-id="e0222-188">Als u een nieuwe Power shell-sessie wilt starten, typt `PowerShell` of opent u een nieuw Power shell-venster.</span><span class="sxs-lookup"><span data-stu-id="e0222-188">To start a new PowerShell session, type `PowerShell` or open a new PowerShell window.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0222-189">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e0222-189">See also</span></span>

[<span data-ttu-id="e0222-190">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="e0222-190">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="e0222-191">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="e0222-191">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="e0222-192">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="e0222-192">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="e0222-193">about_Splatting. MD</span><span class="sxs-lookup"><span data-stu-id="e0222-193">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="e0222-194">[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets</span><span class="sxs-lookup"><span data-stu-id="e0222-194">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="e0222-195">Taak planner</span><span class="sxs-lookup"><span data-stu-id="e0222-195">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
