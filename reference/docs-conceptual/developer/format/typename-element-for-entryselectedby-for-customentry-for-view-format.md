---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)
description: Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645741"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)

Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de aangepaste beheer weergave. Er is geen limiet voor het aantal typen dat voor een definitie kan worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (Format) voor EntrySelectedBy voor CustomEntry

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
|[EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste besturings element weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Voor elke aangepaste controle weergave definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.

## <a name="see-also"></a>Zie ook

[Aangepaste besturingselementen maken](./creating-custom-controls.md)

[EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
