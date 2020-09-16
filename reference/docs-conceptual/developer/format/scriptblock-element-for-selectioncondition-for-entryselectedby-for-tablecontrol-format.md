---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a23d3515749393e9f5a2053634a44d1a817ebf38
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783446"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)

Hiermee geeft u het script blok op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het tabel item gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (Format) script block-element voor SelectionCondition voor EntrySelectedBy

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
|[SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit tabel item.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één script blok of een eigenschaps naam worden opgegeven, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
