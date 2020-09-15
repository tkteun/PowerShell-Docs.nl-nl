---
title: ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1885a2820c0cb250aa6fda80544f58d06136cfeb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773790"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)

Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl-element voor weer gave (Format) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor de weer gave (Format)

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
|[Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.|
|[Het element EnumerateCollection voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Opgegeven dat de elementen van verzamelingen worden weer gegeven.|
|[ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|
|[Het element PropertyName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.|
|[Script block-element voor ExpressionBinding voor CustomCustomControl voor weer gave (indeling)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Het element EnumerateCollection voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Het element PropertyName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Het element ScriptBlock voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
