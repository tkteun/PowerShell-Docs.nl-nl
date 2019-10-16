---
title: Naam element voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354318"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u de naam van het besturings element op. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor de configuratie (indeling) naam element voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Name` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Control-element voor besturings elementen voor configuratie (indeling)](./control-element-for-controls-for-configuration-format.md)|Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.|

## <a name="text-value"></a>Tekst waarde

Geef de naam op die wordt gebruikt om naar dit besturings element te verwijzen.

## <a name="remarks"></a>Opmerkingen

De naam die u hier opgeeft, kan worden gebruikt in de volgende elementen om te verwijzen naar dit besturings element.

- Bij het maken van een tabel, lijst, brede of aangepaste beheer weergave kan het besturings element worden opgegeven door het volgende element: element [GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

- Wanneer u een ander algemeen besturings element maakt, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Wanneer u een besturings element maakt dat kan worden gebruikt door een weer gave, kan dit besturings element worden opgegeven met het volgende element: [ExpressionBinding element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Control-element voor besturings elementen voor configuratie (indeling)](./control-element-for-controls-for-configuration-format.md)

[ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
