---
title: ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354626"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)

Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave ( Format) CustomItem-element voor CustomEntry voor CustomControl voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ExpressionBinding` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomControl Element`|Optioneel element.<br /><br /> Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.|
|[CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.|
|[EnumerateCollection-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Opgegeven dat de elementen van verzamelingen worden weer gegeven.|
|[ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|
|[Het element PropertyName voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.|
|[Script block-element voor ExpressionBinding voor CustomCustomControl voor weer gave (indeling)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor CustomControl voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Het element PropertyName voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Script block-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem-element voor CustomEntry voor CustomControl voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
