---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)
description: Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654781"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)

Hiermee geeft u een .NET-type voor de definitie op. De definitie wordt gebruikt wanneer dit object wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (indeling) element-TypeName voor WideEntry (indeling)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor WideEntry (opmaak)](./entryselectedby-element-for-wideentry-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze brede vermelding of de voor waarde die moet bestaan voor deze vermelding.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Elke uitgebreide vermelding moet een of meer .NET-typen, een selectieset of de selectie voorwaarde opgeven die moet bestaan voor de definitie die u wilt gebruiken.

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Het element EntrySelectedBy voor WideEntry (opmaak)](./entryselectedby-element-for-wideentry-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
