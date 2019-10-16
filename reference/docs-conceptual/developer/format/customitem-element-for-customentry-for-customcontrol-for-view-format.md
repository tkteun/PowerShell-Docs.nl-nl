---
title: CustomItem-element voor CustomEntry voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355186"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)

Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (indeling)

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
|[ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|
|[Frame-element voor CustomItem voor CustomControl voor weer gave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|
|[Element nieuwe regel voor CustomItem voor aangepast besturings element voor weer gave (indeling)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.|
|[Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)](./text-element-for-customitem-for-customview-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Biedt een definitie van de aangepaste beheer weergave.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Frame-element voor CustomItem voor CustomControl voor weer gave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Element nieuwe regel voor CustomItem voor CustomControl voor weer gave (indeling)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)](./text-element-for-customitem-for-customview-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
