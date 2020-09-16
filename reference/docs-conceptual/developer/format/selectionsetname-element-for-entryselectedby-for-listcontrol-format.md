---
title: SelectionSetName-element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4315d81da4ceeb7a5b171087434ae15fb09e6592
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785265"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)

Hiermee geeft u een set .NET-objecten voor de lijst vermelding op. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionSetName element voor de List entry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten. Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een vermelding van een lijst weergave.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
