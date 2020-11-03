---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250321"
---
# Add-JobTrigger

## SAMENVATTING
Taak triggers worden toegevoegd aan geplande taken.

## SYNTAXIS

### Taak definitie (standaard)

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### JobDefinitionId

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **add-JobTrigger** voegt taak triggers toe aan geplande taken.
U kunt deze gebruiken om meerdere triggers aan meerdere geplande taken toe te voegen.

Een taak trigger start een geplande taak op een eenmalige of terugkerende planning of wanneer er een gebeurtenis optreedt.

Gebruik de *trigger* parameter van **add-JobTrigger** om de taak triggers te identificeren die moeten worden toegevoegd.
Gebruik de para meters *name* , *id* of *input object* van **add-JobTrigger** om de geplande taak te identificeren waaraan de triggers worden toegevoegd.

Als u taak triggers wilt maken voor de waarde van de *trigger* parameter, gebruikt u de cmdlet New-JobTrigger of gebruikt u een hash-tabel om de taak trigger op te geven.

**Add-JobTrigger** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een taak trigger toevoegen aan een geplande taak

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

Met deze opdrachten wordt de dagelijkse taak trigger toegevoegd aan de geplande taak TestJob.

De eerste opdracht gebruikt de cmdlet New-JobTrigger om een taak trigger te maken waarmee elke dag om 3:00 uur een geplande taak wordt gestart.
Met de opdracht wordt de taak trigger opgeslagen in de variabele $Daily.

De tweede opdracht maakt gebruik van de cmdlet **add-JobTrigger** om de taak trigger toe te voegen in de variabele $Startup aan de geplande TestJob-taak.

### Voor beeld 2: een taak trigger toevoegen aan verschillende geplande taken

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

Met deze opdracht wordt een AtStartup-taak trigger toegevoegd aan alle geplande taken op de lokale computer.
De Get-ScheduledJob gebruikt om alle geplande taken op de computer op te halen.
Er wordt een pijplijn operator (|) gebruikt om de taken te verzenden naar de cmdlet **add-JobTrigger** , waarmee de taak trigger wordt toegevoegd aan elk van de geplande taken.
De waarde van de *trigger* parameter is een New-JobTrigger opdracht waarmee de taak trigger AtStartup wordt gemaakt.

### Voor beeld 3: een taak trigger kopiëren

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

Met deze opdrachten wordt de taak trigger gekopieerd van de geplande BackupArchives-taak en wordt deze toegevoegd aan de TestBackup-en BackupLogs-geplande taken.

De eerste opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger van de geplande taak BackupArchives te verkrijgen.
De-opdracht slaat de trigger op in de variabele $t.

De tweede opdracht maakt gebruik van de cmdlet **add-JobTrigger** om de taak trigger in $t toe te voegen aan de TestBackup-en BackupLogs-geplande taken.

## PARAMETERS

### -Id
Hiermee geeft u de id-nummers van de geplande taken op.
**Add-JobTrigger** voegt de taak trigger toe aan de opgegeven geplande taken.

Als u het id-nummer van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u de geplande taken op.
Voer een variabele in die **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook **ScheduledJob** -objecten pipeen naar **add-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de namen van de geplande taken.
**Add-JobTrigger** voegt de taak triggers toe aan de opgegeven geplande taken.
Joker tekens worden ondersteund.

Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trigger
Hiermee geeft u de taak triggers op die moeten worden toegevoegd.
Voer een hash-tabel in waarmee taak triggers worden opgegeven of een variabele die **ScheduledJobTrigger** -objecten bevat, of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.
U kunt ook **ScheduledJobTrigger** -objecten pipeen naar **add-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger, micro soft. Power shell. ScheduledJob. ScheduledJobDefinition
U kunt taak triggers of geplande taken door sluizen naar **add-JobTrigger**.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer geretourneerd.

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
