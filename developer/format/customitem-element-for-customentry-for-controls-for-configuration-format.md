---
title: CustomItem-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851665"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)

Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie

## <a name="syntax"></a>Syntaxis

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element. Zie Opmerkingen voor meer informatie.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Definieert de gegevens die door het besturingselement wordt weergegeven.|
|[Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.|
|[Nieuwe regel-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Voegt een lege regel toe aan de weergave van het besturingselement.|
|[Tekstelement voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Tekst, zoals tussen haakjes of vierkante haken, toegevoegd aan de weergave van het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Bevat een definitie van het besturingselement.|

## <a name="remarks"></a>Opmerkingen

Bij het opgeven van de onderliggende elementen van de `CustomItem` -element, houd rekening met het volgende:

- De onderliggende elementen moeten worden toegevoegd in de volgende volgorde: `ExpressionBinding`, `NewLine`, `Text`, en `Frame`.

- Er is geen maximale limiet voor het aantal reeksen die u kunt opgeven.

- In elke volgorde hebben, er is geen maximale limiet voor het aantal `ExpressionBinding` elementen die u kunt gebruiken.

## <a name="see-also"></a>Zie ook

[ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Nieuwe regel-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Tekstelement voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)