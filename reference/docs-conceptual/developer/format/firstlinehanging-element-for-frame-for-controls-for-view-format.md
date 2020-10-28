---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FirstLineHanging voor Frame voor Besturingselementen voor Weergave (opmaak)
description: Het element FirstLineHanging voor Frame voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: a7a2aa533a74bd3c347307ab49a467d1f9844fc3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655214"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>Het element FirstLineHanging voor Frame voor Besturingselementen voor Weergave (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control Format) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het frame-element van de weer gave (Format) voor CustomItem voor besturings elementen voor de weer gave (indeling) FirstLineHanging element van het frame van de besturings elementen van de weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FirstLineHanging` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./frame-element-for-customitem-for-controls-for-view-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[Het element FirstLineIndent voor Frame voor Besturingselementen voor Weergave (opmaak)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
