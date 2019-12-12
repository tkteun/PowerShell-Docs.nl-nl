---
title: Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354976"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format)-frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Frame` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomItem Element`|Vereist element|
|[FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel naar links wordt verplaatst.|
|[FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel naar rechts wordt geschoven.|
|[LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.|
|[RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen niet opgeven in hetzelfde `Frame` element.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
