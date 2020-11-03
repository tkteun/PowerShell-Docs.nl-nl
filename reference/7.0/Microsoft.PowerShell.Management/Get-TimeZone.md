---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 4ed02426fbce279adc3f30af0c95b11966fe75a5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249703"
---
# Get-TimeZone

## SAMENVATTING
Hiermee wordt de huidige tijd zone of een lijst met beschik bare tijd zones opgehaald.

## SYNTAXIS

### Naam (standaard)

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### Id

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### ListAvailable

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Get-time** zone wordt de huidige tijdzone of een lijst met beschik bare tijd zones opgehaald.

## VOORBEELDEN

### Voor beeld 1: de huidige tijd zone ophalen

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

Met deze opdracht wordt de huidige tijd zone opgehaald.

### Voor beeld 2: tijd zones ophalen die overeenkomen met een opgegeven teken reeks

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

Met deze opdracht worden alle tijd zones opgehaald die overeenkomen met het opgegeven Joker teken.

### Voor beeld 3: alle beschik bare tijd zones ophalen

```
PS C:\> Get-TimeZone -ListAvailable
```

Met deze opdracht worden alle beschik bare tijd zones opgehaald.

## PARAMETERS

### -Id

Hiermee geeft u als een teken reeks matrix de ID of Id's op van de tijd zones die met deze cmdlet worden opgehaald.

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

Geeft aan dat met deze cmdlet alle beschik bare tijd zones worden opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u als een teken reeks matrix de naam of namen op van de tijd zones die met deze cmdlet worden opgehaald.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System.String[]

## UITVOER

### System. time zone info []

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Set-tijd zone](Set-TimeZone.md)
