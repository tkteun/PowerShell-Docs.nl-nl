---
title: SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8745ef9e6f326c3e8a5dbf185a595bbe93e92414
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785316"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)

Hiermee geeft u de set .NET-typen op die door deze definitie worden uitgebreid.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor EnumerableExpansion (opmaak)](./entryselectedby-element-for-enumerableexpansion-format.md)|Hiermee definieert u de .NET-verzamelings objecten die door deze definitie worden uitgevouwen.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Elke definitie moet een of meer type namen, een selectieset of een selectie voorwaarde opgeven.

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten. Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

## <a name="see-also"></a>Zie ook

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Het element EntrySelectedBy voor EnumerableExpansion (opmaak)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
