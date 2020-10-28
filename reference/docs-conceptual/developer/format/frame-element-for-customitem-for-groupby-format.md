---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor GroupBy (opmaak)
description: Het element Frame voor CustomItem voor GroupBy (opmaak)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652175"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Het element Frame voor CustomItem voor GroupBy (opmaak)

Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)

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
|[Het element FirstLineHanging voor Frame voor GroupBy (opmaak)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.|
|[Het element FirstLineIndent voor Frame voor GroupBy (opmaak)](./firstlineindent-element-for-frame-for-groupby-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.|
|[Het element LeftIndent voor Frame voor GroupBy (opmaak)](./leftindent-element-for-frame-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.|
|[RightIndent-element voor frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomItem voor CustomEntry voor GroupBy (opmaak)](./customitem-element-for-customentry-for-groupby-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen in hetzelfde element niet opgeven `Frame` .

## <a name="see-also"></a>Zie ook

[Het element FirstLineHanging voor Frame voor GroupBy (opmaak)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Het element FirstLineIndent voor Frame voor GroupBy (opmaak)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Het element LeftIndent voor Frame voor GroupBy (opmaak)](./leftindent-element-for-frame-for-groupby-format.md)

[Het element RightIndent voor Frame voor GroupBy (opmaak)](./rightindent-element-for-frame-for-groupby-format.md)

[Het element CustomItem voor CustomEntry voor GroupBy (opmaak)](./customitem-element-for-customentry-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
