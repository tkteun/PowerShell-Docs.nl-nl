---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655102"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)

Hiermee definieert u de voor waarde die moet bestaan om deze definitie van de lijst weergave te gebruiken. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een lijst definitie.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition element voor de List entry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[TypeName-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor TableRowEntry (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze tabel vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.|

## <a name="remarks"></a>Opmerkingen

lWhen u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Element List entry (indeling)](./listentry-element-for-listcontrol-format.md)

[SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-element voor EntrySelectedBy voor List entry (indeling)](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
