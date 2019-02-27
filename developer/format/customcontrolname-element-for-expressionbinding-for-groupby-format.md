---
title: CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845617"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)

Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling) CustomControlName Element voor ExpressionBinding voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControlName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definieert de gegevens die door het besturingselement wordt weergegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturingselement.

## <a name="remarks"></a>Opmerkingen

Kunt u algemene besturingselementen die kunnen worden gebruikt door alle weergaven van een opmaak bestand maken en u kunt besturingselementen weergeven die kunnen worden gebruikt door een specifieke weergave maken. De volgende elementen geeft de namen van deze besturingselementen:

- [Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
