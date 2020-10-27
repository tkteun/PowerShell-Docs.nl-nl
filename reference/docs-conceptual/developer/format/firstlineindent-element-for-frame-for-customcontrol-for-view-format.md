---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FirstLineIndent voor Frame voor CustomControl voor Weergave (opmaak)
description: Het element FirstLineIndent voor Frame voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 8dce8b4b072b754c3b7d631b3e5c321a5a3e5a3e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645886"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>Het element FirstLineIndent voor Frame voor CustomControl voor Weergave (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor CustomControlView (Format)-element voor CustomItem voor

## <a name="syntax"></a>Syntax

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FirstLineIndent` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|

## <a name="text-value"></a>Tekstwaarde

Geef het aantal tekens op waarmee u de eerste regel van de gegevens wilt verschuiven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[Het element FirstLineHanging voor Frame voor CustomControl voor Weergave (opmaak)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
