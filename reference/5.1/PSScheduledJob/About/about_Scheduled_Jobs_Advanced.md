---
description: Hierin worden geavanceerde geplande taak onderwerpen beschreven, met inbegrip van de bestands structuur waarin geplande taken worden uitgevoerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252413"
---
# <a name="about-scheduled-jobs-advanced"></a>Over geplande taken Geavanceerd

## <a name="short-description"></a>Korte beschrijving

Hierin worden geavanceerde geplande taak onderwerpen beschreven, met inbegrip van de bestands structuur waarin geplande taken worden uitgevoerd.

## <a name="long-description"></a>Lange beschrijving

Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.

## <a name="scheduled-job-directories-and-files"></a>Geplande mappen en bestanden voor de taak

Geplande power shell-taken zijn zowel Power shell-taken als taak planner taken.
Elke geplande taak wordt geregistreerd in de taak planner en opgeslagen op schijf in de XML-indeling van Microsoft .NET Framework-serialisatie.

Wanneer u een geplande taak maakt, maakt Power shell een map voor de geplande taak in de `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` map op de lokale computer. De mapnaam is hetzelfde als de naam van de taak.

Hier volgt een voor beeld van een **ScheduledJobs** -map.

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

Elke geplande taak heeft een eigen map. De map bevat het XML-bestand met de geplande taak en een **uitvoer** subdirectory.

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

De **uitvoermap** voor een geplande taak bevat de uitvoerings geschiedenis.
Telkens wanneer een taak trigger een geplande taak start, maakt Power shell een naam van een time stamp-map in de uitvoermap. De time stamp-map bevat de resultaten van de taak in een **Results.xml** -bestand en de taak status in een **Status.xml** bestand.

De volgende opdracht toont de uitvoerings geschiedenis mappen voor de geplande taak **ProcessJob** .

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

U kunt de bestanden van de **ScheduledJobDefinition.xml** , **Results.xml** en **Status.xml** openen en bekijken of de `Select-XML` cmdlet gebruiken om het bestand te parseren.

> [!WARNING]
> Bewerk de XML-bestanden niet. Als een XML-bestand ongeldige XML bevat, verwijdert Power shell de geplande taak en de uitvoerings geschiedenis, inclusief de taak resultaten.

## <a name="start-a-scheduled-job-immediately"></a>Een geplande taak onmiddellijk starten

U kunt een geplande taak onmiddellijk op een van de volgende twee manieren starten:

- Voer de `Start-Job` cmdlet uit om een geplande taak te starten.
- Voeg de **RunNow** -para meter toe aan de `Register-ScheduledJob` opdracht om de taak te starten zodra de opdracht wordt uitgevoerd.

Taken die zijn gestart met behulp van de `Start-Job` cmdlet zijn standaard-Power shell-achtergrond taken, geen exemplaren van de geplande taak. Net als alle achtergrond taken worden deze taken onmiddellijk gestart, niet onderhevig aan taak opties of worden beïnvloed door taak triggers. De taak uitvoer wordt niet opgeslagen in de **uitvoermap** van de geplande projectmap.

De volgende opdracht maakt gebruik van de para meter **definitienaam** van de `Start-Job` cmdlet om de geplande taak ProcessJob te starten.

```powershell
Start-Job -DefinitionName ProcessJob
```

Gebruik de taak-cmdlets om de taak te beheren en de taak resultaten te verkrijgen. Zie [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)voor meer informatie over de taak-cmdlets.

> [!NOTE]
> Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd. Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .

## <a name="rename-a-scheduled-job"></a>De naam van een geplande taak wijzigen

Als u de naam van een geplande taak wilt wijzigen, gebruikt u de para meter name van de `Set-ScheduledJob` cmdlet. Wanneer u de naam van een geplande taak wijzigt, wijzigt Power shell de naam van de geplande taak en de map geplande taak. De namen van exemplaren van de geplande taak die al zijn uitgevoerd, worden echter niet gewijzigd.

## <a name="get-start-and-end-times"></a>Begin-en eind tijden ophalen

Gebruik de eigenschappen **PSBeginTime** en **PSEndTime** van het ScheduledJob-object dat `Get-Job` wordt geretourneerd voor geplande taken om de datums en tijden te verkrijgen waarop de taak exemplaren zijn gestart en beëindigd.

In het volgende voor beeld wordt de **eigenschap** para meter van de `Format-Table` cmdlet gebruikt om de eigenschappen **PSBeginTime** en **PSEndTime** van elk taak exemplaar in een tabel weer te geven. Een berekende eigenschap met de naam **Label** toont de verstreken tijd van elk taak exemplaar.

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a>Uitvoerings geschiedenis beheren

U kunt het aantal taak instantie resultaten bepalen dat voor elke geplande taak wordt opgeslagen en de uitvoerings geschiedenis en de opgeslagen taak resultaten van een geplande taak verwijderen.

De eigenschap **ExecutionHistoryLength** van een geplande taak bepaalt hoeveel taak exemplaar resultaten voor de geplande taak worden opgeslagen. Wanneer het aantal opgeslagen resultaten de waarde van de eigenschap **ExecutionHistoryLength** overschrijdt, verwijdert Power shell de resultaten van de oudste instantie om ruimte te maken voor de resultaten van het nieuwste exemplaar.

Standaard slaat Power shell de uitvoerings geschiedenis en resultaten van 32 exemplaren van elke geplande taak op. Als u deze waarde wilt wijzigen, gebruikt u de para meters van de **MaxResultCount** van de- `Register-ScheduledJob` of- `Set-ScheduledJob` cmdlets.

Als u de uitvoerings geschiedenis en alle resultaten voor een geplande taak wilt verwijderen, gebruikt u de para meter **ClearExecutionHistory** van de `Set-ScheduledJob` cmdlet. Als u deze uitvoerings geschiedenis verwijdert, wordt niet voor komen dat Power shell de resultaten van nieuwe exemplaren van de geplande taak opslaat.

In het volgende voor beeld wordt splatting gebruikt om `$JobParms` de parameter waarden te maken die worden door gegeven aan de `Register-ScheduledJob` cmdlet. Zie [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.
`Register-ScheduledJob`Hiermee `@JobParms` maakt u een geplande taak. De opdracht gebruikt de para meter **MaxResultCount** met de waarde 12 om alleen de 12 nieuwste taak instantie resultaten van de geplande taak op te slaan.

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

De volgende opdracht maakt gebruik van de para meter **MaxResultCount** van de `Set-ScheduledJob` cmdlet om het aantal opgeslagen instantie resultaten te verhogen naar
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

Met de volgende opdracht worden de uitvoerings geschiedenis en de huidige opgeslagen resultaten van de geplande taak **ProcessJob** verwijderd.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

Met de volgende opdracht worden de waarden van de eigenschappen name en **ExecutionHistoryLength** van alle geplande taken op de computer opgehaald en weer gegeven in een tabel.

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a>Zie ook

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets

[Taak planner](/windows/desktop/TaskSchd/task-scheduler-reference)
