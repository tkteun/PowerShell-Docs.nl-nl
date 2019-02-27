---
title: TableHeaders-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847423"
---
# <a name="tableheaders-element-format"></a>Het element TableHeaders (opmaak)

Hiermee definieert u de koptekst van de kolommen van een tabel.

ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders-Element voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en de bovenliggende elementen van de `TableHeaders` element. Er moet een onderliggend element voor elke eigenschap van het object dat moet worden weergegeven. De kolom header-informatie wordt weergegeven in de volgorde die de onderliggende elementen worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnHeader-Element (indeling)](./tablecolumnheader-element-format.md)|Optioneel element.<br /><br /> Definieert het label, de breedte en de uitlijning van de gegevens voor een kolom van een tabelweergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableControl-Element (indeling)](./tablecontrol-element-format.md)|Hiermee definieert u een tabelindeling voor een weergave.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `TableHeaders` element dat twee kolomkoppen definieert.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[TableColumnHeader-Element (indeling)](./tablecolumnheader-element-format.md)

[TableControl-Element (indeling)](./tablecontrol-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
