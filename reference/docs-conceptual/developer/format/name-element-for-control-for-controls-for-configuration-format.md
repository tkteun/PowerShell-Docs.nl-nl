---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)
description: Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 0c1c83f827482886ca742f2c0174e8383f87fb52
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666498"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u de naam van het besturings element op. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor de configuratie (indeling) naam element voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./control-element-for-controls-for-configuration-format.md)|Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op die wordt gebruikt om naar dit besturings element te verwijzen.

## <a name="remarks"></a>Opmerkingen

De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.

- Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

- Wanneer u een ander algemeen besturings element maakt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Wanneer u een besturings element maakt dat kan worden gebruikt door een weer gave, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./control-element-for-controls-for-configuration-format.md)

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
