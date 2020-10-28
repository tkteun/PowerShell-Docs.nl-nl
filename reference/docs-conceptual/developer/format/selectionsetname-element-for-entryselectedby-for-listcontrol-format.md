---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651836"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)

Hiermee geeft u een set .NET-objecten voor de lijst vermelding op. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionSetName element voor de List entry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten. Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een vermelding van een lijst weergave.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
