---
title: FirstLineIndent-Element voor Frame voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065866"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Het element FirstLineIndent voor Frame voor CustomControl voor Weergave (opmaak)

Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor Frame-Element voor CustomItem voor CustomControl voor weergave (indeling) FirstLineIndent Element CustomControlView (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `FirstLineIndent` element.

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

Als dit element is opgegeven, kunt u niet opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-Element voor Frame voor CustomControl voor weergave (indeling)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
