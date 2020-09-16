---
title: Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0131fa86be4be4daec1d9d24b50397fb8529f050
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785571"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (Format) ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling) eigenschaps element voor ItemSelectionCondition voor CustomControl voor weer gave (Format

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
|[ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.

## <a name="see-also"></a>Zie ook

[Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
