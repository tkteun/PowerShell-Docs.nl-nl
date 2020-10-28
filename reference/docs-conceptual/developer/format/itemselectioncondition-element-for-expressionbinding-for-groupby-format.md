---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651980"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor GroupBy (Format)

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
|[Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)

[Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)](./expressionbinding-element-for-customitem-for-groupby-format.md)
