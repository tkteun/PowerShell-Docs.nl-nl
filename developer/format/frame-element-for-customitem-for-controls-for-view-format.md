---
title: Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065713"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)

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
|[FirstLineHanging-Element van het kader van besturingselementen van weergave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel wordt verplaatst naar de linkerkant.|
|[FirstLineIndent Element van het kader van besturingselementen van weergave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel wordt verplaatst naar de rechterkant.|
|[LeftIndent Element van het kader van besturingselementen van weergave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.|
|[RightIndent Element van het kader van besturingselementen van weergave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementen in dezelfde `Frame` element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-Element van het kader van besturingselementen van weergave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent Element van het kader van besturingselementen van weergave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent Element van het kader van besturingselementen van weergave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent Element van het kader van besturingselementen van weergave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
