---
title: FirstLineHanging-element voor frame voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa428c1fbe4cd8070e40cf0bc732eb335489ba4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773637"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>Het element FirstLineHanging voor Frame voor CustomControl voor Weergave (opmaak)

Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor CustomControlView (Format) voor CustomItem voor de weer gave (Format) voor het kader

## <a name="syntax"></a>Syntax

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FirstLineHanging` element beschreven.

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

Als dit element is opgegeven, kunt u het [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -element niet opgeven.

## <a name="see-also"></a>Zie ook

[Het element FirstLineIndent voor Frame voor CustomControl voor Weergave (opmaak)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
