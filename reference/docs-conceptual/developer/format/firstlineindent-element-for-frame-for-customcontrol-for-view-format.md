---
title: FirstLineIndent-element voor frame voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354563"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Het element FirstLineIndent voor Frame voor CustomControl voor Weergave (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor CustomControlView (Format) frame-element voor CustomItem voor CustomControl voor weer gave (indeling) FirstLineIndent-element

## <a name="syntax"></a>Syntaxis

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `FirstLineIndent` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Frame-element voor CustomItem voor CustomControl voor weer gave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekst waarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-element voor frame voor CustomControl voor weer gave (indeling)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Frame-element voor CustomItem voor CustomControl voor weer gave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
