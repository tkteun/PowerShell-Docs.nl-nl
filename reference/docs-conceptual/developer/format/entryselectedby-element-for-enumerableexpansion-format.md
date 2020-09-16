---
title: EntrySelectedBy-element voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 031bf10cfb1aed2c737fdd53fa4f20f025351d40
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783667"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>Het element EntrySelectedBy voor EnumerableExpansion (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie of de voor waarde die voor deze definitie moet worden gebruikt.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (indeling)

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
|[Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.|
|[Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van hoe verzamelings objecten worden uitgevouwen.|
|[Het element TypeName voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van hoe verzamelings objecten worden uitgevouwen.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EnumerableExpansion (opmaak)](./enumerableexpansion-element-format.md)|Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie vermelding opgeven. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` . Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Voorwaarden voor het weergeven van gegevens definiëren](./defining-conditions-for-displaying-data.md)

[Het element EnumerableExpansion (opmaak)](./enumerableexpansion-element-format.md)

[Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Het element TypeName voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
