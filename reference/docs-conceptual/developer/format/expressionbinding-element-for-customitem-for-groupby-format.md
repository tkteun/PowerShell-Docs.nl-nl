---
title: ExpressionBinding-element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358960"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)

Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (indeling) CustomItem voor CustomEntry voor GroupBy (Format) ExpressionBinding-element voor CustomItem voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ExpressionBinding` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomControl Element`|Optioneel element.<br /><br /> Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.|
|[CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.|
|[EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)|Optioneel element.<br /><br /> Opgegeven dat de elementen van verzamelingen worden weer gegeven.|
|[ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|
|[Het element PropertyName voor ExpressionBinding voor GroupBy (indeling)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.|
|[Script block-element voor ExpressionBinding voor GroupBy (indeling)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)|Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|

## <a name="see-also"></a>Zie ook

[CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Het element PropertyName voor ExpressionBinding voor GroupBy (indeling)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Script block-element voor ExpressionBinding voor GroupBy (indeling)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[CustomItem-element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
