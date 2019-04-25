---
title: AutoSize-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066920"
---
# <a name="autosize-element-for-widecontrol-format"></a>Het element AutoSize voor WideControl (opmaak)

Hiermee geeft u op of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) Autosize-Element voor WideControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `AutoSize` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideControl-Element (indeling)](./widecontrol-element-format.md)|Definieert een breed (één waarde) lijstweergave voor de weergave.|

## <a name="remarks"></a>Opmerkingen

Bij het definiëren van een brede weergave, kunt u toevoegen de `AutoSize` element of de [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, maar niet beide toevoegen.

Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

Zie voor een voorbeeld van een brede weergave [brede weergave (basis)](./wide-view-basic.md).

## <a name="see-also"></a>Zie ook

[ColumnNumber-Element voor WideControl (indeling)](./columnnumber-element-for-widecontrol-format.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[WideControl-Element (indeling)](./widecontrol-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
