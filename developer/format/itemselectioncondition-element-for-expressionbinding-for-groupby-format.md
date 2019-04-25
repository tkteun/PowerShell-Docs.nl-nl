---
title: ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065458"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)

Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor een controle-item. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling) ItemSelectionCondition Element voor ExpressionBinding voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ItemSelectionCondition` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[PropertyName-Element voor ItemSelectionCondition voor GroupBy (indeling)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.|
|[ScriptBlock-Element voor ItemSelectionCondition voor GroupBy (indeling)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definieert de gegevens die door het besturingselement wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)
