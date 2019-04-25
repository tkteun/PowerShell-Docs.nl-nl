---
title: Element beheren voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066767"
---
# <a name="control-element-for-controls-for-view--format"></a>Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u een besturingselement dat kan worden gebruikt door de weergave en de naam die wordt gebruikt om te verwijzen naar het besturingselement.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) bepaalt Element (indeling) controle-Element voor besturingselementen voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Control` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Naamelement voor controle voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam van het besturingselement.|
|[CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Vereist element.<br /><br /> Hiermee definieert u het besturingselement wordt gebruikt door deze weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Besturingselementen Element (indeling)](./controls-element-for-view-format.md)|Hiermee definieert u de weergave-besturingselementen die kunnen worden gebruikt door een specifieke weergave.|

## <a name="remarks"></a>Opmerkingen

Dit besturingselement kan worden opgegeven met de volgende elementen:

- [CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName-Element voor GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Zie ook

[CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Besturingselementen Element (indeling)](./controls-element-for-view-format.md)

[Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
