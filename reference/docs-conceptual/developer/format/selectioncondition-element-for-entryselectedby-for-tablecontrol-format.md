---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)
ms.openlocfilehash: 22f304615c6433ffb67f3b4046b645d0c37be8a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645769"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)

Hiermee definieert u de voor waarde die moet bestaan om te gebruiken voor deze definitie van de tabel weergave. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een tabel definitie.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element SelectionCondition beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor TableRowEntry (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze tabel vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.|

## <a name="remarks"></a>Opmerkingen

Voor elke lijst vermelding moet ten minste ????n type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste ????n eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden defini??ren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[Voor waarden defini??ren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy-element (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
