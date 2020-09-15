---
title: ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a9b74f1882efc578f7d9ab27b8cd2f8a52833ab8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773433"
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
