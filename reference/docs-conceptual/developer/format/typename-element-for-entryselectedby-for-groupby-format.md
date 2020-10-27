---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)
description: Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)
ms.openlocfilehash: 07cc92e9c501aa0eb2d219e416851be0fcd80f47
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645714"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)

Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het aangepaste besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry-element voor CustomControl voor het element GroupBy (Format) voor CustomEntry voor het object GroupBy (Format)

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
|[Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.

## <a name="see-also"></a>Zie ook

[Aangepaste besturingselementen maken](./creating-custom-controls.md)

[Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
