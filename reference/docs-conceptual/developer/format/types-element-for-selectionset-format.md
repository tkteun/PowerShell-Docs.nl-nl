---
title: Type-element voor Selectieset (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358743"
---
# <a name="types-element-for-selectionset-format"></a>Het element Typen voor SelectionSet (opmaak)

Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.

Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling) element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Types` beschreven. Er moet ten minste één onderliggend element zijn, maar er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden toegevoegd.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TypeName-element van typen (indeling)](./typename-element-for-types-format.md)|Vereist element.<br /><br /> Hiermee geeft u het .NET-object op dat deel uitmaakt van de selectieset.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Selectie verzamelings element (indeling)](./selectionset-element-format.md)|Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.|

## <a name="remarks"></a>Opmerkingen

De objecten die door dit element worden gedefinieerd, vormen een selectie reeks die kan worden gebruikt door een weer gave, op basis van een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven.  Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `SelectionSet`-element dat vier .NET-typen definieert.

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

[Selectie verzamelings element (indeling)](./selectionset-element-format.md)

[TypeName-element van typen (indeling)](./typename-element-for-types-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
