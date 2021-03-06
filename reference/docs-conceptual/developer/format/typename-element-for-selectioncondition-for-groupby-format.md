---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor SelectionCondition voor GroupBy (opmaak)
description: Het element TypeName voor SelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: 096d2355e113a7e44cc6ae31ea23efc3f01080a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664639"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a>Het element TypeName voor SelectionCondition voor GroupBy (opmaak)

Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor SelectionCondition voor GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het element niet opgeven `SelectionSetName` . Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
