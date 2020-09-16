---
title: Element naam voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 109f3a40606dbe82322decf0c69d2367c75175f6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781083"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u de naam van het besturings element op.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (Format) naam element voor besturings element voor weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<Name>ControlName</Name>
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
|[Besturings element voor besturings elementen voor weer gave (indeling)](./control-element-for-controls-for-view-format.md)|Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op die wordt gebruikt om te verwijzen naar het besturings element.

## <a name="remarks"></a>Opmerkingen

De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.

- Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

- Wanneer u een ander besturings element maakt dat door een weer gave kan worden gebruikt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Besturings element voor besturings elementen voor weer gave (indeling)](./control-element-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
