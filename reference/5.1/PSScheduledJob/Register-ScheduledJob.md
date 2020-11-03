---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250301"
---
# <span data-ttu-id="9e54a-103">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9e54a-103">Register-ScheduledJob</span></span>

## <span data-ttu-id="9e54a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9e54a-104">SYNOPSIS</span></span>
<span data-ttu-id="9e54a-105">Hiermee maakt u een geplande taak.</span><span class="sxs-lookup"><span data-stu-id="9e54a-105">Creates a scheduled job.</span></span>

## <span data-ttu-id="9e54a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9e54a-106">SYNTAX</span></span>

### <span data-ttu-id="9e54a-107">Script Block (standaard)</span><span class="sxs-lookup"><span data-stu-id="9e54a-107">ScriptBlock (Default)</span></span>

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9e54a-108">Bestandspad</span><span class="sxs-lookup"><span data-stu-id="9e54a-108">FilePath</span></span>

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9e54a-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9e54a-109">DESCRIPTION</span></span>

<span data-ttu-id="9e54a-110">De `Register-ScheduledJob` cmdlet maakt geplande taken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-110">The `Register-ScheduledJob` cmdlet creates scheduled jobs on the local computer.</span></span>

<span data-ttu-id="9e54a-111">Een geplande taak is een Windows Power shell-achtergrond taak die automatisch kan worden gestart in een eenmalige of terugkerende planning.</span><span class="sxs-lookup"><span data-stu-id="9e54a-111">A scheduled job is a Windows PowerShell background job that can be started automatically on a one-time or recurring schedule.</span></span> <span data-ttu-id="9e54a-112">Geplande taken worden op schijf opgeslagen en geregistreerd in taak planner.</span><span class="sxs-lookup"><span data-stu-id="9e54a-112">Scheduled jobs are stored on disk and registered in Task Scheduler.</span></span>
<span data-ttu-id="9e54a-113">De taken kunnen worden beheerd in taak planner of met behulp van de geplande taak cmdlets in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9e54a-113">The jobs can be managed in Task Scheduler or by using the Scheduled Job cmdlets in Windows PowerShell.</span></span>

<span data-ttu-id="9e54a-114">Wanneer een geplande taak wordt gestart, wordt een exemplaar van de geplande taak gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-114">When a scheduled job starts, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="9e54a-115">Geplande taak exemplaren zijn identiek aan Windows Power shell-achtergrond taken, behalve dat de resultaten worden opgeslagen op schijf.</span><span class="sxs-lookup"><span data-stu-id="9e54a-115">Scheduled job instances are identical to Windows PowerShell background jobs, except that the results are saved on disk.</span></span> <span data-ttu-id="9e54a-116">Gebruik de taak-cmdlets, zoals `Start-Job` , `Get-Job` en `Receive-Job` om de resultaten van de taak exemplaren te bekijken, weer te geven en op te halen.</span><span class="sxs-lookup"><span data-stu-id="9e54a-116">Use the Job cmdlets, such as `Start-Job`, `Get-Job`, and `Receive-Job` to start, view, and get the results of the job instances.</span></span>

<span data-ttu-id="9e54a-117">Gebruiken `Register-ScheduledJob` om een nieuwe geplande taak te maken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-117">Use `Register-ScheduledJob` to create a new scheduled job.</span></span> <span data-ttu-id="9e54a-118">Als u de opdrachten wilt opgeven die door de geplande taak worden uitgevoerd, gebruikt u de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="9e54a-118">To specify the commands that the scheduled job runs, use the **ScriptBlock** parameter.</span></span> <span data-ttu-id="9e54a-119">Als u een script wilt opgeven dat door de taak wordt uitgevoerd, gebruikt u de **filepath** -para meter.</span><span class="sxs-lookup"><span data-stu-id="9e54a-119">To specify a script that the job runs, use the **FilePath** parameter.</span></span>

<span data-ttu-id="9e54a-120">Windows Power shell: geplande taken gebruiken dezelfde taak triggers en taak opties die taak planner gebruikt voor geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-120">Windows PowerShell-scheduled jobs use the same job triggers and job options that Task Scheduler uses for scheduled tasks.</span></span>

<span data-ttu-id="9e54a-121">Met de **trigger** parameter van worden `Register-ScheduledJob` een of meer taak triggers toegevoegd waarmee de taak wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9e54a-121">The **Trigger** parameter of `Register-ScheduledJob` adds one or more job triggers that start the job.</span></span> <span data-ttu-id="9e54a-122">De **trigger** parameter is optioneel. u kunt triggers toevoegen wanneer u de geplande taak maakt, taak triggers later toevoegen, de para meter **RunNow** toevoegen om de taak onmiddellijk te starten. Gebruik de `Start-Job` cmdlet om de taak onmiddellijk te starten, of sla de niet-geactiveerde geplande taak op als een sjabloon voor andere taken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-122">The **Trigger** parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the **RunNow** parameter to start the job immediately, use the `Start-Job` cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="9e54a-123">Met de para meter **Options** kunt u de instellingen van de opties voor de geplande taak aanpassen.</span><span class="sxs-lookup"><span data-stu-id="9e54a-123">The **Options** parameter lets you customize the options settings for the scheduled job.</span></span> <span data-ttu-id="9e54a-124">De para meter **Options** is optioneel, zodat u taak opties kunt instellen wanneer u de geplande taak maakt of op elk gewenst moment wijzigt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-124">The **Options** parameter is optional, so you can set job options when you create the scheduled job or change them at any time.</span></span> <span data-ttu-id="9e54a-125">Omdat de instellingen van de taak kunnen voor komen dat de geplande taak wordt uitgevoerd, controleert u de taak opties en stelt u deze zorgvuldig in.</span><span class="sxs-lookup"><span data-stu-id="9e54a-125">Because job option settings can prevent the scheduled job from running, review the job options and set them carefully.</span></span>

