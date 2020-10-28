---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)
description: Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 35e1554a9eed491f37499a7455e9c5cae3cd9e1e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655452"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het ExpressionBinding-element van de CustomItem voor de Controls (Format) voor weer gave (Format) voor CustomControlName voor besturings elementen voor weer gave (indeling)

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
|[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturings element op.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. De volgende elementen geven de namen van deze besturings elementen aan:

- [Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
