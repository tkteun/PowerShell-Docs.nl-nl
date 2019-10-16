---
title: FirstLineHanging-element voor frame voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355095"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>Het element FirstLineHanging voor Frame voor GroupBy (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het CustomItem-element van GroupBy (Format) voor CustomEntry voor het object GroupBy (Format) voor CustomItem voor het object GroupBy (Format) voor het frame voor het object GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `FirstLineHanging` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Frame-element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekst waarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[FirstLineIndent-element voor frame voor GroupBy (indeling)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Frame-element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
