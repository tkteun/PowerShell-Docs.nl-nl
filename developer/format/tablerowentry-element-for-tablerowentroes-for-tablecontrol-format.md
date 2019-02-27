---
title: TableRowEntry-Element voor TableRowEntroes voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845120"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a>Het element TableRowEntry voor TableRowEntries voor TableControl (opmaak)

De gegevens die worden weergegeven in een rij van de tabel definieert.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries Element voor TableControl (indeling) TableRowEntry-Element voor TableRowEntries voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `TableRowEntry` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor TableRowEntry voor TableControl (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Vereist element.<br /><br /> Definieert de objecten waarvan de de eigenschapwaarden worden weergegeven in de rij.|
|[TableColumnItems-Element voor TableRowEntry voor TableControl (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Vereist element.<br /><br /> Definieert de eigenschappen of scripts waarvan de waarden worden weergegeven.|
|[Het inpakken van Element voor TableRowEntry voor TableCntrol (indeling)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de tekst die langer is dan de breedte van de kolom wordt weergegeven op de volgende regel.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableRowEntries-Element voor TableControl (indeling)](./tablerowentries-element-for-tablecontrol-format.md)|Hiermee definieert u de rijen van de tabel.|

## <a name="remarks"></a>Opmerkingen

Een `TableColumnItems` -element en een `EntrySelectedBy` element moet worden opgegeven.

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `TableRowEntry` element dat definieert een rij waarin de waarden van twee eigenschappen van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

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

[Het maken van een tabelweergave](./creating-a-table-view.md)

[EntrySelectedBy-Element voor TableRowEntry voor TableControl (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableColumnItems-Element voor TableRowEntry voor TableControl (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries-Element voor TableControl (indeling)](./tablerowentries-element-for-tablecontrol-format.md)

[TableRowEntry-Element voor TableRowEntries voor TableControl (indeling)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Het inpakken van Element voor TableRowEntry voor TableCntrol (indeling)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
