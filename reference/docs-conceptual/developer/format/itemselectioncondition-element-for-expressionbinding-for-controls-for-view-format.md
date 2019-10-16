---
title: ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354479"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ItemSelectionCondition` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
