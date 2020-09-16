---
title: TableColumnItems-element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 661b938e8db0e68e10dc05f552e4f3a14608bc55
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785146"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)

Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden in een rij worden weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weergave (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (Format) TableColumnItems-element voor TableControlEntry voor TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnItems` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een kolom van de rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.|

## <a name="remarks"></a>Opmerkingen

Een `TableColumnItem` element is vereist voor elke kolom van de rij. De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `TableColumnItems` element dat drie eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) definieert.

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[TableColumnItem-element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry-element (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
