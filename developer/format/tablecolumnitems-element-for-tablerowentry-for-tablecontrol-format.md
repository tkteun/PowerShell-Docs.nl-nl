---
title: TableColumnItems-Element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056903"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Het element TableColumnItems voor TableRowEntry voor TableControl (opmaak)

Definieert de eigenschappen of scripts waarvan de waarden in een rij worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries Element voor TableControl (indeling) TableRowEntry-Element voor TableRowEntries voor TableControl (indeling) TableColumnItems-Element voor TableControlEntry voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `TableColumnItems` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnItem-Element voor TableColumnItems voor TableControl (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Vereist element.<br /><br /> Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een kolom van de rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableRowEntry-Element voor TableRowEntries voor TableControl (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|De gegevens die worden weergegeven in een rij van de tabel definieert.|

## <a name="remarks"></a>Opmerkingen

Een `TableColumnItem` element is vereist voor elke kolom van de rij. De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `TableColumnItems` element dat drie eigenschappen van bepaalt de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

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

[Het maken van een tabelweergave](./creating-a-table-view.md)

[TableColumnItem-Element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry Element (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
