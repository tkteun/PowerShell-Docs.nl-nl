---
title: ScriptBlock-Element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064404"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)

Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en dat het item wordt gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntries voor ListControl (indeling) ListItems Element voor ListEntry voor ListControl (indeling) ListItem Element voor ListItems voor lijst beheer (indeling) ItemSelectionCondition Element voor ListItem voor ListControl (indeling) ScriptBlock Element voor ItemSelectionCondition voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `ScriptBlock` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Hiermee definieert u de voorwaarde die moet bestaan voor dit item in de lijst moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef het script dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u niet opgeven de `PropertyName` element bij het definiëren van de selectievoorwaarde.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
