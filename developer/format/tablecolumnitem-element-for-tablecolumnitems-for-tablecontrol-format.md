---
title: TableColumnItem-Element voor TableColumnItems voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851301"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)

Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries Element voor TableControl (indeling) TableRowEntry-Element voor TableRowEntries voor TableControl (indeling) TableColumnItems-Element voor TableControlEntry voor TableControl (indeling) TableColumnItem Element voor TableColumnItems voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `TableColumnItem` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Uitlijning-Element voor TableColumnItem voor TableControl (indeling)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u hoe de gegevens in een kolom van de rij worden weergegeven.|
|[FormatString-Element voor TableColumnItem voor TableControl (indeling)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Hiermee geeft u een indeling-patroon dat wordt gebruikt om de opmaak van de gegevens in de kolom van de rij.|
|[PropertyName-Element voor TableColumnItem voor TableControl (indeling)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam van de eigenschap waarvan de waarde wordt weergegeven.|
|[ScriptBlock-Element voor TableColumnItem voor TableControl (indeling)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script waarvan de waarde wordt weergegeven in de kolom van een rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnItems-Element voor TableControlEntry voor TableControl (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definieert de eigenschappen of scripts waarvan de waarden worden weergegeven in de rij.|

## <a name="remarks"></a>Opmerkingen

U kunt een eigenschap van een object of een script opgeven in elke kolom van de rij. Als er geen onderliggende elementen zijn opgegeven, wordt het item is een tijdelijke aanduiding en worden geen gegevens weergegeven.

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `TableColumnItem` element waarin de waarde van de `Status` eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Uitlijning-Element voor TableColumnItem voor TableControl (indeling)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems-Element (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString-Element voor TableColumnItem voor TableControl (indeling)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName-Element voor TableColumnItem voor TableControl (indeling)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[ScriptBlock-Element voor TableColumnItem voor TableControl (indeling)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
