---
title: CustomControlName-element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359040"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)

Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (Format) CustomItem voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor het element GroupBy (Format) CustomControlName voor ExpressionBinding voor GroupBy (Format)

## <a name="syntax"></a>Syntaxis

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="text-value"></a>Tekst waarde

Geef de naam van het besturings element op.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. De volgende elementen geven de namen van deze besturings elementen aan:

- [Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Element naam voor besturings elementen voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Element naam voor besturings elementen voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
