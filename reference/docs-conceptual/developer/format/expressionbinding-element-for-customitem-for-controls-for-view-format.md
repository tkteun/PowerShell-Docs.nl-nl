---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)
description: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649886"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)

Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor het weer geven van het element CustomEntry (Format) voor CustomEntries voor besturings elementen voor de weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)

## <a name="syntax"></a>Syntax

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomControl Element`|Optioneel element.<br /><br /> Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.|
|[Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.|
|[Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de elementen van verzamelingen worden weer gegeven.|
|[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|
|[Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.|
|[Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
