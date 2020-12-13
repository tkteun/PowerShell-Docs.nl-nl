---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor Typen (opmaak)
description: Het element TypeName voor Typen (opmaak)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664615"
---
# <a name="typename-element-for-types-format"></a>Het element TypeName voor Typen (opmaak)

Hiermee geeft u het .NET-type op van een object dat tot de selectieset behoort.

Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling)-element (Format) elementen van het type TypeName-element van typen (indeling)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven. Ten minste één `TypeName` element moet worden opgenomen in de selectieset.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Type-element (indeling)](./types-element-for-selectionset-format.md)|Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam voor het .NET-type op.

## <a name="remarks"></a>Opmerkingen

U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname. Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.

Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand. In deze gevallen `SelectionSetName` specificeert het onderliggende element van het `ViewSelectedBy` element voor de weer gave de set. Met verschillende vermeldingen in een weer gave kunt u echter ook een selectie reeks opgeven die alleen van toepassing is op die vermelding van de weer gave. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.

```
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

[Het element SelectionSets (opmaak)](./selectionsets-element-format.md)

[Type-element (indeling)](./types-element-for-selectionset-format.md)

[Een Windows PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
