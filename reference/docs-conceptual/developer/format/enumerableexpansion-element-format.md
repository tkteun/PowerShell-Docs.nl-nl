---
title: EnumerableExpansion-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358975"
---
# <a name="enumerableexpansion-element-format"></a>Het element EnumerableExpansion (opmaak)

Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EnumerableExpansion` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor EnumerableExpansion (indeling)](./entryselectedby-element-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee definieert u welke .NET-verzamelings objecten worden uitgevouwen door deze definitie.|
|[Element uitbreiden (indeling)](./expand-element-format.md)|Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EnumerableExpansions-element (indeling)](./enumerableexpansions-element-format.md)|Definieert de verschillende manieren waarop .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven. In dit geval verwijst een verzamelings object naar een object dat de interface **System. Collections. ICollection** ondersteunt.

Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
