---
title: CustomControlName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066614"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)

Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie van Element (indeling) ViewDefinitions Element (indeling) weergave Element (indeling) CustomControl Element voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor CustomItem weergeven (indeling) Element voor CustomEntry voor weergave (indeling) ExpressionBinding-Element voor CustomItem (indeling) CustomControlName Element voor de Binding van de expressie voor CustomItem (indeling)

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
|[ExpressionBinding-Element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definieert de gegevens die door het besturingselement wordt weergegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturingselement.

## <a name="remarks"></a>Opmerkingen

Kunt u algemene besturingselementen die kunnen worden gebruikt door alle weergaven van een opmaak bestand maken en u kunt besturingselementen weergeven die kunnen worden gebruikt door een specifieke weergave te maken. De namen van deze besturingselementen zijn opgegeven door de volgende elementen.

- [Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-Element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
