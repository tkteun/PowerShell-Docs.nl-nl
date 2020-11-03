---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250290"
---
# Unregister-ScheduledJob

## SAMENVATTING
Hiermee verwijdert u de geplande taken op de lokale computer.

## SYNTAXIS

### Definitie (standaard)

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Definitie

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **unregister-ScheduledJob** verwijdert geplande taken van de lokale computer.

Wanneer u een geplande taak verwijdert of de registratie ervan ongedaan maakt, wordt de **registratie-ScheduledJob** verwijderd uit de map voor de geplande taak (in de map $Home \appdata\local\microsoft\windows\powershell\scheduledjobs), die het XML-bestand bevat dat de geplande taak, de taak uitvoerings geschiedenis en alle taak resultaten definieert.
Met deze actie wordt ook de taak uit taak planner verwijderd.

**Registratie ongedaan maken: ScheduledJob** verwijdert alleen de geplande taken die zijn gemaakt met behulp van de cmdlet Register-ScheduledJob.
Geplande taken die zijn gemaakt in taak planner, worden niet verwijderd.

U kunt de para meters van **unregister-ScheduledJob** gebruiken om de geplande taken te verwijderen op basis van de id of naam, of door de ScheduledJob geplande taken van Get-ScheduledJob uit te **schrijven naar unregistere-** refrom.

**Unregister-ScheduledJob** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een geplande taak verwijderen

```
PS C:\> Unregister-ScheduledJob TestJob
```

Met deze opdracht wordt de geplande taak TestJob op de lokale computer verwijderd.

### Voor beeld 2: alle geplande taken verwijderen

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

In dit voor beeld ziet u twee verschillende opdrachten waarmee alle geplande taken op de lokale computer worden verwijderd.

De eerste opdracht gebruikt de cmdlet Get-ScheduledJob om alle geplande taken op de lokale computer op te halen.
Een pijplijn operator (|) verzendt de geplande taken voor het **ongedaan maken van de registratie-ScheduleJob** , waarmee ze worden verwijderd.

De tweede opdracht maakt gebruik van de para meter *name* van **unregister-ScheduledJob** met een waarde van alle (*) om alle geplande taken te verwijderen.

Beide opdrachten gebruiken de para meter *Force* , waarmee een geplande taak wordt verwijderd, zelfs als er een exemplaar van de taak wordt uitgevoerd.

### Voor beeld 3: een geplande taak op een externe computer verwijderen

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

Met deze opdracht worden geplande taken verwijderd met namen die beginnen met testen op de externe computer Server01.
De opdracht gebruikt de cmdlet Invoke-Command om de opdracht **unregister-ScheduledJob** uit te voeren op de Server02-computer.

## PARAMETERS

### -Force
Hiermee wordt de geplande taak verwijderd, zelfs als er een exemplaar van de taak wordt uitgevoerd.
Bij **het ongedaan maken van de registratie-ScheduledJob** wordt de uitvoering van taken standaard niet onderbroken.

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

### -Id
Hiermee worden de geplande taken met de opgegeven identificatie nummers (ID) verwijderd.
Voer de Id's van de geplande taken op de computer in.

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u een geplande taak op.
Voer een variabele in die **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook **ScheduledJob** -objecten pipeen voor het **ongedaan maken van de registratie-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee worden de geplande taken met de opgegeven namen verwijderd.
Voer de namen in van een of meer geplande taken op de computer.
Joker tekens worden ondersteund.

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

### -Confirm
Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

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

### -WhatIf
Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition
U kunt geplande taken door sluizen naar Unregister-ScheduledJob

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

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
