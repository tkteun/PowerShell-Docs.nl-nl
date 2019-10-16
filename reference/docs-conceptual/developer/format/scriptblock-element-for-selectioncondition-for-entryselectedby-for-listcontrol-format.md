---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358926"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de vermelding in de lijst gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) voor List entry (Format) SelectionCondition element voor EntrySelectedBy voor List entry (Format) script block-element voor SelectionCondition voor EntrySelectedBy voor List entry (Format)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.|

## <a name="text-value"></a>Tekst waarde

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
