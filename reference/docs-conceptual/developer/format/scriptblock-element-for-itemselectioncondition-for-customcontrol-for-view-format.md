---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: d762f400f5bb52af314093079fe94223c56d3f31
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665129"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (Format) ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (Format) script block element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)

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
|[ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
