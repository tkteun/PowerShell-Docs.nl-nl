---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 56bd04c9af74bdaa7a186a208fc15a67cb08b004
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772855"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding in de lijst gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition-element voor EntrySelectedBy voor List entry (Format) script block-element voor SelectionCondition voor List entry (Format)

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
|[SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven. (Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie voorwaarden kunnen worden gebruikt.)

Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over de andere onderdelen van een lijst weergave.

## <a name="see-also"></a>Zie ook

[Element List entry (indeling)](./listentry-element-for-listcontrol-format.md)

[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Lijst weergave](./creating-a-list-view.md)

[Voor waarden definiëren voor het gebruik van een weergave vermelding of een item](./defining-conditions-for-displaying-data.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
