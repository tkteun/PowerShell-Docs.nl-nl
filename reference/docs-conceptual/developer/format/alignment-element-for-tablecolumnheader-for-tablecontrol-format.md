---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)
description: Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)
ms.openlocfilehash: cf8b90c12c28951283b5870186e2c88d427318a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666821"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)

Hiermee wordt gedefinieerd hoe de gegevens in een kolomkop worden weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableHeaders element (indeling) TableColumnHeader element (indeling) uitlijning element voor TableColumnHeader (indeling)

## <a name="syntax"></a>Syntax

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Alignment` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableColumnHeader (opmaak)](./tablecolumnheader-element-format.md)|Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.|

## <a name="text-value"></a>Tekstwaarde

Geef een van de volgende waarden op. Deze waarden zijn niet hoofdlettergevoelig.

Hiermee worden de gegevens links uitgelijnd die worden weer gegeven in de kolom links dit is de standaard waarde als dit element niet is opgegeven.

Hiermee worden de gegevens die worden weer gegeven in de kolom aan de rechter kant uitgelijnd.

Centreert de gegevens die in de kolom worden weer gegeven.

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `TableColumnHeader` element waarvan de gegevens aan de linkerkant worden uitgelijnd.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[Het element TableColumnHeader (opmaak)](./tablecolumnheader-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
