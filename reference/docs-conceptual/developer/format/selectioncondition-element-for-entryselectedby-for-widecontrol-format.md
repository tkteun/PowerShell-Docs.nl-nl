---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
ms.openlocfilehash: 8c51ca72edc6ad174dc289c61a8987e8f9495d19
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655109"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)

Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een definitie van een brede vermelding.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven. U moet één `PropertyName` element of opgeven `ScriptBlock` . De `SelectionSetName` `TypeName` elementen en zijn optioneel. U kunt een van beide elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script blok op waarmee de voor waarde wordt geactiveerd.|
|[Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor WideEntry (opmaak)](./entryselectedby-element-for-wideentry-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.|

## <a name="remarks"></a>Opmerkingen

Voor elke uitgebreide vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Het element EntrySelectedBy voor WideEntry (opmaak)](./entryselectedby-element-for-wideentry-format.md)

[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
