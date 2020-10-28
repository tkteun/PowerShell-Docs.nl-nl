---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)
ms.openlocfilehash: 7ebe5d884061243c8b4af196788187d84c15a92e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651843"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)

Hiermee geeft u een set .NET-objecten voor de lijst vermelding op. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)

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
|[Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Voor elke aangepaste besturings definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.

## <a name="see-also"></a>Zie ook

[Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Aangepaste besturingselementen maken](./creating-custom-controls.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
