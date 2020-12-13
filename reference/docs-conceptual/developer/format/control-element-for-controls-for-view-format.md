---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)
description: Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: c48b8b7ecaebfde5e6ed2123b837d92561551766
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668079"
---
# <a name="control-element-for-controls-for-view--format"></a>Het element Besturingselement voor Besturingselementen voor Weergave (opmaak)

Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave elementen (indeling) Controls element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Control` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Naam element voor besturings element voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam van het besturings element op.|
|[Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Vereist element.<br /><br /> Hiermee wordt het besturings element gedefinieerd dat door deze weer gave wordt gebruikt.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Controls-element (indeling)](./controls-element-for-view-format.md)|Hiermee worden de weergave besturings elementen gedefinieerd die kunnen worden gebruikt door een specifieke weer gave.|

## <a name="remarks"></a>Opmerkingen

Dit besturings element kan worden opgegeven met de volgende elementen:

- [Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Het element CustomControlName voor GroupBy (opmaak)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Zie ook

[Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls-element (indeling)](./controls-element-for-view-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
