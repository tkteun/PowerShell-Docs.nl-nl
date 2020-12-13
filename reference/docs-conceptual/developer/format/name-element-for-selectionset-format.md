---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Naam voor SelectionSet (opmaak)
description: Het element Naam voor SelectionSet (opmaak)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666452"
---
# <a name="name-element-for-selectionset-format"></a>Het element Naam voor SelectionSet (opmaak)

Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.

Configuratie-element (indeling) SelectionSets element (Format) element van de verzameling (indeling) naam element van de Selectieset (indeling)

## <a name="syntax"></a>Syntax

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionSet (opmaak)](./selectionset-element-format.md)|Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op om te verwijzen naar de selectieset. Er zijn geen beperkingen met betrekking tot welke tekens kunnen worden gebruikt.

## <a name="remarks"></a>Opmerkingen

De naam die u hier opgeeft, wordt gebruikt in het- `SelectionSetName` element. De selectieset die kan worden gebruikt door een weer gave, door een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert. De naam van de selectieset is ' FileSystemTypes '.

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Zie ook

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Het element SelectionSet (opmaak)](./selectionset-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
