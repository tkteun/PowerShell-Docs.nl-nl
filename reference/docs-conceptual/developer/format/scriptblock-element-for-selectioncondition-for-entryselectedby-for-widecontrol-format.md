---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
ms.openlocfilehash: 53d3eba9d453dbcc96afbe8f81a16b61573f2874
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651970"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true` , wordt voldaan aan de voor waarde en wordt de definitie van het grote item gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) script block-element voor SelectionCondition voor EntrySelectedBy

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
