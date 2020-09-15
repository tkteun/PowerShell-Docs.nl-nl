---
title: EntrySelectedBy-element voor List entry voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d6ab1c08dd353da74d1a7d27c569d2fa86e083c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774113"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt. In de meeste gevallen is slechts één definitie nodig voor een lijst weergave. U kunt echter meerdere definities voor de lijst weergave opgeven als u dezelfde lijst weergave wilt gebruiken om verschillende gegevens voor verschillende objecten weer te geven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (indeling) voor List entry voor ListControl (Format) element list item voor ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst weergave definitie.|
|[Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze lijst weergave definitie.|
|[Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze lijst weergave definitie.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ListEntry voor ListControl (opmaak)](./listentry-element-for-listcontrol-format.md)|Hiermee wordt gedefinieerd hoe de rijen van de lijst worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een lijst weergave definitie. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` . Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u de objecten voor een lijst weergave definieert met behulp van de .NET-type naam.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Zie ook

[Het element ListEntry voor ListControl (opmaak)](./listentry-element-for-listcontrol-format.md)

[Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Een lijstweergave maken](./creating-a-list-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