<span data-ttu-id="9e54a-126">`Register-ScheduledJob` is een van een verzameling cmdlets voor taak planning in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9e54a-126">`Register-ScheduledJob` is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="9e54a-127">Zie de artikelen in de **PSScheduledJob** -module voor meer informatie over geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-127">For more information about Scheduled Jobs, see the About articles in the **PSScheduledJob** module.</span></span>
<span data-ttu-id="9e54a-128">Importeer de **PSScheduledJob** -module en typ vervolgens: `Get-Help about_Scheduled*` of Zie [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span><span class="sxs-lookup"><span data-stu-id="9e54a-128">Import the **PSScheduledJob** module and then type: `Get-Help about_Scheduled*` or see [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span></span>

<span data-ttu-id="9e54a-129">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9e54a-129">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="9e54a-130">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9e54a-130">EXAMPLES</span></span>

### <span data-ttu-id="9e54a-131">Voor beeld 1: een geplande taak maken</span><span class="sxs-lookup"><span data-stu-id="9e54a-131">Example 1: Create a scheduled job</span></span>

<span data-ttu-id="9e54a-132">In dit voor beeld wordt een geplande taak gemaakt op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-132">This example creates a scheduled job on the local computer.</span></span>

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

<span data-ttu-id="9e54a-133">`Register-ScheduledJob` maakt gebruik van de para meter **name** voor het maken van de taak **Archive-scripts** gepland.</span><span class="sxs-lookup"><span data-stu-id="9e54a-133">`Register-ScheduledJob` uses the **Name** parameter to create the **Archive-Scripts** scheduled job.</span></span>
<span data-ttu-id="9e54a-134">De para meter **script Block** wordt uitgevoerd `Get-ChildItem` die de `$home` map recursief doorzoekt naar `.ps1` bestanden.</span><span class="sxs-lookup"><span data-stu-id="9e54a-134">The **ScriptBlock** parameter runs `Get-ChildItem` that searches the `$home` directory recursively for `.ps1` files.</span></span> <span data-ttu-id="9e54a-135">Met de `Copy-Item` cmdlet worden de bestanden gekopieerd naar een map die is opgegeven door de para meter **Destination** .</span><span class="sxs-lookup"><span data-stu-id="9e54a-135">The `Copy-Item` cmdlet copies the files to a directory specified by the **Destination** parameter.</span></span>

<span data-ttu-id="9e54a-136">Omdat de geplande taak geen trigger bevat, wordt deze niet automatisch gestart.</span><span class="sxs-lookup"><span data-stu-id="9e54a-136">Because the scheduled job doesn't contain a trigger, it's not started automatically.</span></span> <span data-ttu-id="9e54a-137">U kunt taak triggers toevoegen met `Add-JobTrigger` , de `Start-Job` cmdlet gebruiken om de taak op aanvraag te starten of de geplande taak gebruiken als een sjabloon voor andere geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-137">You can add job triggers with `Add-JobTrigger`, use the `Start-Job` cmdlet to start the job on demand, or use the scheduled job as a template for other scheduled jobs.</span></span>

### <span data-ttu-id="9e54a-138">Voor beeld 2: een geplande taak maken met triggers en aangepaste opties</span><span class="sxs-lookup"><span data-stu-id="9e54a-138">Example 2: Create a scheduled job with triggers and custom options</span></span>

<span data-ttu-id="9e54a-139">In dit voor beeld ziet u hoe u een geplande taak maakt met een taak trigger en aangepaste taak opties.</span><span class="sxs-lookup"><span data-stu-id="9e54a-139">This example shows how to create a scheduled job that has a job trigger and custom job options.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

<span data-ttu-id="9e54a-140">De `$O` variabele slaat het taak optie object op dat de `New-ScheduledJobOption` cmdlet heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-140">The `$O` variable stores the job option object that the `New-ScheduledJobOption` cmdlet created.</span></span> <span data-ttu-id="9e54a-141">Met de opties wordt de geplande taak gestart, zelfs als de computer niet inactief is, wordt de computer geactiveerd om de taak uit te voeren, indien nodig, en kunnen meerdere exemplaren van de taak in een reeks worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-141">The options start the scheduled job even if the computer isn't idle, wakes the computer to run the job, if necessary, and allows multiple instances of the job to run in a series.</span></span>

<span data-ttu-id="9e54a-142">De `$T` variabele slaat het resultaat van de `New-JobTrigger` cmdlet op om een taak trigger te maken waarmee een taak elke andere maandag om 9:00 uur wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9e54a-142">The `$T` variable stores the result from the `New-JobTrigger` cmdlet to create job trigger that starts a job every other Monday at 9:00 PM.</span></span>

<span data-ttu-id="9e54a-143">De `$path` variabele slaat het pad naar het `UpdateVersion.ps1` script bestand op.</span><span class="sxs-lookup"><span data-stu-id="9e54a-143">The `$path` variable stores the path to the `UpdateVersion.ps1` script file.</span></span>

<span data-ttu-id="9e54a-144">`Register-ScheduledJob` maakt gebruik van de **naam** parameter om de geplande taak **UpdateVersion** te maken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-144">`Register-ScheduledJob` uses the **Name** paramter to create the **UpdateVersion** scheduled job.</span></span>
<span data-ttu-id="9e54a-145">De **filepath** para meter wordt gebruikt `$path` om het script op te geven dat door de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-145">The **FilePath** parameter uses `$path` to specify the script that the job runs.</span></span> <span data-ttu-id="9e54a-146">De para meter **ScheduledJobOption** maakt gebruik van de taak opties die zijn opgeslagen in `$O` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-146">The **ScheduledJobOption** parameter uses the job options stored in `$O`.</span></span> <span data-ttu-id="9e54a-147">De **trigger** parameter maakt gebruik van de taak triggers die zijn opgeslagen in `$T` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-147">The **Trigger** parameter uses the job triggers stored in `$T`.</span></span>

### <span data-ttu-id="9e54a-148">Voor beeld 3: hash-tabellen gebruiken om een trigger en geplande taak opties op te geven</span><span class="sxs-lookup"><span data-stu-id="9e54a-148">Example 3: Use hash tables to specify a trigger and scheduled job options</span></span>

<span data-ttu-id="9e54a-149">Dit voor beeld heeft hetzelfde effect als de opdracht in voor beeld 2.</span><span class="sxs-lookup"><span data-stu-id="9e54a-149">This example has the same effect as the command in Example 2.</span></span> <span data-ttu-id="9e54a-150">Er wordt een geplande taak gemaakt met behulp van hash-tabellen om de waarden van de **trigger** -en **ScheduledJobOption** -para meters op te geven.</span><span class="sxs-lookup"><span data-stu-id="9e54a-150">It creates a scheduled job, using hash tables to specify the values of the **Trigger** and **ScheduledJobOption** parameters.</span></span> <span data-ttu-id="9e54a-151">De `$O` variabelen en die `$T` in voor beeld 2 zijn gedefinieerd, worden vervangen door hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="9e54a-151">The `$O` and `$T`variables defined in Example 2 are replaced with hash tables.</span></span>

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### <span data-ttu-id="9e54a-152">Voor beeld 4: geplande taken maken op externe computers</span><span class="sxs-lookup"><span data-stu-id="9e54a-152">Example 4: Create scheduled jobs on remote computers</span></span>

<span data-ttu-id="9e54a-153">In dit voor beeld wordt de geplande taak **EnergyData** op meerdere externe computers gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-153">In this example, the **EnergyData** scheduled job is created on multiple remote computers.</span></span> <span data-ttu-id="9e54a-154">Met de geplande taak wordt een script uitgevoerd waarmee onbewerkte gegevens worden verzameld en opgeslagen in een actief logboek op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-154">The scheduled job runs a script that gathers raw data and saves it in a running log on the remote computer.</span></span>

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

<span data-ttu-id="9e54a-155">De `$Cred` variabele slaat referenties op in een **PSCredential** -object voor een gebruiker met machtigingen voor het maken van geplande taken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-155">The `$Cred` variable stores credentials in a **PSCredential** object for a user with permissions to create scheduled jobs.</span></span> <span data-ttu-id="9e54a-156">De `$O` variabele bevat de taak opties die zijn gemaakt met `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-156">The `$O` variable stores the job options created with `New-ScheduledJobOption`.</span></span> <span data-ttu-id="9e54a-157">De `$T` variabele bevat de taak triggers die zijn gemaakt met `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-157">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="9e54a-158">De `Invoke-Command` cmdlet gebruikt de para meter **ComputerName** om een lijst met server namen uit het bestand op te halen `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-158">The `Invoke-Command` cmdlet uses the **ComputerName** parameter to get a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="9e54a-159">De **referentie** parameter haalt het referentie object op dat is opgeslagen in `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-159">The **Credential** parameter gets the credential object stored in `$Cred`.</span></span>
<span data-ttu-id="9e54a-160">De para meter **script Block** voert een `Register-ScheduledJob` opdracht op de computers in het `Servers.txt` bestand uit.</span><span class="sxs-lookup"><span data-stu-id="9e54a-160">The **ScriptBlock** parameter runs a `Register-ScheduledJob` command on the computers in the `Servers.txt` file.</span></span>

<span data-ttu-id="9e54a-161">De para meters voor `Register-ScheduledJob` worden gedefinieerd door `$params` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-161">The parameters for `Register-ScheduledJob` are defined by `$params`.</span></span> <span data-ttu-id="9e54a-162">De **naam** parameters geeft aan dat de taak de naam **Get-EnergyData** heeft op elke externe computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-162">The **Name** parameters specifies the job is named **Get-EnergyData** on each remote computer.</span></span> <span data-ttu-id="9e54a-163">Het **bestandspad** bevat de locatie van het `EnergyData.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="9e54a-163">**FilePath** provides the location of the `EnergyData.ps1` script.</span></span> <span data-ttu-id="9e54a-164">Het script bevindt zich op een bestands server die beschikbaar is voor alle deelnemende computers. De taak wordt uitgevoerd volgens het schema dat is opgegeven door de taak triggers in `$T` en de taak opties in `$O` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-164">The script is located on a file server that is available to all participating computers.The job runs on the schedule specified by the job triggers in `$T` and the job options in `$O`.</span></span>

<span data-ttu-id="9e54a-165">`Register-ScheduledJob @params`Met de opdracht wordt de geplande taak gemaakt met de para meters uit het script blok.</span><span class="sxs-lookup"><span data-stu-id="9e54a-165">The `Register-ScheduledJob @params` command creates the scheduled job with the parameters from the script block.</span></span>

### <span data-ttu-id="9e54a-166">Voor beeld 5: een geplande taak maken waarmee een script wordt uitgevoerd op externe computers</span><span class="sxs-lookup"><span data-stu-id="9e54a-166">Example 5: Create a scheduled job that runs a script on remote computers</span></span>

<span data-ttu-id="9e54a-167">In dit voor beeld wordt de geplande **CollectEnergyData** -taak op de lokale computer gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-167">This example creates the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="9e54a-168">De taak wordt op meerdere externe computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-168">The job runs on multiple remote computers.</span></span>

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

<span data-ttu-id="9e54a-169">De `$Admin` variabele bevat referenties voor een gebruiker met machtigingen voor het uitvoeren van de opdrachten in een **PSCredential** -object.</span><span class="sxs-lookup"><span data-stu-id="9e54a-169">The `$Admin` variable stores credentials for a user with permissions to run the commands in a **PSCredential** object.</span></span> <span data-ttu-id="9e54a-170">De `$T` variabele bevat de taak triggers die zijn gemaakt met `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-170">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="9e54a-171">De `Register-ScheduledJob` cmdlet gebruikt de para meter **name** om de geplande taak **CollectEnergyData** te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-171">The `Register-ScheduledJob` cmdlet uses the **Name** parameter to create the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="9e54a-172">De **trigger** parameter specificeert de taak triggers in `$T` en de para meter **MaxResultCount** verhoogt het aantal opgeslagen resultaten tot 99.</span><span class="sxs-lookup"><span data-stu-id="9e54a-172">The **Trigger** parameter specifies the job triggers in `$T` and the **MaxResultCount** parameter increases the number of saved results to 99.</span></span>

<span data-ttu-id="9e54a-173">Met de para meter **script Block** worden de `Invoke-Command` para meters gedefinieerd met `$params` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-173">The **ScriptBlock** parameter defines the `Invoke-Command` parameters with `$params`.</span></span> <span data-ttu-id="9e54a-174">De para meter **AsJob** maakt het object voor de achtergrond taak op de lokale computer, zelfs als het `Energydata.ps1` script wordt uitgevoerd op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="9e54a-174">The **AsJob** parameter creates the background job object on the local computer, even though the `Energydata.ps1` script runs on the remote computers.</span></span> <span data-ttu-id="9e54a-175">De para meter **ComputerName** haalt een lijst met server namen uit het `Servers.txt` bestand op.</span><span class="sxs-lookup"><span data-stu-id="9e54a-175">The **ComputerName** parameter gets a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="9e54a-176">De **referentie** parameter geeft u een gebruikers account op dat gemachtigd is om scripts uit te voeren op de externe computers.</span><span class="sxs-lookup"><span data-stu-id="9e54a-176">The **Credential** parameter specifies a user account that has permission to run scripts on the remote computers.</span></span> <span data-ttu-id="9e54a-177">En de **verificatie** parameter geeft de waarde **CredSSP** op om gedelegeerde referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="9e54a-177">And, the **Authentication** parameter specifies a value of **CredSSP** to allow delegated credentials.</span></span>

<span data-ttu-id="9e54a-178">De `Invoke-Command @params` opdracht wordt uitgevoerd met de para meters uit het script blok.</span><span class="sxs-lookup"><span data-stu-id="9e54a-178">The `Invoke-Command @params` runs the command with the parameters from the script block.</span></span>

## <span data-ttu-id="9e54a-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e54a-179">PARAMETERS</span></span>

### <span data-ttu-id="9e54a-180">-Argument List</span><span class="sxs-lookup"><span data-stu-id="9e54a-180">-ArgumentList</span></span>

<span data-ttu-id="9e54a-181">Hiermee geeft u waarden op voor de para meters van het script dat is opgegeven met de para meter **filepath** of voor de opdracht die is opgegeven door de para meter **script Block** .</span><span class="sxs-lookup"><span data-stu-id="9e54a-181">Specifies values for the parameters of the script that is specified by the **FilePath** parameter or for the command that is specified by the **ScriptBlock** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-182">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="9e54a-182">-Authentication</span></span>

<span data-ttu-id="9e54a-183">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="9e54a-183">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="9e54a-184">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="9e54a-184">The default value is Default.</span></span>

<span data-ttu-id="9e54a-185">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9e54a-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9e54a-186">Standaard</span><span class="sxs-lookup"><span data-stu-id="9e54a-186">Default</span></span>
- <span data-ttu-id="9e54a-187">Basic</span><span class="sxs-lookup"><span data-stu-id="9e54a-187">Basic</span></span>
- <span data-ttu-id="9e54a-188">CredSSP</span><span class="sxs-lookup"><span data-stu-id="9e54a-188">Credssp</span></span>
- <span data-ttu-id="9e54a-189">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="9e54a-189">Digest</span></span>
- <span data-ttu-id="9e54a-190">Kerberos</span><span class="sxs-lookup"><span data-stu-id="9e54a-190">Kerberos</span></span>
- <span data-ttu-id="9e54a-191">Negotiate</span><span class="sxs-lookup"><span data-stu-id="9e54a-191">Negotiate</span></span>
- <span data-ttu-id="9e54a-192">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="9e54a-192">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="9e54a-193">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="9e54a-193">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="9e54a-194">CredSSP-verificatie (Credential Security service provider), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="9e54a-194">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="9e54a-195">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="9e54a-195">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="9e54a-196">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="9e54a-196">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9e54a-197">-Confirm</span></span>

<span data-ttu-id="9e54a-198">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9e54a-198">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-199">-Credential</span><span class="sxs-lookup"><span data-stu-id="9e54a-199">-Credential</span></span>

<span data-ttu-id="9e54a-200">Hiermee geeft u een gebruikers account op dat gemachtigd is om de geplande taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9e54a-200">Specifies a user account that has permission to run the scheduled job.</span></span> <span data-ttu-id="9e54a-201">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9e54a-201">The default is the current user.</span></span>

<span data-ttu-id="9e54a-202">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in, bijvoorbeeld een van de `Get-Credential` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9e54a-202">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9e54a-203">Als u alleen een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="9e54a-203">If you enter only a user name, you're prompted for a password.</span></span>

<span data-ttu-id="9e54a-204">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="9e54a-204">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9e54a-205">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="9e54a-205">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-206">-FilePath</span><span class="sxs-lookup"><span data-stu-id="9e54a-206">-FilePath</span></span>

<span data-ttu-id="9e54a-207">Hiermee geeft u een script op dat door de geplande taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-207">Specifies a script that the scheduled job runs.</span></span> <span data-ttu-id="9e54a-208">Geef het pad op naar een `.ps1` bestand op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-208">Enter the path to a `.ps1` file on the local computer.</span></span> <span data-ttu-id="9e54a-209">Als u standaard waarden voor de script parameters wilt opgeven, gebruikt u de para meter **argument List** .</span><span class="sxs-lookup"><span data-stu-id="9e54a-209">To specify default values for the script parameters, use the **ArgumentList** parameter.</span></span>
<span data-ttu-id="9e54a-210">Elke `Register-ScheduledJob` opdracht moet de para meters **script Block** of **filepath** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-210">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-211">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="9e54a-211">-InitializationScript</span></span>

<span data-ttu-id="9e54a-212">Hiermee geeft u het volledige pad naar een Windows Power shell-script ( `.ps1` ) op.</span><span class="sxs-lookup"><span data-stu-id="9e54a-212">Specifies the fully qualified path to a Windows PowerShell script (`.ps1`).</span></span> <span data-ttu-id="9e54a-213">Het initialisatie script wordt uitgevoerd in de sessie die is gemaakt voor de achtergrond taak vóór de opdrachten die zijn opgegeven door de para meter **script Block** of het script dat is opgegeven door de para meter **filepath** .</span><span class="sxs-lookup"><span data-stu-id="9e54a-213">The initialization script runs in the session that is created for the background job before the commands that are specified by the **ScriptBlock** parameter or the script that is specified by the **FilePath** parameter.</span></span> <span data-ttu-id="9e54a-214">U kunt het initialisatie script gebruiken om de sessie te configureren, zoals het toevoegen van bestanden, functies of aliassen, het maken van mappen of het controleren op vereisten.</span><span class="sxs-lookup"><span data-stu-id="9e54a-214">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="9e54a-215">Als u een script wilt opgeven dat de opdrachten van de primaire opdracht uitvoert, gebruikt u de **filepath** -para meter.</span><span class="sxs-lookup"><span data-stu-id="9e54a-215">To specify a script that runs the primary job commands, use the **FilePath** parameter.</span></span>

<span data-ttu-id="9e54a-216">Als het initialisatie script een fout genereert, zelfs een niet-afsluit fout, wordt het huidige exemplaar van de geplande taak niet uitgevoerd en is de status **mislukt**.</span><span class="sxs-lookup"><span data-stu-id="9e54a-216">If the initialization script generates an error, even a non-terminating error, the current instance of the scheduled job doesn't run and its status is **Failed**.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-217">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="9e54a-217">-MaxResultCount</span></span>

<span data-ttu-id="9e54a-218">Hiermee geeft u op hoeveel items van de taak resultaat voor de geplande taak worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="9e54a-218">Specifies how many job result entries are maintained for the scheduled job.</span></span> <span data-ttu-id="9e54a-219">De standaard waarde is 32.</span><span class="sxs-lookup"><span data-stu-id="9e54a-219">The default value is 32.</span></span>

<span data-ttu-id="9e54a-220">Windows Power shell slaat de uitvoerings geschiedenis en resultaten van elk geactiveerd exemplaar van de geplande taak op schijf op.</span><span class="sxs-lookup"><span data-stu-id="9e54a-220">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span> <span data-ttu-id="9e54a-221">De waarde van deze para meter bepaalt het aantal taak exemplaar resultaten dat voor deze geplande taak wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="9e54a-221">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span> <span data-ttu-id="9e54a-222">Wanneer het aantal taak exemplaren deze waarde overschrijdt, worden de resultaten van het oudste taak exemplaar door Windows Power shell verwijderd om ruimte te maken voor de resultaten van het nieuwste taak exemplaar.</span><span class="sxs-lookup"><span data-stu-id="9e54a-222">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="9e54a-223">De geschiedenis van de taak uitvoering en taak resultaten worden opgeslagen in de `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span><span class="sxs-lookup"><span data-stu-id="9e54a-223">The job execution history and job results are saved in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span></span>
<span data-ttu-id="9e54a-224">directory's op de computer waarop de taak is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-224">directories on the computer on which the job is created.</span></span> <span data-ttu-id="9e54a-225">Als u de uitvoerings geschiedenis wilt zien, gebruikt u de `Get-Job` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e54a-225">To see the execution history, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="9e54a-226">Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-226">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="9e54a-227">Met de para meter **MaxResultCount** wordt de waarde van de eigenschap ExecutionHistoryLength van de geplande taak ingesteld.</span><span class="sxs-lookup"><span data-stu-id="9e54a-227">The **MaxResultCount** parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="9e54a-228">Als u de huidige uitvoerings geschiedenis en taak resultaten wilt verwijderen, gebruikt u de para meter **ClearExecutionHistory** van de `Set-ScheduledJob` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e54a-228">To delete the current execution history and job results, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-229">-Name</span><span class="sxs-lookup"><span data-stu-id="9e54a-229">-Name</span></span>

<span data-ttu-id="9e54a-230">Hiermee geeft u een naam op voor de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="9e54a-230">Specifies a name for the scheduled job.</span></span> <span data-ttu-id="9e54a-231">De naam wordt ook gebruikt voor alle gestarte exemplaren van de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="9e54a-231">The name is also used for all started instances of the scheduled job.</span></span> <span data-ttu-id="9e54a-232">De naam moet uniek zijn op de computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-232">The name must be unique on the computer.</span></span> <span data-ttu-id="9e54a-233">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="9e54a-233">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-234">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="9e54a-234">-RunAs32</span></span>

<span data-ttu-id="9e54a-235">De geplande taak wordt uitgevoerd in een 32-bits proces.</span><span class="sxs-lookup"><span data-stu-id="9e54a-235">Runs the scheduled job in a 32-bit process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-236">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="9e54a-236">-RunEvery</span></span>

<span data-ttu-id="9e54a-237">Wordt gebruikt om op te geven hoe vaak de taak moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-237">Used to specify how often to run the job.</span></span> <span data-ttu-id="9e54a-238">Gebruik deze optie bijvoorbeeld om elke 15 minuten een taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9e54a-238">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-239">-RunNow</span><span class="sxs-lookup"><span data-stu-id="9e54a-239">-RunNow</span></span>

<span data-ttu-id="9e54a-240">Start een taak onmiddellijk, zodra de `Register-ScheduledJob` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-240">Starts a job immediately, as soon as the `Register-ScheduledJob` cmdlet is run.</span></span> <span data-ttu-id="9e54a-241">Met deze para meter is het niet nodig om taak planner te activeren om een Windows Power shell-script uit te voeren direct na de registratie en hoeven gebruikers geen trigger te maken die een begin datum en-tijd opgeeft.</span><span class="sxs-lookup"><span data-stu-id="9e54a-241">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and doesn't require users to create a trigger that specifies a starting date and time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-242">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9e54a-242">-ScheduledJobOption</span></span>

<span data-ttu-id="9e54a-243">Opties instellen voor de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="9e54a-243">Sets options for the scheduled job.</span></span> <span data-ttu-id="9e54a-244">Voer een **ScheduledJobOptions** -object in, zoals een, dat u maakt met behulp van de `New-ScheduledJobOption` cmdlet of een hash-tabel waarde.</span><span class="sxs-lookup"><span data-stu-id="9e54a-244">Enter a **ScheduledJobOptions** object, such as one that you create by using the `New-ScheduledJobOption` cmdlet, or a hash table value.</span></span>

<span data-ttu-id="9e54a-245">U kunt opties voor een geplande taak instellen wanneer u de plannings taak registreert of de- `Set-ScheduledJobOption` `Set-ScheduledJob` cmdlets gebruikt om de opties te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9e54a-245">You can set options for a scheduled job when you register the schedule job or use the `Set-ScheduledJobOption` or `Set-ScheduledJob` cmdlets to change the options.</span></span>

<span data-ttu-id="9e54a-246">Veel van de opties en hun standaard waarden bepalen of en wanneer een geplande taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-246">Many of the options and their default values determine whether and when a scheduled job runs.</span></span> <span data-ttu-id="9e54a-247">Controleer deze opties voordat u een taak plant.</span><span class="sxs-lookup"><span data-stu-id="9e54a-247">Be sure to review these options before scheduling a job.</span></span> <span data-ttu-id="9e54a-248">Zie voor een beschrijving van de opties voor geplande taken, met inbegrip van de standaard waarden `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="9e54a-248">For a description of the scheduled job options, including the default values, see `New-ScheduledJobOption`.</span></span>

<span data-ttu-id="9e54a-249">Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels.</span><span class="sxs-lookup"><span data-stu-id="9e54a-249">To submit a hash table, use the following keys.</span></span> <span data-ttu-id="9e54a-250">In de volgende hash-tabel worden de sleutels weer gegeven met de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="9e54a-250">In the following hash table, the keys are shown with their default values.</span></span>

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-251">-Script Block</span><span class="sxs-lookup"><span data-stu-id="9e54a-251">-ScriptBlock</span></span>

<span data-ttu-id="9e54a-252">Hiermee geeft u de opdrachten op die door de geplande taak worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-252">Specifies the commands that the scheduled job runs.</span></span> <span data-ttu-id="9e54a-253">Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-253">Enclose the commands in curly braces (`{}`) to create a script block.</span></span> <span data-ttu-id="9e54a-254">Als u standaard waarden voor opdracht parameters wilt opgeven, gebruikt u de para meter **argument List** .</span><span class="sxs-lookup"><span data-stu-id="9e54a-254">To specify default values for command parameters, use the **ArgumentList** parameter.</span></span>

<span data-ttu-id="9e54a-255">Elke `Register-ScheduledJob` opdracht moet de para meters **script Block** of **filepath** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-255">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-256">-Trigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-256">-Trigger</span></span>

<span data-ttu-id="9e54a-257">Hiermee geeft u de triggers voor de geplande taak op.</span><span class="sxs-lookup"><span data-stu-id="9e54a-257">Specifies the triggers for the scheduled job.</span></span> <span data-ttu-id="9e54a-258">Voer een of meer **ScheduledJobTrigger** -objecten in, zoals de objecten die de `New-JobTrigger` cmdlet retourneert of een hash-tabel met sleutels en waarden van de taak trigger.</span><span class="sxs-lookup"><span data-stu-id="9e54a-258">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the `New-JobTrigger` cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="9e54a-259">Met een taak trigger wordt de taak plannen gestart.</span><span class="sxs-lookup"><span data-stu-id="9e54a-259">A job trigger starts the schedule job.</span></span> <span data-ttu-id="9e54a-260">Met de trigger kan een eenmalige of terugkerende geplande taak of een gebeurtenis worden opgegeven, bijvoorbeeld wanneer een gebruiker zich aanmeldt of als Windows wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="9e54a-260">The trigger can specify a one-time or recurring scheduled or an event, such as when a user logs on or Windows starts.</span></span>

<span data-ttu-id="9e54a-261">De **trigger** parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="9e54a-261">The **Trigger** parameter is optional.</span></span> <span data-ttu-id="9e54a-262">U kunt een trigger toevoegen wanneer u de geplande taak maakt, de `Add-JobTrigger` `Set-JobTrigger` cmdlets, of gebruiken `Set-ScheduledJob` om taak triggers later toe te voegen of te wijzigen, of gebruik de `Start-Job` cmdlet om de geplande taak onmiddellijk te starten.</span><span class="sxs-lookup"><span data-stu-id="9e54a-262">You can add a trigger when you create the scheduled job, use the `Add-JobTrigger`, `Set-JobTrigger`, or `Set-ScheduledJob` cmdlets to add or change job triggers later, or use the `Start-Job` cmdlet to start the scheduled job immediately.</span></span> <span data-ttu-id="9e54a-263">U kunt ook een geplande taak maken en onderhouden zonder een trigger die als sjabloon wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-263">You can also create and maintain a scheduled job without a trigger that is used as a template.</span></span>

<span data-ttu-id="9e54a-264">Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="9e54a-264">To submit a hash table, use the following keys:</span></span>

- <span data-ttu-id="9e54a-265">**Frequentie** : dagelijks, wekelijks, AtStartup, AtLogon</span><span class="sxs-lookup"><span data-stu-id="9e54a-265">**Frequency** : Daily, Weekly, AtStartup, AtLogon</span></span>
- <span data-ttu-id="9e54a-266">**Op** : een geldige tijd reeks</span><span class="sxs-lookup"><span data-stu-id="9e54a-266">**At** : Any valid time string</span></span>
- <span data-ttu-id="9e54a-267">**DaysOfWeek** -een combi natie van namen van dagen</span><span class="sxs-lookup"><span data-stu-id="9e54a-267">**DaysOfWeek** - Any combination of day names</span></span>
- <span data-ttu-id="9e54a-268">**Interval** -een wille keurig geldig frequentie-interval</span><span class="sxs-lookup"><span data-stu-id="9e54a-268">**Interval** - Any valid frequency interval</span></span>
- <span data-ttu-id="9e54a-269">**RandomDelay** : een geldige time span-teken reeks</span><span class="sxs-lookup"><span data-stu-id="9e54a-269">**RandomDelay** : Any valid timespan string</span></span>
- <span data-ttu-id="9e54a-270">**Gebruiker** : een geldige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9e54a-270">**User** : Any valid user.</span></span> <span data-ttu-id="9e54a-271">Wordt alleen gebruikt met de AtLogon-frequentie waarde</span><span class="sxs-lookup"><span data-stu-id="9e54a-271">Used only with the AtLogon frequency value</span></span>

<span data-ttu-id="9e54a-272">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9e54a-272">For example:</span></span>

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9e54a-273">-WhatIf</span></span>

<span data-ttu-id="9e54a-274">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9e54a-274">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9e54a-275">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e54a-275">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e54a-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e54a-276">CommonParameters</span></span>

<span data-ttu-id="9e54a-277">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9e54a-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e54a-278">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9e54a-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e54a-279">INVOER</span><span class="sxs-lookup"><span data-stu-id="9e54a-279">INPUTS</span></span>

### <span data-ttu-id="9e54a-280">Geen</span><span class="sxs-lookup"><span data-stu-id="9e54a-280">None</span></span>

<span data-ttu-id="9e54a-281">U kunt de pijp lijn geen invoer naar deze cmdlet sturen.</span><span class="sxs-lookup"><span data-stu-id="9e54a-281">You can't send input down the pipeline to this cmdlet.</span></span>

## <span data-ttu-id="9e54a-282">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9e54a-282">OUTPUTS</span></span>

### <span data-ttu-id="9e54a-283">Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="9e54a-283">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="9e54a-284">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9e54a-284">NOTES</span></span>

<span data-ttu-id="9e54a-285">Elke geplande taak wordt opgeslagen in een submap van de `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e54a-285">Each scheduled job is saved in a subdirectory of the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span>
<span data-ttu-id="9e54a-286">De submap heeft de naam voor de geplande taak en bevat een XML-bestand voor de geplande taak en records van de uitvoerings geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="9e54a-286">The subdirectory is named for the scheduled job and contains an XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="9e54a-287">Zie [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md)voor meer informatie over geplande taken op schijf.</span><span class="sxs-lookup"><span data-stu-id="9e54a-287">For more information about scheduled jobs on disk, see [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).</span></span>

<span data-ttu-id="9e54a-288">Geplande taken die u in Windows Power Shell maakt, worden weer gegeven in taak planner in de `Library\Microsoft\Windows\PowerShell\ScheduledJobs` map taak planner.</span><span class="sxs-lookup"><span data-stu-id="9e54a-288">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler `Library\Microsoft\Windows\PowerShell\ScheduledJobs` folder.</span></span> <span data-ttu-id="9e54a-289">U kunt taak planner gebruiken om de geplande taak weer te geven en te bewerken.</span><span class="sxs-lookup"><span data-stu-id="9e54a-289">You can use Task Scheduler to view and edit the scheduled job.</span></span>

<span data-ttu-id="9e54a-290">U kunt taak planner, het **schtasks.exe** opdracht regel programma en de cmdlets van de taak planner gebruiken om geplande taken te beheren die u met de geplande taak-cmdlets maakt.</span><span class="sxs-lookup"><span data-stu-id="9e54a-290">You can use Task Scheduler, the **schtasks.exe** command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="9e54a-291">U kunt de geplande taak-cmdlets echter niet gebruiken voor het beheren van taken die u maakt in taak planner.</span><span class="sxs-lookup"><span data-stu-id="9e54a-291">However, you can't use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

<span data-ttu-id="9e54a-292">Als een geplande taak mislukt, wordt een fout bericht geretourneerd door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9e54a-292">If a scheduled job command fails, Windows PowerShell returns an error message.</span></span> <span data-ttu-id="9e54a-293">Als de taak echter mislukt wanneer taak planner probeert deze uit te voeren, is de fout niet beschikbaar in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9e54a-293">However, if the job fails when Task Scheduler tries to run it, the error isn't available to Windows PowerShell.</span></span>

<span data-ttu-id="9e54a-294">Als een geplande taak niet wordt uitgevoerd, gebruikt u de volgende methoden om de reden te achterhalen:</span><span class="sxs-lookup"><span data-stu-id="9e54a-294">If a scheduled job doesn't run, use the following methods to find the reason:</span></span>

- <span data-ttu-id="9e54a-295">Controleer of de taak trigger juist is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="9e54a-295">Verify that the job trigger is set properly.</span></span>
  - <span data-ttu-id="9e54a-296">Controleer of aan de voor waarden die zijn ingesteld in de taak opties is voldaan.</span><span class="sxs-lookup"><span data-stu-id="9e54a-296">Verify that the conditions set in the job options are satisfied.</span></span>
- <span data-ttu-id="9e54a-297">Controleer of het gebruikers account waarmee de taak wordt uitgevoerd, gemachtigd is om de opdrachten of scripts in de taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9e54a-297">Verify that the user account under which the job runs has permission to run the commands or scripts in the job.</span></span>
- <span data-ttu-id="9e54a-298">Controleer de geschiedenis van de taak planner op fouten.</span><span class="sxs-lookup"><span data-stu-id="9e54a-298">Check the Task Scheduler history for errors.</span></span>
- <span data-ttu-id="9e54a-299">Controleer het gebeurtenis logboek van de taak planner op fouten.</span><span class="sxs-lookup"><span data-stu-id="9e54a-299">Check the Task Scheduler event log for errors.</span></span>

<span data-ttu-id="9e54a-300">Zie [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9e54a-300">For more information, see [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).</span></span>

## <span data-ttu-id="9e54a-301">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9e54a-301">RELATED LINKS</span></span>

[<span data-ttu-id="9e54a-302">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-302">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="9e54a-303">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-303">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="9e54a-304">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9e54a-304">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="9e54a-305">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-305">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="9e54a-306">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9e54a-306">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="9e54a-307">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-307">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="9e54a-308">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9e54a-308">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="9e54a-309">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9e54a-309">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="9e54a-310">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-310">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="9e54a-311">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9e54a-311">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="9e54a-312">REGI ster-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9e54a-312">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="9e54a-313">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-313">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="9e54a-314">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9e54a-314">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="9e54a-315">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9e54a-315">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="9e54a-316">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9e54a-316">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="9e54a-317">Registratie ongedaan maken-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9e54a-317">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
