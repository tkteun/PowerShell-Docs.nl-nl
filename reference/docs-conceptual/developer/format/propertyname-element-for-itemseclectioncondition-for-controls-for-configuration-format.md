---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 860683eb54b2a3579767640c1d3f0937897b8f8e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655125"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor het object CustomControl voor configuratie (indeling) CustomEntry (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor de configuratie (Format) eigenschap naam voor ItemSeclectionCondition voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.

## <a name="see-also"></a>Zie ook

[Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
