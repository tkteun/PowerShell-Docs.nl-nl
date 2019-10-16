---
title: ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354465"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)

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
|[Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
