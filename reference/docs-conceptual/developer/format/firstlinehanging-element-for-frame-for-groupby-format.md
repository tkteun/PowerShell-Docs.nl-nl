---
title: FirstLineHanging-element voor frame voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3def56e918810d9e201d7a9ae73776d90646d8b3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773603"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>Het element FirstLineHanging voor Frame voor GroupBy (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor het object voor GroupBy (indeling)

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
|[Het element Frame voor CustomItem voor GroupBy (opmaak)](./frame-element-for-customitem-for-groupby-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[Het element FirstLineIndent voor Frame voor GroupBy (opmaak)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Het element Frame voor CustomItem voor GroupBy (opmaak)](./frame-element-for-customitem-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
