---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)
ms.openlocfilehash: 38c88ad47e57cd20902c6b8aabdb0b8e8b682ba4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648038"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding element voor CustomItem voor weer gave (Format) voor expressie binding

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (notatie](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)

[Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
