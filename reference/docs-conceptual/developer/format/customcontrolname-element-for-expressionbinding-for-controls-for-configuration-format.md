---
title: CustomControlName-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 690b6ae01b8116b72fbd00aef574feda1fd737b0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786030"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u de naam van een gemeen schappelijk besturings element op. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor Configuration (Format) CustomEntry element voor het CustomItem-element van de configuratie (indeling) voor CustomEntry voor besturings elementen voor de configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) CustomControlName-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)

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
|[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturings element op.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. De volgende elementen geven de namen van deze besturings elementen aan:

- [Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
