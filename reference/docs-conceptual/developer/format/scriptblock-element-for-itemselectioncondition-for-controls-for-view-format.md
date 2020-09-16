---
title: Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74b3e23005f595c4c550320849cac5b196e9d479
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787662"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries-element voor object voor weer gave (indeling) voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor de weer gave (indeling) ItemSelectionCondition element van ExpressionBinding voor besturings elementen voor weer gave (indeling) script block element voor ItemSelectionCondition for Controls (indeling)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
