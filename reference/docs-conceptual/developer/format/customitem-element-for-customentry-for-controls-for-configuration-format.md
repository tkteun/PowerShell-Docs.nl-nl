---
title: CustomItem-element voor CustomEntry voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355242"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor configuratie besturings elementen

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomItem` beschreven. Zie Opmerkingen voor meer informatie.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|
|[Frame-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|
|[Element nieuwe regel voor CustomItem voor besturings elementen voor configuratie (indeling)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.|
|[Tekst element voor CustomItem voor besturings elementen voor configuratie (indeling)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Biedt een definitie van het besturings element.|

## <a name="remarks"></a>Opmerkingen

Wanneer u de onderliggende elementen van het element `CustomItem` opgeeft, houdt u het volgende in acht:

- De onderliggende elementen moeten worden toegevoegd in de volgende volg orde: `ExpressionBinding`, `NewLine`, `Text` en `Frame`.

- Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.

- In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding`-elementen dat u kunt gebruiken.

## <a name="see-also"></a>Zie ook

[ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Frame-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Element nieuwe regel voor CustomItem voor besturings elementen voor configuratie (indeling)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Tekst element voor CustomItem voor besturings elementen voor configuratie (indeling)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
