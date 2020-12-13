---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)
description: Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645662"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)

Hiermee geeft u een .NET-type op dat gebruikmaakt van dit item van de lijst weergave. Er is geen limiet voor het aantal typen dat kan worden opgegeven voor een vermelding in de lijst.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) bestand van ListControl element (indeling) (Format) List item (Format) element Entry element (indeling) EntrySelectedBy element voor List entry (Format) TypeName element voor EntrySelectedBy voor ListControl

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het gebruik van dit element in een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een vermelding van een lijst weergave.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
