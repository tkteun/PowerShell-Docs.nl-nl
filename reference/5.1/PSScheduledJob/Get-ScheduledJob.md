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
# Get-ScheduledJob

## SAMENVATTING
Hiermee worden geplande taken opgehaald op de lokale computer.

## SYNTAXIS

### DefinitionId (standaard)

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### Definitie

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Get-ScheduledJob** haalt geplande taken op de lokale computer op.
**Get-ScheduledJob** haalt alleen geplande taken op die door de huidige gebruiker zijn gemaakt met behulp van de cmdlet Register-ScheduledJob.

Hoewel taken die zijn gemaakt met behulp van de cmdlet **REGI ster-ScheduledJob** , worden weer gegeven in taak planner, worden met **Get-ScheduledJob** alleen geplande taken opgehaald.
Er worden geen geplande taken opgehaald die zijn gemaakt in taak planner.

Zonder para meters haalt **Get-ScheduledJob** alle geplande taken op de computer op.
U kunt de para meters van **Get-ScheduledJob** gebruiken om geplande taken op basis van id of naam op te halen en ze te bekijken of door te sluizen naar andere cmdlets.

**Get-ScheduledJob** is een van een verzameling cmdlets voor taak planning in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: alle geplande taken ophalen

```
PS C:\> Get-ScheduledJob
```

Met deze opdracht worden alle geplande taken op de lokale computer opgehaald.

### Voor beeld 2: geplande taken op naam ophalen

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

Met deze opdracht worden alle geplande taken opgehaald op de computer met namen die back-up of archief bevatten.
Met deze opdracht indeling kunt u zoeken naar bepaalde taken.

### Voor beeld 3: geplande taken ophalen op externe computers

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

Met deze opdracht worden alle geplande taken opgehaald op de computers die worden vermeld in het Servers.txt-bestand.
De opdracht gebruikt de cmdlet Invoke-Command om op elke computer een opdracht **Get-ScheduleJob** uit te voeren.

### Voor beeld 4: door pipes geplande taken naar andere cmdlets

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

Met deze opdracht worden de taak triggers van de geplande DailyBackup-en WeeklyBackup-taken opgehaald.
De cmdlet **Get-ScheduledJob** wordt gebruikt voor het ophalen van de geplande taken en de cmdlet Get-JobTrigger om de taak triggers van de geplande taken te krijgen.

## PARAMETERS

### -Id
Hiermee worden alleen de geplande taken met het opgegeven id-nummer (ID) opgehaald.
Voer een of meer Id's van de geplande taken op de computer in.
**Get-ScheduledJob** haalt standaard alle geplande taken op de computer op.

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

### -Name
Hiermee worden alleen de geplande taken met de opgegeven namen opgehaald.
Voer een of meer namen van geplande taken op de computer in.
Joker tekens worden ondersteund.
**Get-ScheduledJob** haalt standaard alle geplande taken op de computer op.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen pipe invoer naar **Get-ScheduledJob**.

## UITVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition

## OPMERKINGEN

* Elke geplande taak wordt opgeslagen in een submap van de $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs op de lokale computer. De submap krijgt de naam van de geplande taak en bevat het XML-bestand voor de geplande taak en records van de uitvoerings geschiedenis. Zie about_Scheduled_Jobs_Advanced voor meer informatie over geplande taken op schijf.
* Geplande taken die u in Windows Power Shell maakt, worden weer gegeven in taak planner in de map Library\Microsoft\Windows\PowerShell\ScheduledJobs van taak planner. U kunt taak planner gebruiken om de geplande taak weer te geven en te bewerken.
* U kunt taak planner, het SchTasks.exe opdracht regel programma en de cmdlets van de taak planner gebruiken om geplande taken te beheren die u met de geplande taak-cmdlets maakt. U kunt de geplande taak-cmdlets echter niet gebruiken voor het beheren van taken die u maakt in taak planner.

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
