---
title: CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066376"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)

Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element. Zie Opmerkingen voor meer informatie.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Definieert de gegevens die door het besturingselement wordt weergegeven.|
|[Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.|
|[Nieuwe regel-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./newline-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Voegt een lege regel toe aan de weergave van het besturingselement.|
|[Tekstelement voor CustomItem voor besturingselementen voor weergave (indeling)](./text-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Tekst, zoals tussen haakjes of vierkante haken, toegevoegd aan de weergave van het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Bevat een definitie van het besturingselement.|

## <a name="remarks"></a>Opmerkingen

Bij het opgeven van de onderliggende elementen van de `CustomItem` -element, houd rekening met het volgende:

- De onderliggende elementen moeten worden toegevoegd in de volgende volgorde: `ExpressionBinding`, `NewLine`, `Text`, en `Frame`.

- Er is geen maximale limiet voor het aantal reeksen die u kunt opgeven.

- In elke volgorde hebben, er is geen maximale limiet voor het aantal `ExpressionBinding` elementen die u kunt gebruiken.

## <a name="see-also"></a>Zie ook

[ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Nieuwe regel-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Tekstelement voor CustomItem voor besturingselementen voor weergave (indeling)](./text-element-for-customitem-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
