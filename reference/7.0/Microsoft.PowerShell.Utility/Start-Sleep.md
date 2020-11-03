---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: 535cad057db406eaa48259288e34da6da4ed1cbb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249498"
---
# Start-Sleep

## SAMENVATTING
Hiermee wordt de activiteit in een script of sessie onderbroken gedurende de opgegeven periode.

## SYNTAXIS

### Seconden (standaard instelling)

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### Milliseconden

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## BESCHRIJVING

De `Start-Sleep` cmdlet onderbreekt de activiteit in een script of sessie voor de opgegeven periode. U kunt deze gebruiken voor veel taken, zoals het wachten op het volt ooien of onderbreken van een bewerking voordat een bewerking wordt herhaald.

## VOORBEELDEN

### Voor beeld 1: alle opdrachten in de slaap stand gedurende 15 seconden

```powershell
Start-Sleep -s 15
```

### Voor beeld 2: alle opdrachten in de slaap stand gedurende 1,5 seconden

In dit voor beeld worden alle opdrachten in de sessie binnen een paar seconden in de slaap stand gemaakt.

```powershell
Start-Sleep -Seconds 1.5
```

## PARAMETERS

### -Milliseconden

Hiermee geeft u op hoe lang de resource in milliseconden slaap stand wordt gezet. De para meter kan worden afgekort tot **m**.

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Seconden

Hiermee geeft u op hoe lang de resource in seconden slaap stand heeft. U kunt de parameter naam weglaten of u kunt deze als **s** afkorten. Vanaf Power shell 6.2.0 accepteert deze para meter nu breuk waarden.

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. Int32

U kunt het aantal seconden door sluizen `Start-Sleep` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

- U kunt ook verwijzen naar `Start-Sleep` de ingebouwde alias `sleep` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.
- `Ctrl+C` afgebroken `Start-Sleep` .
  - `Ctrl+C` niet onderbroken `[Threading.Thread]::Sleep` . Zie voor meer informatie [thread. slaap methode](/dotnet/api/system.threading.thread.sleep).

## GERELATEERDE KOPPELINGEN
