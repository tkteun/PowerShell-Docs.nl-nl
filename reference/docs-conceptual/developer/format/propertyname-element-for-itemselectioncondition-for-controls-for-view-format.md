---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 9fb7a21e19338dbf59dab14291e1b02736835040
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645820"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries-element voor object voor weer gave (indeling) voor besturings elementen voor weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor de weer gave (indeling) ItemSelectionCondition element van ExpressionBinding voor besturings elementen voor de weer gave (indeling) eigenschap naam van ItemSelectionCondition voor Controls (indeling)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.

## <a name="see-also"></a>Zie ook

[Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
