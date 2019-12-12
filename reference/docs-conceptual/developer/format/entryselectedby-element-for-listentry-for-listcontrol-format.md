---
title: EntrySelectedBy-element voor List entry voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355102"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Het element EntrySelectedBy voor ListEntry voor ListControl (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt. In de meeste gevallen is slechts één definitie nodig voor een lijst weergave. U kunt echter meerdere definities voor de lijst weergave opgeven als u dezelfde lijst weergave wilt gebruiken om verschillende gegevens voor verschillende objecten weer te geven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item-element (indeling) van het element van de ListControl (Format) List entry voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst weergave definitie.|
|[SelectionSetName-element voor EntrySelectedBy voor ListControl (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze lijst weergave definitie.|
|[TypeName-element voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze lijst weergave definitie.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[List Entry-element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)|Hiermee wordt gedefinieerd hoe de rijen van de lijst worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een lijst weergave definitie. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een script `true`. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

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

[List Entry-element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)

[SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[SelectionSetName-element voor EntrySelectedBy voor ListControl (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-element voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Een lijst weergave maken](./creating-a-list-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
