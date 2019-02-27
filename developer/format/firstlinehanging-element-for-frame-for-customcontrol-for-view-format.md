---
title: FirstLineHanging-Element voor Frame voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ae4ad8ae3e6cb5d1174dc001b30aa84dd182a606
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849775"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>Het element FirstLineHanging voor Frame voor CustomControl voor Weergave (opmaak)

Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor CutomControlView (indeling) Frame-Element voor CustomItem voor CustomControl voor weergave (indeling) FirstLineHanging Element voor Frame voor CustomControl voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `FirstLineHanging` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens dat u wilt verplaatsen van de eerste regel van de gegevens.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u niet opgeven de [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element.

## <a name="see-also"></a>Zie ook

[FirstLineIndent-Element voor Frame voor CustomControl voor weergave (indeling)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
