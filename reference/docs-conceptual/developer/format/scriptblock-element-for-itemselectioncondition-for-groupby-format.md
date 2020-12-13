---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665085"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a>Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor GroupBy (Format) CustomEntry voor het element GroupBy (Format) CustomItem voor CustomEntry voor de ExpressionBinding-element van GroupBy (Format) voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor het element GroupBy (Format) script Block voor ItemSelectionCondition voor GroupBy (Format)

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
|[Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.

## <a name="see-also"></a>Zie ook

[Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
