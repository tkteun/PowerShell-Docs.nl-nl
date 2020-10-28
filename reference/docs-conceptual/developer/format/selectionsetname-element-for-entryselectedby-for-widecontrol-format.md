---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)
ms.openlocfilehash: bf6a44bb733421f36a9140d0ec10e61aedfbda6a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651700"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)

Hiermee geeft u een set .NET-objecten voor de definitie op. De definitie wordt gebruikt wanneer een van deze objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)

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
|[Het element EntrySelectedBy voor WideEntry (opmaak)](./entryselectedby-element-for-wideentry-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Elke definitie moet een type naam, selectieset of selectie voorwaarde opgeven.

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten. Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Het element EntrySelectedBy voor WideEntry (opmaak)](./entryselectedby-element-for-wideentry-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
