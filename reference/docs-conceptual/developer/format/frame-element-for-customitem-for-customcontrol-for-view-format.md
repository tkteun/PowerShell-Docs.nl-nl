---
title: Frame-element voor CustomItem voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4864ea1a865f77c9de6e495d7e8296e81c19b366
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781440"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)

Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor CustomControlView (Format) voor CustomItem voor de weer gave (indeling)

## <a name="syntax"></a>Syntax

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomItem Element`|Vereist element|
|[FirstLineHanging-element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.|
|[FirstLineIndent-element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.|
|[LeftIndent-element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.|
|[RightIndent-element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen in hetzelfde element niet opgeven `Frame` .

## <a name="see-also"></a>Zie ook

[FirstLineHanging-element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent-element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent-element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent-element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomItem-element voor CustomEntry voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
