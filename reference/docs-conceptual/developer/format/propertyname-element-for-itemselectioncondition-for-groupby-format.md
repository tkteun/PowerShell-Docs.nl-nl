---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: 9667a389ded33d0744f0f7f8d739635a8b21d98b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666107"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor GroupBy (Format) CustomItem-element voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor het element GroupBy (Format) voor ItemSelectionCondition voor GroupBy (indeling)

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
|[Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.

## <a name="see-also"></a>Zie ook

[Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
