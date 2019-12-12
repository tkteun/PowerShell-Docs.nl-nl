---
title: CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355179"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomItem` beschreven. Zie Opmerkingen voor meer informatie.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|
|[Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|
|[Element nieuwe regel voor CustomItem voor besturings elementen voor weer gave (indeling)](./newline-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.|
|[Tekst element voor CustomItem voor besturings elementen voor weer gave (indeling)](./text-element-for-customitem-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Biedt een definitie van het besturings element.|

## <a name="remarks"></a>Opmerkingen

Houd bij het opgeven van de onderliggende elementen van het element `CustomItem` het volgende in acht:

- De onderliggende elementen moeten worden toegevoegd in de volgende volg orde: `ExpressionBinding`, `NewLine`, `Text`en `Frame`.

- Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.

- In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding` elementen dat u kunt gebruiken.

## <a name="see-also"></a>Zie ook

[ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Element nieuwe regel voor CustomItem voor besturings elementen voor weer gave (indeling)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Tekst element voor CustomItem voor besturings elementen voor weer gave (indeling)](./text-element-for-customitem-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
