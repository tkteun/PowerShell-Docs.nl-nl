---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 853130da4489e571d7f4026a8d65d029d1889f9b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665234"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor het object CustomControl voor configuratie (indeling) CustomEntry configuratie (Format) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) script block element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
