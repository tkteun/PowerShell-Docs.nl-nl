---
title: TableColumnItems-element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353688"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)

Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden in een rij worden weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling) TableColumnItems-element voor TableControlEntry voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TableColumnItems` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnItem-element voor TableColumnItems voor TableControl (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een kolom van de rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableRowEntry-element voor TableRowEntries voor TableControl (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.|

## <a name="remarks"></a>Opmerkingen

Voor elke kolom van de rij is een `TableColumnItem`-element vereist. De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `TableColumnItems`-element dat drie eigenschappen van het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object definieert.

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

[Een tabel weergave maken](./creating-a-table-view.md)

[TableColumnItem-element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry-element (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
