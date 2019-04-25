---
title: PropertyName-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064863"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)

Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling) ExpressionBinding Element voor CustomItem voor CustomControl voor weergave (indeling) ItemSelectionCondition Element voor de Binding van de expressie voor CustomControl voor PropertyName-Element voor ItemSelectionCondition voor weergave (indeling) CustomControl voor weergave (indeling

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
|[ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de .NET-eigenschap die de voorwaarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element bij het definiëren van de selectievoorwaarde.

## <a name="see-also"></a>Zie ook

[ScriptBlock-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
