---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor TableColumnItem voor TableControl (opmaak)
description: Het element PropertyName voor TableColumnItem voor TableControl (opmaak)
ms.openlocfilehash: e83bbdb96d2755013cb9fe065cb98731ba44917f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665580"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>Het element PropertyName voor TableColumnItem voor TableControl (opmaak)

Hiermee geeft u de eigenschap op waarvan de waarde wordt weer gegeven in de kolom van de rij.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (indeling) element eigenschap van TableColumnItem (indeling)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnItem-element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `TableColumnItem` element dat de `Status` eigenschap van het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object aangeeft.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[TableColumnItem-element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
