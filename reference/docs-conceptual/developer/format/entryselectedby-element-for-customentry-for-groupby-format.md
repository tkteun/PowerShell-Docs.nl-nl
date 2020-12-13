---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)
ms.openlocfilehash: 5af4abe081ca268699d281a1b586a584107b9a83
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652359"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor het object CustomControl voor GroupBy (Format) EntrySelectedBy voor CustomEntry voor GroupBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven. U moet ten minste één type, selectieset of selectie voorwaarde voor een definitie opgeven. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.|
|[Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.|
|[Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)](./typename-element-for-entryselectedby-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomControl voor GroupBy (opmaak)](./customentry-element-for-customcontrol-for-groupby-format.md)|Biedt een definitie van het besturings element.|

## <a name="remarks"></a>Opmerkingen

Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` . Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
