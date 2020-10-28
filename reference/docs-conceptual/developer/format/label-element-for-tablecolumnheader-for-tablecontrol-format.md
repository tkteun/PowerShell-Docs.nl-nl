---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Label voor TableColumnHeader voor TableControl (opmaak)
description: Het element Label voor TableColumnHeader voor TableControl (opmaak)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667790"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Label voor TableColumnHeader voor TableControl (opmaak)

Hiermee wordt het label gedefinieerd dat boven aan een kolom wordt weer gegeven. Dit element wordt gebruikt bij het definiëren van een tabel weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weergave (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (Format) voor TableColumnHeader voor TableControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven. Voor elke kolom is slechts één label toegestaan.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnHeader-element voor TableHeaders voor TableControl (indeling)](./tablecolumnheader-element-format.md)|Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.|

## <a name="text-value"></a>Tekstwaarde

Geef de tekst op die boven aan de kolom van de tabel wordt weer gegeven. Er zijn geen beperkte tekens voor het kolom Label.

## <a name="remarks"></a>Opmerkingen

Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `TableColumnHeader` element waarvan het label ' kolom 1 ' is.

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
