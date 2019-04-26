---
title: EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066223"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `EntrySelectedBy` element. U moet ten minste één type, selectie instellen of selectievoorwaarde voor een definitie opgeven. Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|
|[SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van het besturingselement.|
|[TypeName-Element voor EntrySelectedBy voor GroupBy (indeling)](./typename-element-for-entryselectedby-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md)|Bevat een definitie van het besturingselement.|

## <a name="remarks"></a>Opmerkingen

Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde moet bestaan voor de definitie moet worden gebruikt, bijvoorbeeld wanneer een object een bepaalde eigenschap heeft of wanneer de waarde van een bepaalde eigenschap of script wordt geëvalueerd als `true`. Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zie ook

[SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[TypeName-Element voor EntrySelectedBy voor GroupBy (indeling)](./typename-element-for-entryselectedby-for-groupby-format.md)

[CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
