---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 1dd2da57792cb3ad10453d9d0adc3ef51cf2305e
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249275"
---
# Get-UICulture

## SAMENVATTING
Hiermee worden de huidige instellingen voor de GEBRUIKERSINTERFACE cultuur in het besturings systeem opgehaald.

## SYNTAXIS

```
Get-UICulture [<CommonParameters>]
```

## BESCHRIJVING

De `Get-UICulture` cmdlet haalt informatie op over de huidige instellingen voor de cultuur van gebruikers interface (UI) voor Windows.
De GEBRUIKERSINTERFACE cultuur bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten.

U kunt ook de `Get-Culture` cmdlet gebruiken, waarmee de huidige cultuur op het systeem wordt opgehaald.
De cultuur bepaalt de weergave opmaak van items zoals getallen, valuta en datums.

## VOORBEELDEN

### Voor beeld 1: de UI-cultuur ophalen

```powershell
Get-UICulture
```

Met deze opdracht wordt de huidige UI-cultuur gegevens opgehaald.

### Voor beeld 2: de UI-cultuur ophalen en de resultaten opmaken

```powershell
Get-UICulture | Format-List *
```

Met deze opdracht worden de waarden van alle eigenschappen van de huidige GEBRUIKERSINTERFACE cultuur in een lijst weer gegeven.

### Voor beeld 3: de waarde van de eigenschap Calendar ophalen

```powershell
(Get-UICulture).Calendar
```

Met deze opdracht worden de huidige waarden weer gegeven voor de eigenschap **Calendar** van de huidige gebruikersinterface cultuur.
Calendar is slechts één eigenschap van UI-cultuur.
Als u alle eigenschappen wilt weer geven, typt u `Get-UICulture | Get-Member` .

### Voor beeld 4: het korte datum patroon ophalen

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

Met deze opdracht wordt het korte datum patroon voor de huidige GEBRUIKERSINTERFACE cultuur weer gegeven.
Als u alle subeigenschappen van de eigenschap **date time format** van de UI-cultuur wilt weer geven, typt u `(Get-UICulture).DateTimeFormat | gm` .

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Globalization. Culture info, micro soft. Power shell. VistaCultureInfo

`Get-UICulture` retourneert een object dat de huidige GEBRUIKERSINTERFACE cultuur vertegenwoordigt.
In Windows Power Shell 3,0 wordt een **Culture info** -object geretourneerd.
In Windows Power Shell 2,0 wordt een **VistaCultureInfo** -object geretourneerd.

## OPMERKINGEN

- U kunt ook de `$PsCulture` variabelen en gebruiken `$PsUICulture` . De `$PsCulture` variabele bevat de naam van de huidige cultuur en de `$PsUICulture` variabele bevat de naam van de huidige gebruikersinterface cultuur.

## GERELATEERDE KOPPELINGEN
