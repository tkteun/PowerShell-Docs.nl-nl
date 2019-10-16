---
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355921"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Als deze eigenschap aanwezig is of als deze wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het tabel item gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy-element voor TableRowEntry (indeling) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling) Property element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit tabel item.|

## <a name="text-value"></a>Tekst waarde

Geef de .NET-eigenschaps naam op.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script blok worden opgegeven, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="see-also"></a>Zie ook

[Een tabel weergave maken](./creating-a-table-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
