---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651782"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)

Hiermee geeft u een set .NET-typen op die gebruikmaken van dit item van de tabel weergave. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling) SelectionSetName element voor EntrySelectedBy voor TableRowEntry (indeling)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van dit item of de voor waarde die voor deze vermelding moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten. Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

Als u een selectie reeks voor een vermelding opgeeft, kunt u geen type naam opgeven. Zie voor meer informatie over het opgeven van een .NET-type [TypeName-element voor EntrySelectedBy voor TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="see-also"></a>Zie ook

[EntrySelectedBy-element (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)

[Een tabelweergave maken](./creating-a-table-view.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
