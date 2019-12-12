---
title: Element uitbreiden (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358971"
---
# <a name="expand-element-format"></a>Het element Uitvouwen (opmaak)

Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) element uitbreiden (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Expand` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EnumerableExpansion-element (indeling)](./enumerableexpansion-element-format.md)|Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef een van de volgende waarden op:

- EnumOnly: alleen de eigenschappen van de objecten in de verzameling worden weer gegeven.

- CoreOnly: alleen de eigenschappen van het verzamelings object worden weer gegeven.

- Beide: Hiermee worden de eigenschappen van de objecten in de verzameling en de eigenschappen van het verzamelings object weer gegeven.

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven. In dit geval verwijst een verzamelings object naar een object dat de interface **System. Collections. ICollection** ondersteunt.

Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
