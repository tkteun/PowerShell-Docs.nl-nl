---
title: EnumerableExpansion-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066138"
---
# <a name="enumerableexpansion-element-format"></a>Het element EnumerableExpansion (opmaak)

Hiermee definieert u hoe specifieke .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.

Configuratie-Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EnumerableExpansion` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor EnumerableExpansion (indeling)](./entryselectedby-element-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee definieert u welke .NET verzameling objecten worden uitgebreid door deze definitie.|
|[Vouw Element (indeling)](./expand-element-format.md)|Hiermee geeft u op hoe het verzamelingsobject voor deze definitie is uitgevouwen.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EnumerableExpansions-Element (indeling)](./enumerableexpansions-element-format.md)|Hiermee definieert u de verschillende manieren die .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.|

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe de verzameling en de objecten in de verzameling worden weergegeven. In dit geval een verzamelingsobject verwijst naar objecten die ondersteuning biedt voor de **System.Collections.ICollection** interface.

Het standaardgedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
