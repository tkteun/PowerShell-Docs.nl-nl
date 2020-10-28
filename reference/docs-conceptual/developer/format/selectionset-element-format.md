---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSet (opmaak)
description: Het element SelectionSet (opmaak)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647875"
---
# <a name="selectionset-element-format"></a>Het element SelectionSet (opmaak)

Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.

Configuratie-element (indeling) SelectionSets element (indeling) element verzameling (indeling)

## <a name="syntax"></a>Syntax

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSet` element beschreven. Elke selectie reeks moet een naam hebben en moet de .NET-objecten van de set opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Naam voor SelectionSet (opmaak)](./name-element-for-selectionset-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.|
|[Type-element (indeling)](./types-element-for-selectionset-format.md)|Vereist element.<br /><br /> Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionSets element indeling](./selectionsets-element-format.md)|Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname. Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.

Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven. In deze gevallen geeft het `SelectionSetName` onderliggende element van de- `ViewSelectedBy` en- `EntrySelectedBy` elementen de set op die moet worden gebruikt. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.

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

[Element naam van de Selectieset (indeling)](./name-element-for-selectionset-format.md)

[Het element SelectionSets (opmaak)](./selectionsets-element-format.md)

[Type-element (indeling)](./types-element-for-selectionset-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
