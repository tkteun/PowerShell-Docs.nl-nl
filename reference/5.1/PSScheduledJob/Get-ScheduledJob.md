---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250306"
---
# <span data-ttu-id="c4991-103">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c4991-103">Get-ScheduledJob</span></span>

## <span data-ttu-id="c4991-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c4991-104">SYNOPSIS</span></span>
<span data-ttu-id="c4991-105">Hiermee worden geplande taken opgehaald op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c4991-105">Gets scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="c4991-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c4991-106">SYNTAX</span></span>

### <span data-ttu-id="c4991-107">DefinitionId (standaard)</span><span class="sxs-lookup"><span data-stu-id="c4991-107">DefinitionId (Default)</span></span>

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c4991-108">Definitie</span><span class="sxs-lookup"><span data-stu-id="c4991-108">DefinitionName</span></span>

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="c4991-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c4991-109">DESCRIPTION</span></span>
<span data-ttu-id="c4991-110">De cmdlet **Get-ScheduledJob** haalt geplande taken op de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="c4991-110">The **Get-ScheduledJob** cmdlet gets scheduled jobs on the local computer.</span></span>
<span data-ttu-id="c4991-111">**Get-ScheduledJob** haalt alleen geplande taken op die door de huidige gebruiker zijn gemaakt met behulp van de cmdlet Register-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="c4991-111">**Get-ScheduledJob** gets only scheduled jobs that are created by the current user using the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="c4991-112">Hoewel taken die zijn gemaakt met behulp van de cmdlet **REGI ster-ScheduledJob** , worden weer gegeven in taak planner, worden met **Get-ScheduledJob** alleen geplande taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4991-112">Although jobs that are created by using the **Register-ScheduledJob** cmdlet appear in Task Scheduler, **Get-ScheduledJob** gets only scheduled jobs.</span></span>
<span data-ttu-id="c4991-113">Er worden geen geplande taken opgehaald die zijn gemaakt in taak planner.</span><span class="sxs-lookup"><span data-stu-id="c4991-113">It does not get scheduled tasks created in Task Scheduler.</span></span>

<span data-ttu-id="c4991-114">Zonder para meters haalt **Get-ScheduledJob** alle geplande taken op de computer op.</span><span class="sxs-lookup"><span data-stu-id="c4991-114">Without parameters, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="c4991-115">U kunt de para meters van **Get-ScheduledJob** gebruiken om geplande taken op basis van id of naam op te halen en ze te bekijken of door te sluizen naar andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c4991-115">You can use the parameters of **Get-ScheduledJob** to get scheduled jobs by ID or name and examine them or pipe them to other cmdlets.</span></span>

<span data-ttu-id="c4991-116">**Get-ScheduledJob** is een van een verzameling cmdlets voor taak planning in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c4991-116">**Get-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="c4991-117">Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="c4991-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="c4991-118">Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="c4991-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="c4991-119">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c4991-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="c4991-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c4991-120">EXAMPLES</span></span>

