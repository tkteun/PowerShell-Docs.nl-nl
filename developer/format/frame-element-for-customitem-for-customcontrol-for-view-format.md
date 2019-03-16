---
title: Frame-Element voor CustomItem voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054778"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)

Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor CustomControlView (indeling) Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)

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
|[FirstLineHanging-Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant.|
|[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.|
|[LeftIndent Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.|
|[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element voor CustomEntry voor weergave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementen in dezelfde `Frame` element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomItem-Element voor CustomEntry voor weergave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
