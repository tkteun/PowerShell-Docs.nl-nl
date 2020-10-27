---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)
description: Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645905"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)

Hiermee worden de .NET-typen gedefinieerd die gebruikmaken van deze definitie van de tabel weergave of de voor waarde die voor deze definitie moet worden gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling)

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
|[Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze tabel weergave definitie.|
|[Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze tabel weergave definitie.|
|[Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze tabel weergave definitie.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableRowEntry-element voor TableControl (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een tabel weergave definitie. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` . Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `TableRowEntry` element dat wordt gebruikt om de eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry-element voor TableControl (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
