---
title: EntrySelectedBy-Element voor CustomEntry voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066274"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor EntrySelectedBy weergeven (indeling) Element voor CustomEntry voor weergave (indeling)

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
|[SelectionCondition-Element voor EntrySelectedBy voor CustomEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|
|[SelectionSetName-Element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van de weergave beheer.|
|[TypeName-Element voor EntrySelectedBy voor CustomEntry (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van de weergave beheer.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomEntries voor weergave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Hiermee definieert u de besturingselementen die worden gebruikt door specifieke .NET-objecten.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectie instellen of selectievoorwaarde voor een vermelding opgeven. Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.

Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde moet bestaan voor de vermelding moet worden gebruikt, bijvoorbeeld wanneer een object een bepaalde eigenschap heeft of wanneer de waarde van een bepaalde eigenschap of script wordt geëvalueerd als `true`. Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [aangepaste weergave van het](./creating-custom-controls.md).

## <a name="see-also"></a>Zie ook

[SelectionCondition-Element voor EntrySelectedBy voor CustomEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[SelectionSetName-Element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[TypeName-Element voor EntrySelectedBy voor CustomEntry (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry-Element voor CustomEntries voor weergave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Aangepast besturingselement weergeven](./creating-custom-controls.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
