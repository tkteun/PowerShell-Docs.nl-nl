---
title: TableRowEntries-element voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358788"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>Het element TableRowEntries voor TableControl (opmaak)

Hiermee worden de rijen van de tabel gedefinieerd.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TableRowEntries` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableRowEntry-element voor TableRowEntries voor TableControl (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableControl-element (indeling)](./tablecontrol-element-format.md)|Definieert een tabel indeling voor een weer gave.|

## <a name="remarks"></a>Opmerkingen

U moet een of meer elementen van het @no__t 0 opgeven voor de tabel weergave. Er is geen maximum limiet voor het aantal `TableRowEntry`-elementen dat kan worden toegevoegd, en de volg orde is belang rijk.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `TableRowEntries`-element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.

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

[Een tabel weergave maken](./creating-a-table-view.md)

[TableControl-element (indeling)](./tablecontrol-element-format.md)

[TableRowEntry-element (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
