---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)
description: Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)
ms.openlocfilehash: 60d64b7c14b40e87825ada36e19f52a66fe8b6cb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659775"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)

Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableRowEntry` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee worden de objecten gedefinieerd waarvan de eigenschaps waarden worden weer gegeven in de rij.|
|[Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven.|
|[Omloop-element voor TableRowEntry voor TableControl (indeling)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Geeft aan dat de tekst die de kolom breedte overschrijdt wordt weer gegeven op de volgende regel.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableRowEntries voor TableControl (opmaak)](./tablerowentries-element-for-tablecontrol-format.md)|Hiermee worden de rijen van de tabel gedefinieerd.|

## <a name="remarks"></a>Opmerkingen

Er `TableColumnItems` moet één element en één `EntrySelectedBy` element worden opgegeven.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `TableRowEntry` element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.

```xml
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
```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Het element TableRowEntries voor TableControl (opmaak)](./tablerowentries-element-for-tablecontrol-format.md)

[Omloop-element voor TableRowEntry voor TableControl (indeling)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
