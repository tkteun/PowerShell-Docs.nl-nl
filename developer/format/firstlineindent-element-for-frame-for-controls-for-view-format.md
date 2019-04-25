---
title: FirstLineIndent-Element voor kader voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066019"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>Het element FirstLineIndent voor Frame voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling) FirstLineIndent Element van het Frame besturingselementen van weergave (indeling)

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
|[Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)|Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens dat u wilt verplaatsen van de eerste regel van de gegevens.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u niet opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-Element voor kader voor besturingselementen voor weergave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
