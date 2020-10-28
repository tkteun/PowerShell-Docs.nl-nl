---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)
description: Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 9090a3ada5316ba5ddb4a9c46eee37c11982ae6e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666736"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)

Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|
|[Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|
|[Element nieuwe regel voor CustomItem voor aangepast besturings element voor weer gave (indeling)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.|
|[Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)](./text-element-for-customitem-for-customview-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Biedt een definitie van de aangepaste beheer weergave.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Het element NewLine voor CustomItem voor CustomControl voor Weergave (opmaak)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)](./text-element-for-customitem-for-customview-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
