---
title: Naam element voor Selectieset (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354290"
---
# <a name="name-element-for-selectionset-format"></a>Het element Naam voor SelectionSet (opmaak)

Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.

Configuratie-element (indeling) SelectionSets element (Format) element van de verzameling (indeling) naam element van de Selectieset (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Name` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Selectie verzamelings element (indeling)](./selectionset-element-format.md)|Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op om te verwijzen naar de selectieset. Er zijn geen beperkingen met betrekking tot welke tekens kunnen worden gebruikt.

## <a name="remarks"></a>Opmerkingen

De naam die u hier opgeeft, wordt gebruikt in het element `SelectionSetName`. De selectieset die kan worden gebruikt door een weer gave, door een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

Dit voor beeld toont een `SelectionSet`-element waarmee vier .NET-typen worden gedefinieerd. De naam van de selectieset is ' FileSystemTypes '.

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

[Selectie sets definiëren](./defining-selection-sets.md)

[Selectie verzamelings element (indeling)](./selectionset-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
