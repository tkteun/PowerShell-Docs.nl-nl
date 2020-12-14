---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: c196d00359c9b20b5dc1fefc0ab2b94655703f6f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705931"
---
# Get-TraceSource

## SAMENVATTING
Hiermee haalt u Power shell-onderdelen op die worden geinstrumenteerd voor tracering.

## SYNTAXIS

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Get-TraceSource** haalt de tracerings bronnen voor Power shell-onderdelen op die momenteel in gebruik zijn.
U kunt de gegevens gebruiken om te bepalen welke Power shell-onderdelen u kunt traceren.
Bij tracering genereert het onderdeel gedetailleerde berichten over elke stap in de interne verwerking.
Ontwikkel aars gebruiken de tracerings gegevens om de gegevens stroom, uitvoering van Program ma's en fouten te bewaken.

De tracerings-cmdlets zijn ontworpen voor Power shell-ontwikkel aars, maar ze zijn beschikbaar voor alle gebruikers.

## VOORBEELDEN

### Voor beeld 1: tracerings bronnen op naam ophalen

```
PS C:\> Get-TraceSource -Name "*provider*"
```

Met deze opdracht worden alle tracerings bronnen opgehaald die de naam van de provider bevatten.

### Voor beeld 2: alle tracerings bronnen ophalen

```
PS C:\> Get-TraceSource
```

Met deze opdracht worden alle Power shell-onderdelen opgehaald die kunnen worden getraceerd.

## PARAMETERS

### -Name

Hiermee geeft u de tracerings bronnen op die moeten worden opgehaald.
Joker tekens zijn toegestaan.
De parameter naam *naam* is optioneel.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die de naam van een tracerings bron bevat, door sluizen als **Get-TraceSource**.

## UITVOER

### System. Management. Automation. PSTraceSource

**Get-TraceSource** retourneert objecten die de traceer bronnen vertegenwoordigen.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Set-TraceSource](Set-TraceSource.md)

[Tracering-opdracht](Trace-Command.md)

