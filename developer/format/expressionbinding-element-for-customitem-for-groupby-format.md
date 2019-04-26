---
title: ExpressionBinding-Element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065900"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)

Definieert de gegevens die door het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling)

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

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ExpressionBinding` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|`CustomControl Element`|Optioneel element.<br /><br /> Hiermee definieert u een besturingselement dat wordt gebruikt door dit besturingselement.|
|[CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.|
|[EnumerateCollection-Element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection-Element voor ExpressionBinding voor GroupBy (indeling)|Optioneel element.<br /><br /> Opgegeven dat de elementen van verzamelingen worden weergegeven.|
|[ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.|
|[PropertyName-Element voor ExpressionBinding voor GroupBy (indeling)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven.|
|[ScriptBlock-Element voor ExpressionBinding voor GroupBy (indeling)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)|Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.|

## <a name="see-also"></a>Zie ook

[CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[EnumerateCollection-Element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-Element voor ExpressionBinding voor GroupBy (indeling)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[ScriptBlock-Element voor ExpressionBinding voor GroupBy (indeling)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[CustomItem-Element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
