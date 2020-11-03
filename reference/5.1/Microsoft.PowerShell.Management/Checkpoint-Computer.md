---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250843"
---
# Checkpoint-Computer

## SAMENVATTING
Hiermee maakt u een systeem herstel punt op de lokale computer.

## SYNTAXIS

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## BESCHRIJVING

De `Checkpoint-Computer` cmdlet maakt een systeem herstel punt op de lokale computer.

Systeem herstel punten en de `Checkpoint-Computer` cmdlet worden alleen ondersteund op client besturingssystemen, zoals Windows 8, Windows 7, Windows Vista en Windows XP.

Vanaf Windows 8 `Checkpoint-Computer` kan niet meer dan één controle punt elke dag maken.

## VOORBEELDEN

### Voor beeld 1: een systeem herstel punt maken

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

Met deze opdracht maakt u een systeem herstel punt met de naam Install Mijntoep.
Het standaard APPLICATION_INSTALL herstel punt type wordt gebruikt.

### Voor beeld 2: een systeem MODIFY_SETTINGS herstel punt maken

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

Met deze opdracht maakt u een MODIFY_SETTINGS systeem herstel punt met de naam ' ChangeNetSettings '.

## PARAMETERS

### -Beschrijving

Hiermee geeft u een beschrijvende naam op voor het herstel punt.
Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePointType

Hiermee geeft u het type herstel punt op.
De standaard waarde is APPLICATION_INSTALL.

De aanvaardbare waarden voor deze parameter zijn:

- APPLICATION_INSTALL
- APPLICATION_UNINSTALL
- DEVICE_DRIVER_INSTALL
- MODIFY_SETTINGS
- CANCELLED_OPERATION

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten pipeen naar `Checkpoint-Computer` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- Deze cmdlet gebruikt de methode **CreateRestorePoint** van de klasse **SystemRestore** met een **BEGIN_SYSTEM_CHANGE** gebeurtenis.
- Vanaf Windows 8 `Checkpoint-Computer` kan elke dag niet meer dan één systeem herstel punt maken. Als u probeert een nieuw herstel punt te maken voordat de periode van 24 uur is verstreken, genereert Windows Power shell de volgende fout:

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## GERELATEERDE KOPPELINGEN

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Herstellen-computer](Restore-Computer.md)
