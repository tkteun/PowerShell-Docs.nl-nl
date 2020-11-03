---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250304"
---
# Get-ScheduledJobOption

## SAMENVATTING
Hiermee worden de taak opties van geplande taken opgehaald.

## SYNTAXIS

### Taak definitie (standaard)

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Get-ScheduledJobOption** haalt de taak opties van geplande taken op.
U kunt deze opdracht gebruiken om de taak opties te controleren of om de taak opties naar andere cmdlets te pipeen.

Taak opties worden niet onafhankelijk van de schijf opgeslagen. ze maken deel uit van een geplande taak.
Als u de taak opties van een geplande taak wilt weer geven, geeft u de geplande taak op.

Gebruik de para meters van de cmdlet **Get-ScheduledJobOption** om de geplande taak te identificeren.
U kunt geplande taken identificeren met hun namen of identificatie nummers of door **ScheduledJob** -objecten op te geven of te maken, zoals die die worden geretourneerd door de Get-ScheduledJob cmdlet, naar **Get-ScheduledJobOption**.

**Get-ScheduledJobOption** is een van een verzameling cmdlets voor taak planning in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: taak opties ophalen

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : False

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Met deze opdracht worden de taak opties opgehaald van geplande taken met een back-up in hun namen.
De resultaten geven het taak opties-object weer dat **Get-ScheduledJobOption** retourneert.

### Voor beeld 2: alle taak opties ophalen

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

Met deze opdracht worden de taak opties van alle geplande taken op de lokale computer opgehaald.

De Get-ScheduledJob cmdlet wordt gebruikt om de geplande taken op de lokale computer op te halen.
Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet **Get-ScheduledJobOption** , waarmee de taak opties van elke geplande taak worden opgehaald.

### Voor beeld 3: de geselecteerde taak opties ophalen

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

In dit voor beeld ziet u hoe u met bepaalde waarden het object taak opties kunt vinden.

Met de eerste opdracht worden taak opties opgehaald waarin de eigenschap RunElevated de waarde $True heeft en de eigenschap RunWithoutNetwork de waarde $False heeft.
De uitvoer toont het object **JobOptions** dat is geselecteerd.

### Voor beeld 4: taak opties gebruiken om een nieuwe taak te maken

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

In dit voor beeld ziet u hoe u de taak opties kunt gebruiken die Get-ScheduledJobOption in een nieuwe geplande taak ontvangt.

De eerste opdracht gebruikt **Get-ScheduledJobOption** om de opties voor de taken van de geplande BackupTestLogs-taak op te halen.
Met de opdracht worden de opties opgeslagen in de variabele $Opts.

De tweede opdracht maakt gebruik van Register-ScheduledJob cmdlet om een nieuwe geplande taak te maken.
De waarde van de para meter *ScheduledJobOption* is het object Options in de variabele $opts.

### Voor beeld 5: taak opties ophalen van een externe computer

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

Met deze opdracht wordt de cmdlet Invoke-Command gebruikt om de geplande taak opties van de DataDemon-taak op de Srv01-computer op te halen.
Met de opdracht worden de opties opgeslagen in de variabele $O.

## PARAMETERS

### -Id
Hiermee geeft u het id-nummer van een geplande taak op.
**Get-ScheduledJobOption** haalt de taak opties van de opgegeven geplande taak op.

Als u de identificatie nummers van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.

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
Voer een variabele in die een **ScheduledJob** -object bevat of typ een opdracht of expressie waarmee een **ScheduledJob** -object wordt opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook een **ScheduledJob** -object door sluizen naar **Get-ScheduledJobOption**.

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
Hiermee geeft u de namen van geplande taken.
**Get-ScheduledJobOption** haalt de taak opties van de opgegeven geplande taak op.
Joker tekens worden ondersteund.

Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition
U kunt een geplande taak door sluizen van Get-ScheduledJob naar **Get-ScheduledJobOption**.

## UITVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobOptions

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
