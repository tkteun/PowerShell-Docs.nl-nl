---
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca2106dbbd8da345e71e83a3ead3cf7a1cb44cb4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773110"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition element voor EntrySelectedBy voor WideEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de .NET-eigenschaps naam op.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script worden opgegeven om te evalueren, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
