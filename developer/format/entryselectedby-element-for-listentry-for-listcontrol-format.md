---
title: EntrySelectedBy-Element voor ListEntry voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066189"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)

Definieert de .NET-typen die gebruikmaken van de definitie van deze lijst weergeven of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt. In de meeste gevallen is slechts één definitie nodig voor een lijst weergeven. U kunt echter meerdere definities voor de lijstweergave opgeven als u wilt de dezelfde lijstweergave gebruiken om verschillende gegevens voor verschillende objecten weer te geven.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntry voor ListControl (indeling) EntrySelectedBy Element voor ListEntry voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie voor het weergeven van lijst moet worden gebruikt.|
|[SelectionSetName-Element voor EntrySelectedBy voor ListControl (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set van .NET-typen die gebruikmaken van de definitie van deze lijst weergeven.|
|[TypeName-Element voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat gebruikmaakt van de definitie van deze lijst weergeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListEntry-Element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)|Hiermee definieert u hoe de rijen van de lijst worden weergegeven.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van een lijst weergeven. Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.

Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde die moet aanwezig zijn voor de definitie moet worden gebruikt, zoals wanneer een object een bepaalde eigenschap heeft of die een bepaalde eigenschapwaarde of een script wordt geëvalueerd als `true`. Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u definieert de objecten voor een lijst weergeven met behulp van de .NET-typenaam.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Zie ook

[ListEntry-Element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)

[SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[SelectionSetName-Element voor EntrySelectedBy voor ListControl (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-Element voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
