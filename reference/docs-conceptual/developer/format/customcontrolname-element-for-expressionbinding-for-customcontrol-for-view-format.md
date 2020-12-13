---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)
description: Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 24b27428c07d7178f0069f6d0e5b7ffc555efe34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666804"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)

Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl-element voor weer gave (Format) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding element voor CustomItem (Format) voor expressie binding voor CustomControlName (indeling)

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
|[ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturings element op.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. De namen van deze besturings elementen worden aangegeven door de volgende elementen.

- [Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
