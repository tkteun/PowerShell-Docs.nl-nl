---
title: Element van het type voor SelectionSet (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851273"
---
# <a name="types-element-for-selectionset-format"></a>Het element Typen voor SelectionSet (opmaak)

Hiermee definieert u de .NET-objecten die in de selectie.

Configuratie Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling) van het type Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Types` element. Er moet ten minste één onderliggend element, maar er is geen maximale limiet voor het aantal onderliggende elementen die kunnen worden toegevoegd.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[TypeName Element van de typen (indeling)](./typename-element-for-types-format.md)|Vereist element.<br /><br /> Hiermee geeft u de .NET-object die deel uitmaakt van de selectieset.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionSet-Element (indeling)](./selectionset-element-format.md)|Hiermee definieert een set van .NET-objecten die kan worden verwezen door de naam van de set.|

## <a name="remarks"></a>Opmerkingen

De objecten die zijn gedefinieerd door dit element gezamenlijk een selectie instellen die door een weergave kan worden gebruikt door een definitie van een weergave (weergaven kunnen meerdere definities hebben), of wanneer een selectievoorwaarde op te geven.  Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `SelectionSet` element waarin vier .NET-typen.

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

[Sets van objecten te definiëren](./defining-selection-sets.md)

[SelectionSet-Element (indeling)](./selectionset-element-format.md)

[TypeName Element van de typen (indeling)](./typename-element-for-types-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
