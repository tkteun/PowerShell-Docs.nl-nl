---
title: CustomItem-element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355137"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Het element CustomItem voor CustomEntry voor GroupBy (opmaak)

Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomItem voor CustomEntry voor GroupBy (indeling)

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomItem` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|
|[Frame-element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|
|[Element nieuwe regel voor CustomItem voor GroupBy (indeling)](./newline-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.|
|[Tekst element voor CustomItem voor GroupBy (indeling)](./text-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md)|Biedt een definitie van de aangepaste beheer weergave.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomEntry-element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md)

[ExpressionBinding-element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Frame-element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md)

[Element nieuwe regel voor CustomItem voor GroupBy (indeling)](./newline-element-for-customitem-for-groupby-format.md)

[Tekst element voor CustomItem voor GroupBy (indeling)](./text-element-for-customitem-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
