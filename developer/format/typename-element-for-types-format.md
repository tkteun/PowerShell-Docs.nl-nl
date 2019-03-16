---
title: TypeName-Element voor typen die zijn (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057923"
---
# <a name="typename-element-for-types-format"></a>Het element TypeName voor Typen (opmaak)

Hiermee geeft u de .NET-type van een object dat bij de selectieset hoort.

Configuratie Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling) van het type Element (indeling) TypeName Element van de typen (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element. Ten minste één `TypeName` element moet worden opgenomen in de selectieset.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Typen Element (indeling)](./types-element-for-selectionset-format.md)|Hiermee definieert u de .NET-objecten die in de selectie.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam voor het .NET-type.

## <a name="remarks"></a>Opmerkingen

U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt. Bij het definiëren van uw weergaven, kunt u de set objecten opgeven met behulp van de naam van de selectie instellen in plaats van de lijst van alle objecten in elke weergave.

Algemene selectiesets worden opgegeven door de naam bij het definiëren van de weergaven van de opmaak-bestand. In dergelijke gevallen de `SelectionSetName` onderliggend element van de `ViewSelectedBy` -element voor de weergave bevat de set. Verschillende vermeldingen van een weergave kunnen echter ook een selectie instellen die van toepassing op alleen die vermelding van de weergave opgeven. Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `SelectionSet` element waarin vier .NET-typen.

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

[Selectiesets definiëren](./defining-selection-sets.md)

[SelectionSet-Element (indeling)](./selectionset-element-format.md)

[SelectionSets-Element (indeling)](./selectionsets-element-format.md)

[Typen Element (indeling)](./types-element-for-selectionset-format.md)

[Een Windows PowerShell opmaak bestand schrijven](./writing-a-powershell-formatting-file.md)
