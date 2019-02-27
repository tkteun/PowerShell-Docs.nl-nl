---
title: FirstLineIndent-Element voor Frame voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848599"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>Het element FirstLineIndent voor Frame voor GroupBy (opmaak)

Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) Frame-Element voor CustomItem voor GroupBy (indeling) FirstLineIndent Element voor Frame voor GroupBy (indeling)

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
|[Frame-Element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)|Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens dat u wilt verplaatsen van de eerste regel van de gegevens.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u niet opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-Element voor Frame voor GroupBy (indeling)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Frame-Element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
