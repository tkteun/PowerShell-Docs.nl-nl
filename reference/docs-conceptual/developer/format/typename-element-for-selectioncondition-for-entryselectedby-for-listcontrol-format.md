---
title: TypeName-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bc58d630e65b316f9223bf3c529f928358e38ebc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787372"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Het element TypeName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)

Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de vermelding in de lijst gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het object (indeling) ListControl element (indeling) (Format) element list item voor ListControl (indeling) element List entry voor List Entries (Format) EntrySelectedBy element voor List entry voor ListControl (Format) SelectionCondition-element voor het object voor de ListControl (Format) voor de SelectionCondition voor ListControl (indeling)

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
|[Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
