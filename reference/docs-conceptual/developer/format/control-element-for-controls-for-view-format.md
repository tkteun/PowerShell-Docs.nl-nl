---
title: Besturings element voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354850"
---
# <a name="control-element-for-controls-for-view--format"></a>Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)

Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave elementen (indeling) Controls element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Control` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Naam element voor besturings element voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam van het besturings element op.|
|[CustomControl-element voor besturings elementen voor de weer gave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Vereist element.<br /><br /> Hiermee wordt het besturings element gedefinieerd dat door deze weer gave wordt gebruikt.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Controls-element (indeling)](./controls-element-for-view-format.md)|Hiermee worden de weergave besturings elementen gedefinieerd die kunnen worden gebruikt door een specifieke weer gave.|

## <a name="remarks"></a>Opmerkingen

Dit besturings element kan worden opgegeven met de volgende elementen:

- [CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName-element voor GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Zie ook

[CustomControl-element voor besturings elementen voor de weer gave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName-element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls-element (indeling)](./controls-element-for-view-format.md)

[Element naam voor besturings elementen voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
