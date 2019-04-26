---
title: Naam van Element voor SelectionSet (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065149"
---
# <a name="name-element-for-selectionset-format"></a>Het element Naam voor SelectionSet (opmaak)

Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de selectieset.

Configuratie-Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling) de naam van Element van SelectionSet (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Name` Element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionSet-Element (indeling)](./selectionset-element-format.md)|Definieert één set met .NET-objecten die kan worden verwezen door de naam van de set.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam om te verwijzen naar de selectieset. Er zijn geen beperkingen voor welke tekens kunnen worden gebruikt.

## <a name="remarks"></a>Opmerkingen

De naam die u hier opgeeft, wordt gebruikt in de `SelectionSetName` element. De van selectieset die door een weergave kan worden gebruikt door een definitie van een weergave (weergaven kunnen meerdere definities hebben), of wanneer een selectievoorwaarde op te geven. Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `SelectionSet` element waarin vier .NET-typen. De naam van de selectieset is 'FileSystemTypes'.

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

[SelectionSet-Element (indeling)](./selectionset-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
