---
title: Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354157"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Als deze eigenschap aanwezig is of als deze wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor de eigenschap element van de weer gave (Format) voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekst waarde

Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.

## <a name="see-also"></a>Zie ook

[Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
