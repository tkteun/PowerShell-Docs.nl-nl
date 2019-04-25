---
title: PropertyName-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064888"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor ExpressionBinding, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling) ItemSelectionCondition-Element voor ExpressionBinding controles voor configuratie (-indeling) PropertyName-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling)

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
|[ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de .NET-eigenschap die de voorwaarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element bij het definiëren van de selectievoorwaarde.

## <a name="see-also"></a>Zie ook

[ScriptBlock-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
