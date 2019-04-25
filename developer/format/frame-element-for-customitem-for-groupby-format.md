---
title: Frame-Element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065594"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Het element Frame voor CustomItem voor GroupBy (opmaak)

Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) Frame-Element voor CustomItem voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Frame` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|`CustomItem Element`|Vereist Element|
|[FirstLineHanging-Element voor Frame voor GroupBy (indeling)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant.|
|[FirstLineIndent-Element voor Frame voor GroupBy (indeling)](./firstlineindent-element-for-frame-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.|
|[LeftIndent-Element voor Frame voor GroupBy (indeling)](./leftindent-element-for-frame-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.|
|[RightIndent-Element voor Frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent-Element|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)|Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementen in dezelfde `Frame` element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-Element voor Frame voor GroupBy (indeling)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[FirstLineIndent-Element voor Frame voor GroupBy (indeling)](./firstlineindent-element-for-frame-for-groupby-format.md)

[LeftIndent-Element voor Frame voor GroupBy (indeling)](./leftindent-element-for-frame-for-groupby-format.md)

[RightIndent-Element voor Frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md)

[CustomItem-Element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
