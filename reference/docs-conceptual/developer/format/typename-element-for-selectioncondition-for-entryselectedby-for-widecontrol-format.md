---
title: TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5021f665b994581f9ff982e13af922d7940ebf2b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783310"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Het element TypeName voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)

Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de definitie gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)

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
|[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Hiermee definieert u de voor waarde die voor deze brede vermelding moet bestaan om te worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Met de selectie voorwaarde kan een .NET-type of een selectieset worden opgegeven, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