### <span data-ttu-id="c4991-121">Voor beeld 1: alle geplande taken ophalen</span><span class="sxs-lookup"><span data-stu-id="c4991-121">Example 1: Get all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob
```

<span data-ttu-id="c4991-122">Met deze opdracht worden alle geplande taken op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4991-122">This command gets all scheduled jobs on the local computer.</span></span>

### <span data-ttu-id="c4991-123">Voor beeld 2: geplande taken op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="c4991-123">Example 2: Get scheduled jobs by name</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

<span data-ttu-id="c4991-124">Met deze opdracht worden alle geplande taken opgehaald op de computer met namen die back-up of archief bevatten.</span><span class="sxs-lookup"><span data-stu-id="c4991-124">This command gets all scheduled jobs on the computer that have names that include Backup or Archive.</span></span>
<span data-ttu-id="c4991-125">Met deze opdracht indeling kunt u zoeken naar bepaalde taken.</span><span class="sxs-lookup"><span data-stu-id="c4991-125">This command format lets you search for particular jobs.</span></span>

### <span data-ttu-id="c4991-126">Voor beeld 3: geplande taken ophalen op externe computers</span><span class="sxs-lookup"><span data-stu-id="c4991-126">Example 3: Get scheduled jobs on remote computers</span></span>

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

<span data-ttu-id="c4991-127">Met deze opdracht worden alle geplande taken opgehaald op de computers die worden vermeld in het Servers.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="c4991-127">This command gets all scheduled jobs on the computers that are listed in the Servers.txt file.</span></span>
<span data-ttu-id="c4991-128">De opdracht gebruikt de cmdlet Invoke-Command om op elke computer een opdracht **Get-ScheduleJob** uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c4991-128">The command uses the Invoke-Command cmdlet to run a **Get-ScheduleJob** command on each computer.</span></span>

### <span data-ttu-id="c4991-129">Voor beeld 4: door pipes geplande taken naar andere cmdlets</span><span class="sxs-lookup"><span data-stu-id="c4991-129">Example 4: Pipe scheduled jobs to other cmdlets</span></span>

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

<span data-ttu-id="c4991-130">Met deze opdracht worden de taak triggers van de geplande DailyBackup-en WeeklyBackup-taken opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4991-130">This command gets the job triggers of the DailyBackup and WeeklyBackup scheduled jobs.</span></span>
<span data-ttu-id="c4991-131">De cmdlet **Get-ScheduledJob** wordt gebruikt voor het ophalen van de geplande taken en de cmdlet Get-JobTrigger om de taak triggers van de geplande taken te krijgen.</span><span class="sxs-lookup"><span data-stu-id="c4991-131">It uses the **Get-ScheduledJob** cmdlet to get the scheduled jobs and the Get-JobTrigger cmdlet to get the job triggers of the scheduled jobs.</span></span>

## <span data-ttu-id="c4991-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4991-132">PARAMETERS</span></span>

### <span data-ttu-id="c4991-133">-Id</span><span class="sxs-lookup"><span data-stu-id="c4991-133">-Id</span></span>
<span data-ttu-id="c4991-134">Hiermee worden alleen de geplande taken met het opgegeven id-nummer (ID) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4991-134">Gets only the scheduled jobs with the specified identification number (ID).</span></span>
<span data-ttu-id="c4991-135">Voer een of meer Id's van de geplande taken op de computer in.</span><span class="sxs-lookup"><span data-stu-id="c4991-135">Enter one or more IDs of scheduled jobs on the computer.</span></span>
<span data-ttu-id="c4991-136">**Get-ScheduledJob** haalt standaard alle geplande taken op de computer op.</span><span class="sxs-lookup"><span data-stu-id="c4991-136">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4991-137">-Name</span><span class="sxs-lookup"><span data-stu-id="c4991-137">-Name</span></span>
<span data-ttu-id="c4991-138">Hiermee worden alleen de geplande taken met de opgegeven namen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4991-138">Gets only the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="c4991-139">Voer een of meer namen van geplande taken op de computer in.</span><span class="sxs-lookup"><span data-stu-id="c4991-139">Enter one or more names of scheduled jobs on the computer.</span></span>
<span data-ttu-id="c4991-140">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c4991-140">Wildcards are supported.</span></span>
<span data-ttu-id="c4991-141">**Get-ScheduledJob** haalt standaard alle geplande taken op de computer op.</span><span class="sxs-lookup"><span data-stu-id="c4991-141">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4991-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4991-142">CommonParameters</span></span>
<span data-ttu-id="c4991-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4991-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4991-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c4991-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4991-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="c4991-145">INPUTS</span></span>

### <span data-ttu-id="c4991-146">Geen</span><span class="sxs-lookup"><span data-stu-id="c4991-146">None</span></span>
<span data-ttu-id="c4991-147">U kunt geen pipe invoer naar **Get-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="c4991-147">You cannot pipe input to **Get-ScheduledJob**.</span></span>

## <span data-ttu-id="c4991-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c4991-148">OUTPUTS</span></span>

### <span data-ttu-id="c4991-149">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="c4991-149">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="c4991-150">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c4991-150">NOTES</span></span>

* <span data-ttu-id="c4991-151">Elke geplande taak wordt opgeslagen in een submap van de $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c4991-151">Each scheduled job is saved in a subdirectory of the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the local computer.</span></span> <span data-ttu-id="c4991-152">De submap krijgt de naam van de geplande taak en bevat het XML-bestand voor de geplande taak en records van de uitvoerings geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="c4991-152">The subdirectory is named for the scheduled job and contains the XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="c4991-153">Zie about_Scheduled_Jobs_Advanced voor meer informatie over geplande taken op schijf.</span><span class="sxs-lookup"><span data-stu-id="c4991-153">For more information about scheduled jobs on disk, see about_Scheduled_Jobs_Advanced.</span></span>
* <span data-ttu-id="c4991-154">Geplande taken die u in Windows Power Shell maakt, worden weer gegeven in taak planner in de map Library\Microsoft\Windows\PowerShell\ScheduledJobs van taak planner.</span><span class="sxs-lookup"><span data-stu-id="c4991-154">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs folder.</span></span> <span data-ttu-id="c4991-155">U kunt taak planner gebruiken om de geplande taak weer te geven en te bewerken.</span><span class="sxs-lookup"><span data-stu-id="c4991-155">You can use Task Scheduler to view and edit the scheduled job.</span></span>
* <span data-ttu-id="c4991-156">U kunt taak planner, het SchTasks.exe opdracht regel programma en de cmdlets van de taak planner gebruiken om geplande taken te beheren die u met de geplande taak-cmdlets maakt.</span><span class="sxs-lookup"><span data-stu-id="c4991-156">You can use Task Scheduler, the SchTasks.exe command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="c4991-157">U kunt de geplande taak-cmdlets echter niet gebruiken voor het beheren van taken die u maakt in taak planner.</span><span class="sxs-lookup"><span data-stu-id="c4991-157">However, you cannot use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

## <span data-ttu-id="c4991-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c4991-158">RELATED LINKS</span></span>

[<span data-ttu-id="c4991-159">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c4991-159">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="c4991-160">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c4991-160">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="c4991-161">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c4991-161">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="c4991-162">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c4991-162">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="c4991-163">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c4991-163">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="c4991-164">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c4991-164">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="c4991-165">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c4991-165">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="c4991-166">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c4991-166">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="c4991-167">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c4991-167">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="c4991-168">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c4991-168">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="c4991-169">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c4991-169">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="c4991-170">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c4991-170">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="c4991-171">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c4991-171">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="c4991-172">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c4991-172">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="c4991-173">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c4991-173">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="c4991-174">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c4991-174">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
