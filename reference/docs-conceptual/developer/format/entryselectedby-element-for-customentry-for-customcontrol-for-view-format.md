---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655351"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.|
|[SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van de beheer weergave.|
|[TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de controle weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Hiermee worden de besturings elementen gedefinieerd die worden gebruikt door specifieke .NET-objecten.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde voor een vermelding opgeven. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die moet bestaan voor het gebruik van de vermelding, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` . Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

Zie [aangepaste besturings elementen weer geven](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Aangepaste besturings elementen weer geven](./creating-custom-controls.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
