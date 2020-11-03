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
# <a name="about-scheduled-jobs-basics"></a>Over de basis beginselen van geplande taken

## <a name="short-description"></a>Korte beschrijving

Hierin wordt uitgelegd hoe u geplande taken maakt en beheert.

## <a name="long-description"></a>Lange beschrijving

Dit document bevat informatie over het uitvoeren van basis taken voor het maken en beheren van geplande taken. Zie [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)voor meer informatie over geavanceerde taken.

Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.

## <a name="how-to-create-a-scheduled-job"></a>Een geplande taak maken

Als u een geplande taak wilt maken, gebruikt u de `Register-ScheduledJob` cmdlet. De cmdlet vereist een naam en de opdrachten of het script dat door de taak wordt uitgevoerd. U kunt de taak onmiddellijk uitvoeren door de para meter **RunNow** toe te voegen, of een taak trigger te maken en taak opties in te stellen wanneer u de taak maakt of een bestaande taak bewerkt.

Als u een taak wilt maken waarmee een script wordt uitgevoerd, gebruikt u de **filepath** para meter om het pad naar het script bestand op te geven. Als u een taak wilt maken die opdrachten uitvoert, gebruikt u de para meter **script Block** .

De `Register-ScheduledJob` cmdlet maakt de **ProcessJob** , waarmee een opdracht wordt uitgevoerd `Get-Process` . Deze geplande taak heeft de standaard taak opties en geen taak trigger.

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a>Een taak trigger maken

Taak triggers starten een geplande taak automatisch. Een taak trigger kan een eenmalige of terugkerende planning of een gebeurtenis zijn, zoals wanneer een gebruiker zich aanmeldt of als Windows wordt gestart. Elke taak kan nul, één of meerdere taak triggers hebben.

Als u een taak trigger wilt maken, gebruikt u de `New-JobTrigger` cmdlet. Met de volgende opdracht wordt een taak trigger gemaakt waarmee elke maandag en donderdag om 5:00 uur een taak wordt gestart.
Met de opdracht wordt de taak trigger opgeslagen in de `$T` variabele.

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

Taak triggers zijn optioneel. U kunt op elk gewenst moment een geplande taak starten door de para meter **RunNow** toe te voegen aan uw `Register-ScheduledJob` opdracht of door de- `Start-Job` cmdlets te gebruiken.

## <a name="how-to-add-a-job-trigger"></a>Een taak trigger toevoegen

Wanneer u een taak trigger aan een geplande taak toevoegt, wordt de taak trigger toegevoegd aan het XML-bestand van de geplande taak voor de geplande taak en wordt het onderdeel van de geplande taak.

U kunt een taak trigger toevoegen aan een geplande taak wanneer u de geplande taak maakt of een bestaande taak bewerkt. U kunt de taak trigger van een geplande taak op elk gewenst moment wijzigen.

Power shell gebruikt enkele van dezelfde taak triggers die taak planner gebruikt. Zie het Help-onderwerp voor de cmdlet [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) voor meer informatie over taak triggers.

