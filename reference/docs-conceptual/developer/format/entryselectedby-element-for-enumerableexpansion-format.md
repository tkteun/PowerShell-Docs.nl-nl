---
title: EntrySelectedBy-element voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358992"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>Het element EntrySelectedBy voor EnumerableExpansion (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie of de voor waarde die voor deze definitie moet worden gebruikt.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.|
|[SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van hoe verzamelings objecten worden uitgevouwen.|
|[TypeName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van hoe verzamelings objecten worden uitgevouwen.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EnumerableExpansion-element (indeling)](./enumerableexpansion-element-format.md)|Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie vermelding opgeven. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een script het `true` evalueert. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Voor waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion-element (indeling)](./enumerableexpansion-element-format.md)

[SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[TypeName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
