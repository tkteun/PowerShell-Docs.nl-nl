---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)
ms.openlocfilehash: 1e518f898e0e1e62ca64f9897b1323cc6dd89ae9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665055"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het lijst item gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling). element van ListControl element (Format) voor ListControl (indeling) element List entry voor List Entries (Format) List items element voor List entry voor ListControl (Format) lijst item-element voor de list items voor listing Control (Format) ItemSelectionCondition element voor ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `ScriptBlock` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het element niet opgeven `PropertyName` bij het definiëren van de selectie voorwaarde.

## <a name="see-also"></a>Zie ook

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
