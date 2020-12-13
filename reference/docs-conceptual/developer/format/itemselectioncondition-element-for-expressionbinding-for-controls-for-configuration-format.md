---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 6bd3d386ba64b33a1744fcc9e602cf13404765a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648086"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor Configuration (Format) CustomEntry element voor het CustomItem-element van de configuratie (indeling) voor CustomEntry voor besturings elementen voor de configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
