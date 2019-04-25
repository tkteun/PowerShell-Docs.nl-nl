---
title: PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064676"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)

Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling) PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de .NET-eigenschap.

## <a name="remarks"></a>Opmerkingen

De selectievoorwaarde moet opgeven de naam van ten minste één eigenschap of een script om te evalueren, maar u kunt niet beide opgeven. Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over andere onderdelen van een brede weergave [brede weergave](./creating-a-wide-view.md).

## <a name="see-also"></a>Zie ook

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
