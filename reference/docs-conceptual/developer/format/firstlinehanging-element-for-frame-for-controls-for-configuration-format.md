---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)
description: Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 94d59ef7b54e036f76e38a3b06b769700443b9fb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655225"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a>Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor Configuration (Format) CustomEntry element voor het CustomItem-element voor het configureren van de configuratie (indeling) voor CustomEntry voor besturings elementen voor het element configuratie frame voor CustomItem voor besturings elementen voor de configuratie (Format) FirstLineHanging-element voor de configuratie (indeling)

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
|[Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het element niet opgeven `FirstLineIndent` .

## <a name="see-also"></a>Zie ook

[Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
