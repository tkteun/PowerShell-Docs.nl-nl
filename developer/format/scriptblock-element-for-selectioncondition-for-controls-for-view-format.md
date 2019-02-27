---
title: ScriptBlock-Element voor SelectionCondition voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850895"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a>Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor besturingselementen voor weergave ( -Indeling) ScriptBlock Element voor SelectionCondition voor besturingselementen voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef het script dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

De selectievoorwaarde moet een minimaal één script of de eigenschap naam opgeven om te evalueren, maar u kunt niet beide opgeven. Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zie ook

[SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
