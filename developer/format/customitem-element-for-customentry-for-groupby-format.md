---
title: CustomItem-Element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847458"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Het element CustomItem voor CustomEntry voor GroupBy (opmaak)

Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Definieert de gegevens die door het besturingselement wordt weergegeven.|
|[Frame-Element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.|
|[Nieuwe regel-Element voor CustomItem voor GroupBy (indeling)](./newline-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Voegt een lege regel toe aan de weergave van het besturingselement.|
|[Tekstelement voor CustomItem voor GroupBy (indeling)](./text-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u aanvullende tekst in de gegevens die worden weergegeven door het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md)|Bevat een definitie van de weergave van het aangepaste besturingselement.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomEntry-Element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md)

[ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Frame-Element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)

[Nieuwe regel-Element voor CustomItem voor GroupBy (indeling)](./newline-element-for-customitem-for-groupby-format.md)

[Tekstelement voor CustomItem voor GroupBy (indeling)](./text-element-for-customitem-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
