---
title: SelectionSet-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076307"
---
# <a name="selectionset-element-format"></a>Het element SelectionSet (opmaak)

Hiermee definieert een set van .NET-objecten die kan worden verwezen door de naam van de set.

Configuratie Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSet` element. Elke selectieset moet een naam hebben en deze de .NET-objecten van de set moet opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[De van naamelement voor SelectionSet (indeling)](./name-element-for-selectionset-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de selectieset.|
|[Typen Element (indeling)](./types-element-for-selectionset-format.md)|Vereist element.<br /><br /> Hiermee definieert u de .NET-objecten die in de selectie.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionSets Element opmaken](./selectionsets-element-format.md)|Hiermee definieert u de algemene sets met .NET-objecten die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.|

## <a name="remarks"></a>Opmerkingen

U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt. Bij het definiëren van uw weergaven, kunt u de set objecten opgeven met behulp van de naam van de selectie instellen in plaats van de lijst van alle objecten in elke weergave.

Algemene selectiesets worden opgegeven door de naam bij het definiëren van de weergaven van de opmaak bestand of de definities van de weergaven. In dergelijke gevallen de `SelectionSetName` onderliggend element van de `ViewSelectedBy` en `EntrySelectedBy` elementen Hiermee geeft u de set moet worden gebruikt. Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `SelectionSet` element waarin vier .NET-typen.

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

[Selectiesets definiëren](./defining-selection-sets.md)

[De van naamelement van SelectionSet (indeling)](./name-element-for-selectionset-format.md)

[SelectionSets-Element (indeling)](./selectionsets-element-format.md)

[Typen Element (indeling)](./types-element-for-selectionset-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
