---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 29b0574a95d81962fb3f72a526f89273baeea647
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660270"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) Controls-element (opmaak) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor object voor weer gave (Format) voor de weer gave (Format) voor het EntrySelectedBy-element voor Controls (indeling)

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
|[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.|
|[Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element.|
|[Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Biedt een definitie van het besturings element.|

## <a name="remarks"></a>Opmerkingen

Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script wordt geëvalueerd `true` . Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
