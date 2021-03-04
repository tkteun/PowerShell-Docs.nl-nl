---
description: Legt uit hoe u problemen met geplande taken kunt oplossen
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: aac2133cee4abdd7e50e7b433104b9578d74b0a8
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685854"
---
# <a name="about-scheduled-jobs-troubleshooting"></a>Over het oplossen van problemen met geplande taken

## <a name="short-description"></a>Korte beschrijving

Legt uit hoe u problemen met geplande taken kunt oplossen

## <a name="long-description"></a>Lange beschrijving

In dit document worden enkele van de problemen beschreven die u kunt ondervinden bij het gebruik van de geplande taak functies van Power shell en worden oplossingen voor deze problemen voorgesteld.

Zie [about_Scheduled_Jobs](about_Scheduled_Jobs.md) en de gerelateerde geplande taken over onderwerpen voor informatie over het gebruik van Power shell-geplande taken.

Zie [PSScheduledJob](xref:PSScheduledJob)voor meer informatie over de cmdlets die deel uitmaken van de **PSScheduledJob** -module.

## <a name="cant-find-job-results"></a>Kan geen taak resultaten vinden

### <a name="basic-method-for-getting-job-results-in-powershell"></a>Basis methode voor het ophalen van taak resultaten in Power shell

Wanneer een geplande taak wordt uitgevoerd, wordt er een exemplaar van de geplande taak gemaakt. Gebruik de taak-cmdlets om de resultaten van geplande taak exemplaren weer te geven, te beheren en op te halen.

> [!NOTE]
> Als u de taak-cmdlets wilt gebruiken voor exemplaren van geplande taken, moet de **PSScheduledJob** -module in de sessie worden geïmporteerd. Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of gebruikt u een geplande taak-cmdlet, zoals `Get-ScheduledJob` .

Als u een lijst wilt weer geven van alle exemplaren van een geplande taak, gebruikt u de `Get-Job` cmdlet.

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

De `Get-Job` cmdlet verzendt **ProcessJob** -objecten omlaag in de pijp lijn. `Format-Table`Met de cmdlet worden de eigenschappen **name**, **id** en **PSBeginTime** van een geplande taak instantie in een tabel weer gegeven.

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
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

Gebruik de cmdlet om de resultaten van een exemplaar van een geplande taak op te halen `Receive-Job` . Met de volgende opdracht worden de resultaten van het nieuwste exemplaar van de ProcessJob (ID = 50) opgehaald.

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a>Basis methode voor het zoeken naar taak resultaten op schijf

Als u geplande taken wilt beheren, gebruikt u de taak-cmdlets, zoals `Get-Job` en `Receive-Job` .

Als `Get-Job` het taak exemplaar niet wordt opgehaald of `Receive-Job` de taak resultaten niet worden opgehaald, kunt u de uitvoerings geschiedenis bestanden voor de taak zoeken op schijf.
De uitvoerings geschiedenis bevat een record van alle geactiveerde taak exemplaren.

Controleer of er een time stamp-naam voor komt in de Directory voor een geplande taak in het volgende pad:

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

Bijvoorbeeld:

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

Met de `Get-ChildItem` cmdlet wordt bijvoorbeeld de uitvoerings geschiedenis op schijf opgehaald van de geplande taak **ProcessJob** .

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

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

Elke time stamp-naam directory vertegenwoordigt een taak exemplaar. De resultaten van elk taak exemplaar worden opgeslagen in een **Results.xml** -bestand in de map met de naam van de tijds tempel.

Met de volgende opdracht worden bijvoorbeeld de **Results.xml** -bestanden voor elk opgeslagen exemplaar van de geplande taak **ProcessJob** . Als het **Results.xml** bestand ontbreekt, kan Power shell de taak resultaten niet retour neren of weer geven.

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

Het is mogelijk dat de taak-cmdlet geen geplande taak exemplaren of de bijbehorende resultaten kan ophalen omdat de **PSScheduledJob** -module niet is geïmporteerd in de sessie.

> [!NOTE]
> Voordat u een taak-cmdlet gebruikt voor geplande taak instanties, controleert u of de **PSScheduledJob** -module is opgenomen in de sessie. Zonder de **PSScheduledJob** -module kunnen de taak-cmdlets geen geplande taak exemplaren of hun resultaten ophalen.

De **PSScheduledJob** -module importeren:

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a>De resultaten zijn mogelijk al geretourneerd door de Receive-Job-cmdlet

Als geen `Receive-Job` taak exemplaar resultaat retourneert, kan dit zijn omdat er een `Receive-Job` opdracht voor dat taak exemplaar is uitgevoerd in de huidige sessie zonder de para meter **Keep** .

