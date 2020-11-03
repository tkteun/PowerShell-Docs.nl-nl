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
# <a name="about-scheduled-jobs"></a>Over geplande taken

## <a name="short-description"></a>Korte beschrijving

Hierin worden geplande taken beschreven en wordt uitgelegd hoe u geplande taken in Power shell en in taak planner kunt gebruiken en beheren.

## <a name="long-description"></a>Lange beschrijving

Geplande power shell-taken zijn een nuttige hybride van Power shell-achtergrond taken en taak planner taken.

Net als Power shell-achtergrond taken worden geplande taken asynchroon uitgevoerd op de achtergrond. Exemplaren van geplande taken die zijn uitgevoerd, kunnen worden beheerd met behulp van de taak-cmdlets, zoals `Start-Job` ,, `Get-Job` `Stop-Job` en `Receive-Job` .

Geplande taken worden als taak planner-taken opgeslagen op schijf. U kunt de taken weer geven en beheren in Task Scheduler, inschakelen en uitschakelen als dat nodig is, ze uitvoeren of gebruiken als sjablonen, een eenmalige of terugkerende planning instellen voor het starten van de taken of voor waarden opgeven waaronder de taken worden gestart.

Daarnaast worden de resultaten van geplande-taak exemplaren opgeslagen op schijf in een gemakkelijk toegankelijke indeling, die een actief logboek van de taak uitvoer biedt. Geplande taken worden geleverd met een aangepaste set cmdlets voor het beheren ervan. Met de cmdlets kunt u geplande taken, taak triggers en taak opties maken, bewerken, beheren, uitschakelen en opnieuw inschakelen.

Deze uitgebreide en flexibele set hulpprogram ma's maken geplande taken een essentieel onderdeel van een groot aantal professionele Power shell-oplossingen.

De geplande taak-cmdlets zijn opgenomen in de **PSScheduledJob** -module die is geïnstalleerd met Power shell. Deze module werd geïntroduceerd in Power Shell 3,0 en werkt in Power Shell 3,0 en latere versies van Power shell. Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.

Zie [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)voor meer informatie over Power shell-achtergrond taken.

Zie [taak planner](/windows/desktop/TaskSchd/task-scheduler-reference)voor meer informatie over taak planner.

> [!NOTE]
> U kunt geplande power shell-taken weer geven en beheren in taak planner. De cmdlets voor Power shell-taken en geplande taken werken alleen voor geplande taken die in Power shell zijn gemaakt.

## <a name="quick-start"></a>Snel starten

In dit voor beeld wordt een geplande taak gemaakt die elke dag om 3:00 uur wordt gestart en de `Get-Process` cmdlet uitvoert. De taak wordt gestart, zelfs als de computer op een accu werkt.

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

De `Get-ScheduledJob` cmdlet haalt de geplande taken op de lokale computer op.

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

`Get-JobTrigger` Hiermee worden de taak triggers van **ProcessJob** opgehaald. De invoer parameters geven de geplande taak op, niet de trigger, omdat triggers worden opgeslagen in een geplande taak.

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

In dit voor beeld wordt de para meter **ContinueIfGoingOnBattery** van de `Set-ScheduledJob` cmdlet gebruikt om de eigenschap **StopIfGoingOnBatteries** van **ProcessJob** te wijzigen in **False**.

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

De `Get-ScheduledJob` cmdlet krijgt de geplande taak **ProcessJob** .

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

De `Get-Job` cmdlet haalt alle exemplaren op van de geplande **ProcessJob** -taak die tot nu toe is uitgevoerd. De `Get-Job` cmdlet haalt alleen geplande taken op wanneer de **PSScheduledJob** -module in de huidige sessie wordt geïmporteerd.

> [!TIP]
> U ziet dat u de geplande taak-cmdlets gebruikt om geplande taken te beheren, maar u kunt de taak-cmdlets gebruiken om exemplaren van geplande taken te beheren.

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

De `Receive-Job` cmdlet haalt de resultaten van het meest recente exemplaar van de geplande **ProcessJob** -taak (id = 51) op.

```powershell
Receive-Job -ID 51
```

