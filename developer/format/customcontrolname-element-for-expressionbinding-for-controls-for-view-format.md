---
title: CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066648"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) ExpressionBinding Element voor CustomItem voor besturingselementen voor weergave (indeling) CustomControlName Element voor ExpressionBindine voor besturingselementen voor weergave (indeling)

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
|[ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definieert de gegevens die door het besturingselement wordt weergegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturingselement.

## <a name="remarks"></a>Opmerkingen

Kunt u algemene besturingselementen die kunnen worden gebruikt door alle weergaven van een opmaak bestand maken en u kunt besturingselementen weergeven die kunnen worden gebruikt door een specifieke weergave maken. De volgende elementen geeft de namen van deze besturingselementen:

- [Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
