---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250562"
---
# Restore-Computer

## SAMENVATTING
Start een systeem herstel op de lokale computer.

## SYNTAXIS

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet Restore **-computer** wordt de lokale computer teruggezet naar het opgegeven systeem herstel punt.

**Herstellen:** de computer wordt opnieuw opgestart.
De herstel bewerking is voltooid tijdens het opnieuw opstarten.

Systeem herstel punten en **herstel-computer** worden alleen ondersteund op client besturingssystemen, zoals Windows 7, Windows Vista en Windows XP.

## VOORBEELDEN

### Voor beeld 1: de lokale computer herstellen

```
PS C:\> Restore-Computer -RestorePoint 253
```

Met deze opdracht wordt de lokale computer teruggezet naar het herstel punt met het Volg nummer 253.

### Voor beeld 2: de lokale computer herstellen met bevestiging

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Met deze opdracht wordt de lokale computer teruggezet naar het herstel punt met het Volg nummer 255.
De para meter *confirm* wordt gebruikt om de gebruiker te vragen voordat de bewerking daad werkelijk wordt uitgevoerd.

### Voor beeld 3: een computer herstellen en de status controleren

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

Met deze opdrachten wordt een systeem herstel uitgevoerd en wordt de status ervan gecontroleerd.

De eerste opdracht gebruikt **Get-ComputerRestorePoint** om de herstel punten op de lokale computer op te halen.

Met de tweede opdracht wordt de computer teruggezet naar het herstel punt met het Volg nummer 255.

De derde opdracht maakt gebruik van de para meter *LastStatus* van de cmdlet *Get-ComputerRestorePoint* om de status van de herstel bewerking te controleren.
Omdat **Restore-computer** geforceerd opnieuw moet worden opgestart, wordt deze opdracht ingevoerd nadat de computer opnieuw is opgestart.

## PARAMETERS

### -RestorePoint
Hiermee geeft u het Volg nummer van het herstel punt op.
Gebruik de cmdlet Get-ComputerRestorePoint om het Volg nummer te vinden.
Deze parameter is vereist.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

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

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u een Restore-Computer-opdracht wilt uitvoeren in Windows Vista en latere versies van het Windows-besturings systeem, opent u Windows Power shell met de optie als administrator uitvoeren.
* Deze cmdlet maakt gebruik van de Windows Management Instrumentation klasse **SystemRestore** (WMI).

## GERELATEERDE KOPPELINGEN

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)
