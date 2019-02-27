---
title: ColumnNumber-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846968"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Het element ColumnNumber voor WideControl (opmaak)

Hiermee geeft u het aantal kolommen in de brede weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) ColumnNumber Element voor WideControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ColumnNumber` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideControl-Element (indeling)](./widecontrol-element-format.md)|Definieert een breed (één waarde) lijstweergave voor de weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef een positief geheel getal.

## <a name="remarks"></a>Opmerkingen

Bij het definiëren van een brede weergave, kunt u toevoegen de `AutoSize` element of de `ColumnNumber` element, maar niet beide toevoegen.

Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

Zie voor een voorbeeld van een brede weergave [brede weergave (basis)](./wide-view-basic.md).

## <a name="see-also"></a>Zie ook

[AutoSize-Element voor WideControl (indeling)](./autosize-element-for-widecontrol-format.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Brede weergave (basis)](./wide-view-basic.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
