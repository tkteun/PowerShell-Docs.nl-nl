---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableHeaders (opmaak)
description: Het element TableHeaders (opmaak)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659828"
---
# <a name="tableheaders-element-format"></a>Het element TableHeaders (opmaak)

Hiermee worden de kopteksten van de kolommen van een tabel gedefinieerd.

ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het `TableHeaders` element beschreven. Er moet een onderliggend element zijn voor elke eigenschap van het object dat moet worden weer gegeven. De informatie in de kolomkop wordt weer gegeven in de volg orde waarin de onderliggende elementen zijn opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableColumnHeader (opmaak)](./tablecolumnheader-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u het label, de breedte en de uitlijning van de gegevens voor een kolom van een tabel weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableControl (opmaak)](./tablecontrol-element-format.md)|Definieert een tabel indeling voor een weer gave.|

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `TableHeaders` element dat twee kolom koppen definieert.

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

[Een tabelweergave maken](./creating-a-table-view.md)

[Het element TableColumnHeader (opmaak)](./tablecolumnheader-element-format.md)

[Het element TableControl (opmaak)](./tablecontrol-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
