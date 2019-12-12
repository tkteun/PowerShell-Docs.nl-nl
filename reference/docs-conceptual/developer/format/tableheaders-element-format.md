---
title: TableHeaders-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353695"
---
# <a name="tableheaders-element-format"></a>Het element TableHeaders (opmaak)

Hiermee worden de kopteksten van de kolommen van een tabel gedefinieerd.

ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het element `TableHeaders` beschreven. Er moet een onderliggend element zijn voor elke eigenschap van het object dat moet worden weer gegeven. De informatie in de kolomkop wordt weer gegeven in de volg orde waarin de onderliggende elementen zijn opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnHeader-element (indeling)](./tablecolumnheader-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u het label, de breedte en de uitlijning van de gegevens voor een kolom van een tabel weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableControl-element (indeling)](./tablecontrol-element-format.md)|Definieert een tabel indeling voor een weer gave.|

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `TableHeaders`-element waarmee twee kolom koppen worden gedefinieerd.

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

[Een tabel weergave maken](./creating-a-table-view.md)

[TableColumnHeader-element (indeling)](./tablecolumnheader-element-format.md)

[TableControl-element (indeling)](./tablecontrol-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
