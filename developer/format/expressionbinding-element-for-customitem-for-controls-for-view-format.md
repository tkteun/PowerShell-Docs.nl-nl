---
title: ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848417"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)

Definieert de gegevens die door het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) ExpressionBinding Element voor CustomItem voor besturingselementen voor weergave (indeling)

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
|[CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.|
|[EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de elementen van verzamelingen worden weergegeven.|
|[ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.|
|[PropertyName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven.|
|[ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
