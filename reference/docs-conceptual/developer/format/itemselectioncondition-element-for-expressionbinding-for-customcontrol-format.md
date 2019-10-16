---
title: ItemSelectionCondition-element voor ExpressionBinding voor CustomControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354458"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor View (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling) ItemSelectionCondition element voor expressie binding voor CustomControl voor weer gave (indeling)

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
|[Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (notatie](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