Hoewel de `Receive-Job` opdracht de para meter **Keep** niet bevat, worden de resultaten van de taak op schijf opgeslagen totdat u ze verwijdert of het maximum aantal resultaten wordt overschreden.

De taak resultaten zijn niet meer beschikbaar in deze sessie, maar als u een nieuwe sessie start of een nieuw Power shell-venster opent, zijn de resultaten van de taak weer beschikbaar.

De volgende opdracht maakt gebruik van de para meter **definitienaam** van de `Start-Job` cmdlet om de geplande taak **ProcessJob** te starten.

Taken die zijn gestart met behulp van de `Start-Job` cmdlet zijn standaard-Power shell-achtergrond taken, geen exemplaren van de geplande taak. Net als bij alle achtergrond taken worden deze taken onmiddellijk gestart, niet onderhevig aan taak opties of worden beïnvloed door taak triggers, en de uitvoer ervan wordt niet opgeslagen in de uitvoermap van de geplande projectmap.

```powershell
Start-Job -DefinitionName ProcessJob
```

De `Unregister-ScheduledJob` cmdlet verwijdert de geplande taak **ProcessJob** en alle opgeslagen resultaten van de bijbehorende taak exemplaren.

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a>Concepten van geplande taken

Een geplande taak voert opdrachten of een script uit. Een geplande taak kan taak triggers bevatten waarmee de taak-en taak opties worden gestart die de voor waarden voor het uitvoeren van de taak instellen.

Een taak trigger start een geplande taak automatisch. Een taak trigger kan een eenmalige of terugkerende planning bevatten of een gebeurtenis opgeven, bijvoorbeeld wanneer een gebruiker zich aanmeldt of als Windows wordt gestart. Een geplande taak kan een of meer taak triggers hebben en u kunt taak triggers maken, toevoegen, inschakelen, uitschakelen en ophalen.

Taak triggers zijn optioneel. U kunt geplande taken onmiddellijk starten met behulp van de `Start-Job cmdlet` , of door de para meter **RunNow** toe te voegen aan de `Register-ScheduledJob` opdracht.

Met taak opties stelt u de voor waarden in voor het uitvoeren van een geplande taak. Elke geplande taak heeft één taak opties-object. U kunt taak opties objecten maken en bewerken en toevoegen aan een of meer geplande taken.

Telkens wanneer een geplande taak wordt gestart, wordt een taak exemplaar gemaakt. Gebruik de Power shell-taak-cmdlets om het taak exemplaar te bekijken en te beheren.

Geplande taken worden op schijf opgeslagen en gebruiken de werk-cmdlet, `Register` in plaats van `New` . De XML-bestanden bevinden zich op de lokale computer in de Directory `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .

In Power shell wordt een map voor elke geplande taak gemaakt en worden de opdracht opdrachten, taak triggers, taak opties en taak resultaten opgeslagen in de map geplande taak. Taak triggers en taak opties worden niet onafhankelijk op schijf opgeslagen.
Ze worden opgeslagen in de geplande XML-taak van elke geplande taak waarmee ze zijn verbonden.

Geplande taken, taak triggers en taak opties worden weer gegeven in Power shell als objecten.
De objecten zijn gekoppeld, waardoor ze eenvoudig kunnen worden gedetecteerd en gebruikt in opdrachten en scripts.

Geplande taken worden weer gegeven als **ScheduledJobDefinition** -objecten. Het **ScheduledJobDefinition** -object heeft een **JobTriggers** -eigenschap die de taak triggers van de geplande taak bevat en een **optie** -eigenschap die de taak opties bevat. De **ScheduledJobTriggers** -en **ScheduledJobOptions** -objecten die respectievelijk taak triggers en taak opties vertegenwoordigen, hebben elk een eigenschap **taak definitie** die de geplande taak bevat waarmee ze zijn verbonden. Deze recursieve interconnectie maakt het eenvoudig om de triggers en opties van een geplande taak te vinden en om de geplande taak waarmee een taak trigger of taak optie is gekoppeld, te zoeken, te scripteren en weer te geven.

## <a name="see-also"></a>Zie ook

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets

[Taak planner](/windows/desktop/TaskSchd/task-scheduler-reference)
