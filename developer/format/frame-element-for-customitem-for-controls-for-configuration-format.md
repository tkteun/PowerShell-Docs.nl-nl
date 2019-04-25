---
title: Element voor CustomItem kader voor controles voor configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065560"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor het kader, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)

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
|[FirstLineHanging-Element voor kader voor controles voor configuratie (-indeling)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant.|
|[FirstLineIndent-Element voor kader voor controles voor configuratie (-indeling)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.|
|[LeftIndent-Element voor kader voor controles voor configuratie (-indeling)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.|
|[RightIndent-Element voor kader voor controles voor configuratie (-indeling)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementen in dezelfde `Frame` element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-Element voor kader voor controles voor configuratie (-indeling)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent-Element voor kader voor controles voor configuratie (-indeling)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent-Element voor kader voor controles voor configuratie (-indeling)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent-Element voor kader voor controles voor configuratie (-indeling)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
