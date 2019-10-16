---
title: Frame-element voor CustomItem voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354983"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het element configuratie frame voor CustomItem voor besturings elementen voor configuratie (indeling)

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
|[FirstLineHanging-element voor frame voor besturings elementen voor configuratie (indeling)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.|
|[FirstLineIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.|
|[LeftIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.|
|[RightIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen niet opgeven in hetzelfde element `Frame`.

## <a name="see-also"></a>Zie ook

[FirstLineHanging-element voor frame voor besturings elementen voor configuratie (indeling)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