Wanneer u gebruikt `Receive-Job` zonder de para meter **Keep** , worden `Receive-Job` de taak resultaten geretourneerd en wordt de eigenschap **HasMoreData** van het taak exemplaar ingesteld op **Onwaar**. De waarde **Onwaar** geeft `Receive-Job` aan dat de resultaten van de taak zijn geretourneerd en het exemplaar heeft geen resultaten meer die kunnen worden geretourneerd. Deze instelling is geschikt voor standaard achtergrond taken, maar niet voor exemplaren van geplande taken die op schijf worden opgeslagen.

Als u de resultaten van de taak instantie opnieuw wilt ophalen, start u een nieuwe Power shell-sessie door te typen `PowerShell` . Importeer de **PSScheduledJob** -module en voer de `Receive-Job` opdracht opnieuw uit.

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a>De para meter Keep gebruiken om resultaten meer dan één keer in een sessie op te halen

Als u het resultaat van een taak exemplaar in een sessie meer dan één keer wilt ophalen, gebruikt u de para meter **Keep** van de `Receive-Job` cmdlet.

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a>De geplande taak is mogelijk beschadigd

Als een geplande taak beschadigd raakt, verwijdert Power shell de beschadigde geplande taak en de resultaten ervan. U kunt de resultaten van een beschadigde geplande taak niet herstellen.

Gebruik de cmdlet om te bepalen of een geplande taak nog bestaat `Get-ScheduledJob` .

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a>Het aantal resultaten kan de ExecutionHistoryLength overschrijden

De eigenschap **ExecutionHistoryLength** van een geplande taak bepaalt hoeveel taak exemplaren en de bijbehorende resultaten worden opgeslagen op schijf. De standaard waarde is 32.
Wanneer het aantal exemplaren van een geplande taak deze waarde overschrijdt, verwijdert Power shell het oudste taak exemplaar om ruimte te maken voor elk nieuw taak exemplaar.

Als u de waarde van de eigenschap **ExecutionHistoryLength** van een geplande taak wilt ophalen, gebruikt u de volgende opdracht indeling:

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **ExecutionHistoryLength** van de geplande **ProcessJob** -taak opgehaald.

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

Als u de waarde van de eigenschap **ExecutionHistoryLength** wilt instellen of wijzigen, gebruikt u de para meter **MaxResultCount** van de `Register-ScheduledJob` `Set-ScheduledJob` cmdlets.

Met de volgende opdracht wordt de waarde van de eigenschap **ExecutionHistoryLength** verhoogd naar 50.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a>De resultaten van de taak instantie zijn mogelijk verwijderd

Met de para meter **ClearExecutionHistory** van de `Set-ScheduledJob` cmdlet wordt de uitvoerings geschiedenis van een taak verwijderd. U kunt deze functie gebruiken om schijf ruimte vrij te maken of resultaten te verwijderen die niet nodig zijn of al zijn gebruikt, te analyseren of op een andere locatie op te slaan.

Als u de uitvoerings geschiedenis van een geplande taak wilt verwijderen, gebruikt u de para meter **ClearExecutionHistory** van de geplande taak.

Met de volgende opdracht wordt de uitvoerings geschiedenis van de geplande taak **ProcessJob** verwijderd.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

De `Remove-Job` cmdlet verwijdert ook taak resultaten. Wanneer u gebruikt `Remove-Job` om een geplande taak te verwijderen, worden alle exemplaren van de taak op de schijf verwijderd, inclusief de uitvoerings geschiedenis en alle taak resultaten.

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a>Taken die zijn gestart met behulp van de cmdlet Start-Job worden niet op schijf opgeslagen

Wanneer u gebruikt `Start-Job` om een geplande taak te starten in plaats van een taak trigger te gebruiken, `Start-Job` wordt een standaard achtergrond taak gestart. De achtergrond taak en de bijbehorende resultaten worden niet opgeslagen in de uitvoerings geschiedenis van de taak op schijf.

U kunt de- `Get-Job` cmdlet gebruiken om de taak en de `Receive-Job` cmdlet op te halen om de resultaten van de taak op te halen, maar de resultaten zijn pas beschikbaar nadat u ze hebt ontvangen, tenzij u de para meter Keep van de `Receive-Job` cmdlet gebruikt.

Achtergrond taken en de bijbehorende resultaten zijn ook specifieke sessies; ze bestaan alleen in de sessie waarin ze zijn gemaakt. Als u de taak verwijdert met `Remove-Job` , sluit u de sessie of sluit Power shell, het taak exemplaar en de resultaten ervan worden verwijderd.

## <a name="scheduled-job-doesnt-run"></a>De geplande taak wordt niet uitgevoerd

Geplande taken worden niet automatisch uitgevoerd als de taak wordt geactiveerd of de geplande taak is uitgeschakeld.

Gebruik de `Get-ScheduledJob` cmdlet om de geplande taak op te halen. Controleer of de waarde van de eigenschap **enabled** van de geplande taak **waar** is.

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

