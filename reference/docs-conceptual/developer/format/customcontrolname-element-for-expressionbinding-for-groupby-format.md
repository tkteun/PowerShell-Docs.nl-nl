---
title: CustomControlName-element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785996"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)

Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturings element op.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. De volgende elementen geven de namen van deze besturings elementen aan:

- [Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

[Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