In het volgende voor beeld wordt splatting gebruikt om `$JobParms` de parameter waarden te maken die worden door gegeven aan de `Register-ScheduledJob` cmdlet. Zie [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.
`Register-ScheduledJob`Hiermee `@JobParms` maakt u een geplande taak. De **trigger** parameter wordt gebruikt om de taak trigger in de variabele op te geven `$T` .

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

U kunt op elk gewenst moment ook een taak trigger toevoegen aan een bestaande geplande taak. De `Add-JobTrigger` cmdlet voegt de taak trigger in de `$T` variabele toe aan de geplande taak **ProcessJob** .

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

Als gevolg hiervan start de taak trigger de **ProcessJob** automatisch elke maandag en donderdag om 5:00 uur.

## <a name="how-to-get-a-job-trigger"></a>Een taak trigger ophalen

Gebruik de cmdlet om de taak trigger van een geplande taak op te halen `Get-JobTrigger` . Gebruik de para meters **name** , **id** en **input object** om de geplande taak op te geven, niet de taak trigger.

`Get-JobTrigger` Hiermee wordt de taak trigger van de **ProcessJob** opgehaald.

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a>Taak opties maken

Taak opties bepalen de voor waarden voor het starten en uitvoeren van de taak. Elke taak heeft de standaard taak opties tenzij u deze wijzigt. Omdat taak opties kunnen voor komen dat een taak op het geplande tijdstip wordt uitgevoerd, is het belang rijk om de taak opties te begrijpen en deze zorgvuldig te gebruiken.

Power Shell maakt gebruik van dezelfde taak opties die taak planner gebruikt. Zie het Help-onderwerp voor [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)voor meer informatie over de taak opties.

Taak opties worden opgeslagen in het XML-bestand met de geplande taak. U kunt taak opties instellen wanneer u een geplande taak maakt of deze op elk gewenst moment wijzigt.

De `New-ScheduledJobOption` cmdlet maakt een geplande taak optie waarbij de optie geplande taak **WakeToRun** is ingesteld op waar. Met de optie **WakeToRun** wordt de geplande taak uitgevoerd, zelfs als de computer zich in de slaap stand of sluimer stand bevindt op de geplande begin tijd. Met de opdracht worden de taak opties in de `$O` variabele opgeslagen.

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a>Hoe kan ik taak opties ophalen?

Als u de taak opties van een geplande taak wilt weer geven, gebruikt u de `Get-ScheduledJobOption` cmdlet. Gebruik de para meters **name** , **id** en **input object** om de geplande taak op te geven, niet de taak opties.

`Get-ScheduledJobOption` Hiermee worden de taak opties van de **ProcessJob** opgehaald.

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

## <a name="how-to-change-job-options"></a>Taak opties wijzigen

U kunt de taak opties van een geplande taak wijzigen wanneer u een geplande taak maakt of een bestaande taak bewerkt.

De splatted `$JobParms` worden door gegeven aan de `Add-JobTrigger` cmdlet om de proces taak te maken. De para meter **ScheduledJobOption** wordt gebruikt om de taak opties in de variabele op te geven `$O` .

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

U kunt de taak opties ook op elk gewenst moment wijzigen in een bestaande geplande taak.
De volgende opdracht gebruikt de `Set-ScheduledJobOption` cmdlet om de waarde van de **WakeToRun** -optie van de **ProcessJob** scheduledJob te wijzigen in **True**.

De `Set` cmdlets in de **PSScheduledJob** -module, zoals de `Set-ScheduledJobOption` cmdlet, hebben geen **naam** **-of id-** para meters. U kunt de para meter **input object** gebruiken om de geplande taak opties op te geven of een geplande taak vanuit `Get-ScheduledJobOption` cmdlet naar te pipeen `Set-ScheduledJobOption` .

In dit voor beeld wordt de `Get-ScheduledJob` cmdlet gebruikt om de ProcessJob op te halen. De cmdlet wordt gebruikt `Get-ScheduledJobOption` voor het ophalen van de taak opties in de **ProcessJob** en de `Set-ScheduledJobOption` cmdlet om de **WakeToRun** -taak optie in de ProcessJob te wijzigen in waar.

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a>Geplande taak instanties ophalen

Wanneer een geplande taak wordt gestart, maakt Power shell een taak exemplaar dat lijkt op een standaard-Power shell-achtergrond taak. U kunt de taak-cmdlets gebruiken, zoals `Get-Job` `Stop-Job` en `Receive-Job` voor het beheren van de taak exemplaren.

> [!NOTE]
> Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd. Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .

Als u alle instanties van Power shell-geplande taken en alle actieve standaard taken wilt ophalen, gebruikt u de `Get-Job` cmdlet. `Import-Module`Met de cmdlet wordt de **PSScheduledJob** -module geïmporteerd en worden `Get-Job` de taken op de lokale computer opgehaald.

```powershell
Import-Module PSScheduledJob
Get-Job
```

`Get-Job` Hiermee worden de exemplaren van **ProcessJob** op de lokale computer opgehaald.

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

In de standaard weergave wordt de begin tijd niet weer gegeven. Dit onderscheidt meestal het aantal exemplaren van dezelfde geplande taak.

De `Get-Job` cmdlet verzendt objecten uit de pijp lijn. `Format-Table`Met de cmdlet worden de eigenschappen **name** , **id** en **BeginTime** van de geplande taak weer gegeven.

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

## <a name="get-scheduled-job-results"></a>Geplande taak resultaten ophalen

Gebruik de cmdlet om de resultaten van een exemplaar van een geplande taak op te halen `Receive-Job` .

> [!NOTE]
> Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd. Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .

In deze voor beelden worden de resultaten opgehaald van het nieuwste exemplaar van de geplande **ProcessJob** -taak (ID = 51).

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

De resultaten van geplande taken worden op schijf opgeslagen, dus de para meter **behouden** van `Receive-Job` is niet vereist. Zonder de para meter **Keep** kunt u echter de resultaten van een geplande taak slechts één keer in elke Power shell-sessie ophalen. Als u een nieuwe Power shell-sessie wilt starten, typt `PowerShell` of opent u een nieuw Power shell-venster.

## <a name="see-also"></a>Zie ook

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets

[Taak planner](/windows/desktop/TaskSchd/task-scheduler-reference)
