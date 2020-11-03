---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250307"
---
# Get-JobTrigger

## SAMENVATTING
Hiermee worden de taak triggers van geplande taken opgehaald.

## SYNTAXIS

### Taak definitie (standaard)

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Get-JobTrigger** worden de taak triggers van geplande taken opgehaald.
U kunt deze opdracht gebruiken om de taak triggers te controleren of om de taak triggers te pipeen naar andere cmdlets.

Een taak trigger definieert een terugkerende planning of voor waarden voor het starten van een geplande taak.
Taak triggers worden niet onafhankelijk van de schijf opgeslagen. ze maken deel uit van een geplande taak.
Als u een taak trigger wilt ophalen, geeft u de geplande taak op waarmee de trigger wordt gestart.

Gebruik de para meters van de cmdlet **Get-JobTrigger** om de geplande taken te identificeren.
U kunt de geplande taken identificeren met hun namen of identificatie nummers, of door **ScheduledJob** -objecten in of uit te voeren, zoals die worden geretourneerd door de Get-ScheduledJob cmdlet, naar **Get-JobTrigger**.

**Get-JobTrigger** is een van een verzameling cmdlets voor taak planning in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een taak trigger ophalen op basis van de naam van de geplande taak

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

De opdracht gebruikt de para meter *name* van **Get-JobTrigger** om de taak triggers van de geplande BackupJob-taak op te halen.

### Voor beeld 2: een taak trigger op basis van ID ophalen

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

In het voor beeld wordt de para meter *id* van **Get-JobTrigger** gebruikt om de taak triggers van een geplande taak op te halen.

### Voor beeld 3: taak triggers ophalen door pijpleidingen aan een taak

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

Met deze opdracht worden de taak triggers opgehaald van alle taken met een back-up of archief in hun namen.

### Voor beeld 4: de taak trigger van een taak op een externe computer ophalen

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

Met deze opdracht wordt een van de twee taak triggers van een geplande taak op een externe computer opgehaald.

De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Server01.
De Get-ScheduledJob cmdlet wordt gebruikt voor het ophalen van de geplande back-uptaak, die het pipet naar de **Get-JobTrigger-** cmdlet.
De para meter *TriggerID* wordt gebruikt om alleen de tweede trigger op te halen.

### Voor beeld 5: alle taak triggers ophalen

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

Met deze opdracht worden alle taak triggers van alle geplande taken op de lokale computer opgehaald.

De opdracht gebruikt de Get-ScheduledJob om de geplande taken op de lokale computer op te halen en deze op te **halen-JobTrigger** , waarmee de taak trigger van elke geplande taak wordt opgehaald (indien van toepassing).

Als u de naam van de geplande taak wilt toevoegen aan de taak trigger weergave, gebruikt de opdracht de berekende eigenschap van de cmdlet Format-Table.
Naast de taak trigger eigenschappen die standaard worden weer gegeven, maakt de opdracht een nieuwe ScheduledJob-eigenschap die de naam van de geplande taak weergeeft.

### Voor beeld 6: de eigenschap taak trigger van een geplande taak ophalen

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

De taak triggers van een geplande taak worden opgeslagen in de eigenschap JobTriggers van de taak.
Dit voor beeld toont alternatieven voor het gebruik van de cmdlet **Get-JobTrigger** om taak triggers op te halen.
De resultaten zijn identiek aan het gebruik van de cmdlet **Get-JobTrigger** en de technieken kunnen door elkaar worden gebruikt.

### Voor beeld 7: taak triggers vergelijken

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

In dit voor beeld ziet u hoe de taak triggers van twee geplande taken worden vergeleken.

## PARAMETERS

### -Id
Hiermee geeft u het id-nummer van een geplande taak op.
**Get-JobTrigger** haalt de taak trigger van de opgegeven geplande taak op.

Als u het id-nummer van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u een geplande taak op.
Voer een variabele in die  **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook **ScheduledJob** -objecten pipeen naar **Get-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de naam van een geplande taak op.
**Get-JobTrigger** haalt de taak trigger van de opgegeven geplande taak op.
Joker tekens worden ondersteund.

Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TriggerId
Hiermee worden de opgegeven taak triggers opgehaald.
Voer de trigger-Id's in van een of meer taak triggers van een geplande taak.
Gebruik deze para meter wanneer de geplande taak die wordt opgegeven door de para meters *name* , *id* of *input object* , meerdere taak triggers heeft.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition
U kunt een geplande taak door sluizen van Get-ScheduledJob naar **Get-JobTrigger**.

## UITVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[REGI ster-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Registratie ongedaan maken-ScheduledJob](Unregister-ScheduledJob.md)
