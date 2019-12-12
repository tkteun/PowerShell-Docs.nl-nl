---
title: TypeName-element voor typen (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358737"
---
# <a name="typename-element-for-types-format"></a>Het element TypeName voor Typen (opmaak)

Hiermee geeft u het .NET-type op van een object dat tot de selectieset behoort.

Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling)-element (Format) elementen van het type TypeName-element van typen (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven. Ten minste één `TypeName` element moet worden opgenomen in de selectieset.

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

Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand. In dergelijke gevallen specificeert het `SelectionSetName` onderliggende element van het `ViewSelectedBy` element voor de weer gave de set. Met verschillende vermeldingen in een weer gave kunt u echter ook een selectie reeks opgeven die alleen van toepassing is op die vermelding van de weer gave. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `SelectionSet`-element waarmee vier .NET-typen worden gedefinieerd.

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

[Selectie sets definiëren](./defining-selection-sets.md)

[Selectie verzamelings element (indeling)](./selectionset-element-format.md)

[SelectionSets-element (indeling)](./selectionsets-element-format.md)

[Type-element (indeling)](./types-element-for-selectionset-format.md)

[Een Windows Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
