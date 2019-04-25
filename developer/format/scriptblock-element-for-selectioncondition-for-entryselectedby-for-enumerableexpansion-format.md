---
title: ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064370"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)

Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.

Configuratie van Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling) SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling) ScriptBlock Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)

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
|[SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|De voorwaarde die moet aanwezig zijn om uit te breiden, de verzameling objecten van deze definitie wordt gedefinieerd.|

## <a name="text-value"></a>Tekstwaarde

Geef het script dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

De selectievoorwaarde moet Geef ten minste één script of eigenschap op om te evalueren, maar u kunt niet beide opgeven. Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zie ook

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
