---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FirstLineIndent voor Frame voor GroupBy (opmaak)
description: Het element FirstLineIndent voor Frame voor GroupBy (opmaak)
ms.openlocfilehash: 391a6f338e264fd9fdd1948ded74bf022cb114d1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645789"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>Het element FirstLineIndent voor Frame voor GroupBy (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor het object voor GroupBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FirstLineIndent` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Frame voor CustomItem voor GroupBy (opmaak)](./frame-element-for-customitem-for-groupby-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[Het element FirstLineHanging voor Frame voor GroupBy (opmaak)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Het element Frame voor CustomItem voor GroupBy (opmaak)](./frame-element-for-customitem-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
