---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)
description: Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652200"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor het CustomEntry-element (Format) voor CustomEntries voor besturings elementen voor de weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format)-frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)

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
|[FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel naar links wordt verplaatst.|
|[FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel naar rechts wordt geschoven.|
|[LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.|
|[RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen in hetzelfde element niet opgeven `Frame` .

## <a name="see-also"></a>Zie ook

[FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
