---
title: TableColumnItem-element voor TableColumnItems voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143585"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)

Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableRowEntries element voor TableControl (Format) TableRowEntry-element voor TableRowEntries voor TableControl (indeling) TableColumnItems-element voor TableControlEntry voor TableControl (Format) TableColumnItem element voor TableColumnItems voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van `TableColumnItem` het element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Alignment-element voor TableColumnItem voor TableControl (indeling)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Bepaalt hoe de gegevens in een kolom van de rij worden weer gegeven.|
|[Element formats Tring voor TableColumnItem voor TableControl (indeling)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Geeft een indelings patroon aan dat wordt gebruikt om de gegevens in de kolom van de rij op te maken.|
|[Het element PropertyName voor TableColumnItem voor TableControl (indeling)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van de eigenschap waarvan de waarde wordt weer gegeven.|
|[Script block-element voor TableColumnItem voor TableControl (indeling)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de kolom van een rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnItems-element voor TableControlEntry voor TableControl (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven in de rij.|

## <a name="remarks"></a>Opmerkingen

U kunt een eigenschap van een object of een script in elke kolom van de rij opgeven. Als er geen onderliggende elementen zijn opgegeven, is het item een tijdelijke aanduiding en worden er geen gegevens weer gegeven.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld `TableColumnItem` ziet u een-element dat de `Status` waarde van de eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weergeeft.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Zie ook

[Een tabel weergave maken](./creating-a-table-view.md)

[Alignment-element voor TableColumnItem voor TableControl (indeling)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems-element (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Element formats Tring voor TableColumnItem voor TableControl (indeling)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Het element PropertyName voor TableColumnItem voor TableControl (indeling)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Script block-element voor TableColumnItem voor TableControl (indeling)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
