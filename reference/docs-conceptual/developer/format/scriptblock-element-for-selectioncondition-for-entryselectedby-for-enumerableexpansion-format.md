---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 71fd969fd3e5c0a4e39762c9a026982a8ca2a9d1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785367"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (Format) script block-element voor SelectionCondition voor EntrySelectedBy (Format)

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
|[Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
