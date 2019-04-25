---
title: PropertyName-Element voor ItemSelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064761"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)

Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling) ItemSelectionCondition Element voor ExpressionBinding voor PropertyName-Element voor GroupBy (indeling) ItemSelectionCondition voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de .NET-eigenschap die de voorwaarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element bij het definiëren van de selectievoorwaarde.

## <a name="see-also"></a>Zie ook

[ScriptBlock-Element voor ItemSelectionCondition voor GroupBy (indeling)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
