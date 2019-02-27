---
title: Naam van Element voor controle voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849670"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u de naam van het besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) naamelement voor controle van besturingselementen voor de configuratie (-indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Name` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Controle-Element voor besturingselementen voor de configuratie (-indeling)](./control-element-for-controls-for-configuration-format.md)|Hiermee definieert u een algemene besturingselement dat kan worden gebruikt door alle weergaven van de opmaak bestands- en de naam die wordt gebruikt om te verwijzen naar het besturingselement.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam die wordt gebruikt om te verwijzen naar dit besturingselement.

## <a name="remarks"></a>Opmerkingen

Naam van de hier opgegeven kan in de volgende elementen worden gebruikt om te verwijzen naar dit besturingselement.

- Bij het maken van een tabel, lijst, breed of aangepast besturingselement weergeven, kan het besturingselement door het volgende element worden opgegeven: [GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)

- Bij het maken van een andere algemene besturingselement, kan dit besturingselement kan worden opgegeven met het volgende element: [ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Bij het maken van een besturingselement dat kan worden gebruikt door een weergave, kan dit besturingselement kan worden opgegeven met het volgende element: [ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Controle-Element voor besturingselementen voor de configuratie (-indeling)](./control-element-for-controls-for-configuration-format.md)

[ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
