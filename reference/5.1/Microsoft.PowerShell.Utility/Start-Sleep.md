---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 3/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4add39c09b6123aaf8c9302529346a6b1dec391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250363"
---
# Start-Sleep

## SAMENVATTING
Hiermee wordt de activiteit in een script of sessie onderbroken gedurende de opgegeven periode.

## SYNTAXIS

### Seconden (standaard instelling)

```
Start-Sleep [-Seconds] <Int32> [<CommonParameters>]
```

### Milliseconden

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## BESCHRIJVING

De `Start-Sleep` cmdlet onderbreekt de activiteit in een script of sessie voor de opgegeven periode.
U kunt deze gebruiken voor veel taken, zoals het wachten op het volt ooien of onderbreken van een bewerking voordat een bewerking wordt herhaald.

## VOORBEELDEN

### Voor beeld 1: alle opdrachten in de slaap stand gedurende 15 seconden

```powershell
Start-Sleep -s 15
```

Met deze opdracht worden alle opdrachten in de sessie-slaap stand 15 seconden.

### Voor beeld 2: alle opdrachten in de slaap stand zetten

```powershell
Start-Sleep -m 500
```

Met deze opdracht worden alle opdrachten in de sessie-slaap stand voor een helft van een seconde (500 milliseconden).

## PARAMETERS

### -Milliseconden

Hiermee geeft u op hoe lang de resource in milliseconden slaap stand wordt gezet.
De para meter kan worden afgekort tot **m**.

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Seconden

Hiermee geeft u op hoe lang de resource in seconden slaap stand heeft.
U kunt de parameter naam ( **seconden** ) weglaten, of u kunt deze afkorten als **s**.

```yaml
Type: System.Int32
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
