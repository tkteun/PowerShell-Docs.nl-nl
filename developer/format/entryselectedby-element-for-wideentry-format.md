---
title: EntrySelectedBy-Element voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846093"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Het element EntrySelectedBy voor WideEntry (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie van de brede weergave of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie brede weergave moet worden gebruikt.|
|[SelectionSetName-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie brede weergave.|
|[TypeName-Element voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie brede weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideEntry-Element (indeling)](./wideentry-element-for-widecontrol-format.md)|Bevat een definitie van de brede weergave.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van een brede weergave opgeven. Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.

Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde die moet aanwezig zijn voor de definitie moet worden gebruikt, zoals wanneer een object een bepaalde eigenschap heeft of die een bepaalde eigenschapwaarde of een Scriptwaarde resulteert in `true`. Zie voor meer informatie over de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

## <a name="see-also"></a>Zie ook

[WideEntry-Element (indeling)](./wideentry-element-for-widecontrol-format.md)

[SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-Element voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Voorwaarden voor het weergeven van gegevens definiëren](./defining-conditions-for-displaying-data.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
