---
title: TableRowEntry-element voor TableRowEntries voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353681"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)

Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TableRowEntry` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee worden de objecten gedefinieerd waarvan de eigenschaps waarden worden weer gegeven in de rij.|
|[TableColumnItems-element voor TableRowEntry voor TableControl (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven.|
|[Omloop-element voor TableRowEntry voor TableControl (indeling)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Geeft aan dat de tekst die de kolom breedte overschrijdt wordt weer gegeven op de volgende regel.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableRowEntries-element voor TableControl (indeling)](./tablerowentries-element-for-tablecontrol-format.md)|Hiermee worden de rijen van de tabel gedefinieerd.|

## <a name="remarks"></a>Opmerkingen

Er moet een `TableColumnItems` element en één `EntrySelectedBy` element worden opgegeven.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `TableRowEntry`-element dat een rij definieert waarin de waarden van twee eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) worden weer gegeven.

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

[Een tabel weergave maken](./creating-a-table-view.md)

[EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableColumnItems-element voor TableRowEntry voor TableControl (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries-element voor TableControl (indeling)](./tablerowentries-element-for-tablecontrol-format.md)

[Omloop-element voor TableRowEntry voor TableControl (indeling)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
