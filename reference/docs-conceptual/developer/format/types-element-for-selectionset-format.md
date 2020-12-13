---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Typen voor SelectionSet (opmaak)
description: Het element Typen voor SelectionSet (opmaak)
ms.openlocfilehash: ff3c24e7f52f862dc416b88d50983196ce907012
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645460"
---
# <a name="types-element-for-selectionset-format"></a>Het element Typen voor SelectionSet (opmaak)

Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.

Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling) element (indeling)

## <a name="syntax"></a>Syntax

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Types` element beschreven. Er moet ten minste één onderliggend element zijn, maar er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden toegevoegd.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TypeName-element van typen (indeling)](./typename-element-for-types-format.md)|Vereist element.<br /><br /> Hiermee geeft u het .NET-object op dat deel uitmaakt van de selectieset.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionSet (opmaak)](./selectionset-element-format.md)|Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.|

## <a name="remarks"></a>Opmerkingen

De objecten die door dit element worden gedefinieerd, vormen een selectie reeks die kan worden gebruikt door een weer gave, op basis van een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven.  Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.

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

[Sets van objecten definiëren](./defining-selection-sets.md)

[Het element SelectionSet (opmaak)](./selectionset-element-format.md)

[TypeName-element van typen (indeling)](./typename-element-for-types-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
