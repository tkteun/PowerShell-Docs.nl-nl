---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)
description: Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655297"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)

Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomControl Element`|Optioneel element.<br /><br /> Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.|
|[Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.|
|[EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)|Optioneel element.<br /><br /> Opgegeven dat de elementen van verzamelingen worden weer gegeven.|
|[Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|
|[Het element PropertyName voor ExpressionBinding voor GroupBy (opmaak)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.|
|[Het element ScriptBlock voor ExpressionBinding voor GroupBy (opmaak)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomItem voor CustomEntry voor GroupBy (opmaak)](./customitem-element-for-customentry-for-groupby-format.md)|Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|

## <a name="see-also"></a>Zie ook

[Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Het element EnumerateCollection voor ExpressionBinding voor GroupBy (opmaak)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Het element PropertyName voor ExpressionBinding voor GroupBy (opmaak)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Het element ScriptBlock voor ExpressionBinding voor GroupBy (opmaak)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Het element CustomItem voor CustomEntry voor GroupBy (opmaak)](./customitem-element-for-customentry-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
