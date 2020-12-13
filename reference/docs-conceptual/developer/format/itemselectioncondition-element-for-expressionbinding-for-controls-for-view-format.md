---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648060"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het ExpressionBinding-element van de CustomItem voor besturings elementen voor weer gave (opmaak) ItemSelectionCondition element van ExpressionBinding voor besturings elementen voor weer gave (indeling)

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
|[Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
