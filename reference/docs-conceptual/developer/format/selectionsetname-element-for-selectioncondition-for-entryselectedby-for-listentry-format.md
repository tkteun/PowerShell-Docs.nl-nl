---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651550"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)

Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition-element voor EntrySelectedBy voor List entry (Format) SelectionSetName-element voor SelectionCondition voor List entry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan om deze definitie van de lijst weergave te gebruiken.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven. Zie voor [waarden defini??ren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd. Zie [sets van objecten defini??ren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Voor waarden defini??ren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
