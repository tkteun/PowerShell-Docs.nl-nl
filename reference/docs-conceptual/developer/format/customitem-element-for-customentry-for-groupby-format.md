---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomItem voor CustomEntry voor GroupBy (opmaak)
description: Het element CustomItem voor CustomEntry voor GroupBy (opmaak)
ms.openlocfilehash: 5db23ad4dad5bd66ea64b9c6e91b8224a4aa4eca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645991"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Het element CustomItem voor CustomEntry voor GroupBy (opmaak)

Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (opmaak) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor GroupBy (Format) CustomItem-element voor de CustomEntry voor GroupBy (indeling)

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
|[Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|
|[Het element Frame voor CustomItem voor GroupBy (opmaak)](./frame-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|
|[Het element NewLine voor CustomItem voor GroupBy (opmaak)](./newline-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.|
|[Het element Tekst voor CustomItem voor GroupBy (opmaak)](./text-element-for-customitem-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomControl voor GroupBy (opmaak)](./customentry-element-for-customcontrol-for-groupby-format.md)|Biedt een definitie van de aangepaste beheer weergave.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Het element CustomEntry voor CustomControl voor GroupBy (opmaak)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Het element Frame voor CustomItem voor GroupBy (opmaak)](./frame-element-for-customitem-for-groupby-format.md)

[Het element NewLine voor CustomItem voor GroupBy (opmaak)](./newline-element-for-customitem-for-groupby-format.md)

[Het element Tekst voor CustomItem voor GroupBy (opmaak)](./text-element-for-customitem-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
