---
title: ItemSelectionCondition-Element voor ExpressionBinding voor CustomControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065815"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)

Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor een controle-item. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling) ExpressionBinding Element voor CustomItem voor CustomControl voor weergave (indeling) ItemSelectionCondition Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)

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
|[PropertyName-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.|
|[ScriptBlock-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Definieert de gegevens die door het besturingselement wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
