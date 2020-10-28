---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Breedte voor TableColumnHeader voor TableControl (opmaak)
description: Het element Breedte voor TableColumnHeader voor TableControl (opmaak)
ms.openlocfilehash: bde84f1d33b3d6b3b8c4462f870f978611cb434b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658259"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Breedte voor TableColumnHeader voor TableControl (opmaak)

Hiermee wordt de breedte (in tekens) van een kolom gedefinieerd.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableHeaders element voor TableControl (indeling) TableColumnHeader element TableHeaders voor TableControl (indeling) breedte-element voor TableColumnHeader voor TableControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Width` element beschreven die worden gebruikt bij het definiëren van kolom koppen.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnHeader-element voor TableHeaders voor TableControl (indeling)](./tablecolumnheader-element-format.md)|Hiermee definieert u een label, breedte en uitlijning van de gegevens voor een kolom van de tabel.|

## <a name="text-value"></a>Tekstwaarde

Als dat mogelijk is, geeft u een breedte (in tekens) op die groter is dan de lengte van de weer gegeven eigenschaps waarden.

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `TableColumnHeader` element waarvan de breedte 16 tekens is.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[TableColumnHeader-element voor TableHeader voor TableControl (indeling)](./tablecolumnheader-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