Gebruik de `Get-JobTrigger` cmdlet om de taak triggers van de geplande taak op te halen.
Controleer of de waarde van de eigenschap **enabled** van de taak trigger **True** is.

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a>Geplande taken worden niet automatisch uitgevoerd als de taak triggers ongeldig zijn

Een taak trigger kan bijvoorbeeld een datum in het verleden of een datum die niet plaatsvindt, opgeven, zoals de vijfde maandag van de maand.

Geplande taken worden niet automatisch uitgevoerd als er niet aan de voor waarden van de taak trigger of aan de taak opties wordt voldaan.

Bijvoorbeeld een geplande taak die alleen wordt uitgevoerd wanneer een bepaalde gebruiker zich aanmeldt bij de computer, wordt niet uitgevoerd als de gebruiker zich niet aanmeldt of alleen op afstand verbinding maakt.

Bekijk de opties van de geplande taak en zorg ervoor dat ze zijn voldaan.
Bijvoorbeeld een geplande taak waarvoor de computer inactief moet zijn of een netwerk verbinding vereist, of een lange **IdleDuration** heeft of een korte **IdleTimeout** kan nooit worden uitgevoerd.

Gebruik de `Get-ScheduledJobOption` cmdlet om de taak opties en de bijbehorende waarden te controleren.

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
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

Zie [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)voor beschrijvingen van de opties voor geplande taken.

### <a name="the-scheduled-job-instance-might-have-failed"></a>De geplande taak kan zijn mislukt

Als een geplande taak mislukt, Power shell rapporteert deze onmiddellijk door een fout bericht te genereren. Als de taak echter mislukt wanneer taak planner probeert deze uit te voeren, is de fout niet beschikbaar voor Power shell.

Gebruik de volgende methoden om taak fouten te detecteren en te corrigeren:

Controleer het gebeurtenis logboek van de taak planner op fouten. Als u het logboek wilt controleren, gebruikt u Logboeken of een Power shell-opdracht zoals de volgende:

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

Controleer de taak record in taak planner. Geplande power shell-taken worden opgeslagen in de volgende geplande map voor de taak:

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a>De geplande taak wordt mogelijk niet uitgevoerd vanwege onvoldoende machtigingen

Geplande taken worden uitgevoerd met de machtigingen van de gebruiker die de taak heeft gemaakt of de machtigingen van de gebruiker die is opgegeven door de para meter **Credential** in de `Register-ScheduledJob` or- `Set-ScheduledJob` opdracht.

Als die gebruiker geen machtiging heeft om de opdrachten of scripts uit te voeren, mislukt de taak.

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a>Kan de geplande taak niet ophalen of de geplande taak is beschadigd

In zeldzame gevallen kunnen geplande taken beschadigd raken of interne tegen strijdigheden bevatten die niet kunnen worden opgelost. Dit gebeurt meestal wanneer de XML-bestanden voor de geplande taak hand matig worden bewerkt, wat resulteert in ongeldige XML.

Wanneer een geplande taak is beschadigd, probeert Power shell de geplande taak, de uitvoerings geschiedenis en de resultaten van de schijf te verwijderen.

Als het niet mogelijk is om de geplande taak te verwijderen, ontvangt u een fout bericht over een beschadigde taak telkens wanneer u de `Get-ScheduledJob` cmdlet uitvoert.

Als u een beschadigde geplande taak wilt verwijderen, gebruikt u een van de volgende methoden:

Verwijder de `<ScheduledJobName>` map voor de geplande taak. Verwijder de **ScheduledJob** -map niet.

De locatie van de map:

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

Bijvoorbeeld:

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

Taak planner gebruiken om de geplande taak te verwijderen. Geplande power shell-taken worden weer gegeven in het volgende pad van de taak planner:

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a>Taak-cmdlets kunnen geplande taken niet consistent vinden

Wanneer de **PSScheduledJob** -module zich niet in de huidige sessie bevindt, kunnen de taak-cmdlets geen geplande taken ophalen, starten of de resultaten ophalen.

Als u de **PSScheduledJob** -module wilt importeren, typt `Import-Module PSScheduledJob` of voert u een cmdlet in de module, zoals de cmdlet, uit of haalt u deze op `Get-ScheduledJob` .
Vanaf Power Shell 3,0 worden modules automatisch geïmporteerd wanneer u een cmdlet in de module ophaalt of gebruikt.

Wanneer de **PSScheduledJob** -module zich niet in de huidige sessie bevindt, is de volgende opdracht volgorde mogelijk.

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

Dit probleem treedt op omdat de `Get-ScheduledJob` opdracht de **PSScheduledJob** -module automatisch importeert en vervolgens de opdracht uitvoert.

## <a name="see-also"></a>Zie ook

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[PSScheduledJob](xref:PSScheduledJob) -module-cmdlets

[Taak planner](/windows/desktop/TaskSchd/task-scheduler-reference)
