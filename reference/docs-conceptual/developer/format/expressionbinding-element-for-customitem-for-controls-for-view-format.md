---
title: ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355067"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)

Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)

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
|[CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.|
|[EnumerateCollection-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de elementen van verzamelingen worden weer gegeven.|
|[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.|
|[Het element PropertyName voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.|
|[Script block-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[EnumerateCollection-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Het element PropertyName voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Script block-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
