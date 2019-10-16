---
title: Selectionset-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358871"
---
# <a name="selectionset-element-format"></a>Het element SelectionSet (opmaak)

Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.

Configuratie-element (indeling) SelectionSets element (indeling) element verzameling (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSet` beschreven. Elke selectie reeks moet een naam hebben en moet de .NET-objecten van de set opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Naam element voor Selectieset (indeling)](./name-element-for-selectionset-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.|
|[Type-element (indeling)](./types-element-for-selectionset-format.md)|Vereist element.<br /><br /> Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionSets element indeling](./selectionsets-element-format.md)|Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname. Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.

Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven. In dergelijke gevallen wordt in het onderliggende `SelectionSetName`-element van de `ViewSelectedBy`-en `EntrySelectedBy`-elementen de set opgegeven die moet worden gebruikt. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `SelectionSet`-element dat vier .NET-typen definieert.

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

[Element naam van de Selectieset (indeling)](./name-element-for-selectionset-format.md)

[SelectionSets-element (indeling)](./selectionsets-element-format.md)

[Type-element (indeling)](./types-element-for-selectionset-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
