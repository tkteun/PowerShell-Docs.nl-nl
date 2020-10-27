---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableRowEntries voor TableControl (opmaak)
description: Het element TableRowEntries voor TableControl (opmaak)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651470"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>Het element TableRowEntries voor TableControl (opmaak)

Hiermee worden de rijen van de tabel gedefinieerd.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableRowEntries` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableControl (opmaak)](./tablecontrol-element-format.md)|Definieert een tabel indeling voor een weer gave.|

## <a name="remarks"></a>Opmerkingen

U moet een of meer `TableRowEntry` elementen opgeven voor de tabel weergave. Er is geen maximum limiet voor het aantal `TableRowEntry` elementen dat kan worden toegevoegd en de volg orde hiervan is aanzienlijk.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `TableRowEntries` element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[Het element TableControl (opmaak)](./tablecontrol-element-format.md)

[TableRowEntry-element (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
