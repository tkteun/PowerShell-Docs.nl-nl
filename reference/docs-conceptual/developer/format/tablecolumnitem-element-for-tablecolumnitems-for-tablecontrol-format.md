---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)
description: Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)
ms.openlocfilehash: 8ef5158c9bb9f074d5c58190d4d3b20c10c83744
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659853"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)

Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (Format) TableColumnItems-element voor TableControlEntry voor TableControl (Format) TableColumnItem-element voor TableColumnItems voor TableControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnItem` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Uitlijning voor TableColumnItem voor TableControl (opmaak)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Bepaalt hoe de gegevens in een kolom van de rij worden weer gegeven.|
|[Het element FormatString voor TableColumnItem voor TableControl (opmaak)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Geeft een indelings patroon aan dat wordt gebruikt om de gegevens in de kolom van de rij op te maken.|
|[Het element PropertyName voor TableColumnItem voor TableControl (opmaak)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van de eigenschap waarvan de waarde wordt weer gegeven.|
|[Het element ScriptBlock voor TableColumnItem voor TableControl (opmaak)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de kolom van een rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnItems-element voor TableControlEntry voor TableControl (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven in de rij.|

## <a name="remarks"></a>Opmerkingen

U kunt een eigenschap van een object of een script in elke kolom van de rij opgeven. Als er geen onderliggende elementen zijn opgegeven, is het item een tijdelijke aanduiding en worden er geen gegevens weer gegeven.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `TableColumnItem` element dat de waarde van de `Status` eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weergeeft.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[Het element Uitlijning voor TableColumnItem voor TableControl (opmaak)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems-element (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Het element FormatString voor TableColumnItem voor TableControl (opmaak)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Het element PropertyName voor TableColumnItem voor TableControl (opmaak)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Het element ScriptBlock voor TableColumnItem voor TableControl (opmaak)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
