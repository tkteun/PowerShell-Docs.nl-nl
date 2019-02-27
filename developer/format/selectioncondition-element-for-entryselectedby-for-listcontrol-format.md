---
title: SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: ec75945c5517c02fa001f0a38573c045ffcdbfd3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847850"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)

Hiermee definieert u de voorwaarde die moet bestaan voor het gebruik van deze definitie van de lijstweergave. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor de Lijstdefinitie van een.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[PropertyName-Element voor SelectionCondition voor EmtrySelectedBy voor ListEntry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.|
|[ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.|
|[SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd.|
|[TypeName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor TableRowEntry (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van de vermelding in deze tabel of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.|

## <a name="remarks"></a>Opmerkingen

lWhen definieert u een selectievoorwaarde, gelden voor de volgende vereisten:

- De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.

- De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.

Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over andere onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).

## <a name="see-also"></a>Zie ook

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[ListEntry-Element (indeling)](./listentry-element-for-listcontrol-format.md)

[SelectionSetName-Element voor EnrtySelectedBy voor ListEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-Element voor EntrySelectedBy voor ListEntry (indeling)](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
