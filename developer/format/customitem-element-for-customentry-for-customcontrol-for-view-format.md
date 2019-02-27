---
title: CustomItem-Element voor CustomEntry voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846940"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)

Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling)

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
|[ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Definieert de gegevens die door het besturingselement wordt weergegeven.|
|[Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.|
|[Nieuwe regel-Element voor CustomItem voor aangepaste besturingselementen voor weergave (indeling)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Voegt een lege regel toe aan de weergave van het besturingselement.|
|[Tekstelement voor CustomItem voor CustomControl voor weergave (indeling)](./text-element-for-customitem-for-customview-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u aanvullende tekst in de gegevens die worden weergegeven door het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomEntries voor CustomControl voor weergave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Bevat een definitie van de weergave van het aangepaste besturingselement.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomEntry-Element voor CustomEntries voor weergave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Nieuwe regel-Element voor CustomItem voor CustomControl voor weergave (indeling)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Tekstelement voor CustomItem voor CustomControl voor weergave (indeling)](./text-element-for-customitem-for-customview-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
