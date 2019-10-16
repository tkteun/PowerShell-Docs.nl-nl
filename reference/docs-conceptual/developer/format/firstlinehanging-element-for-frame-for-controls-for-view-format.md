---
title: FirstLineHanging-element voor frame voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355074"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>Het element FirstLineHanging voor Frame voor Besturingselementen voor Weergave (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format)-frame-element voor CustomItem voor besturings elementen voor de weer gave (Format) FirstLineHanging-element van Frame van de besturings elementen van de weer gave (indeling)

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
|[Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekst waarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[FirstLineIndent-element voor frame voor besturings elementen voor weer gave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
