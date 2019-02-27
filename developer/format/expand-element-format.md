---
title: Vouw Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848613"
---
# <a name="expand-element-format"></a>Het element Uitvouwen (opmaak)

Hiermee geeft u op hoe het verzamelingsobject voor deze definitie is uitgevouwen.

Configuratie-Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion Element (indeling) Vouw Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Expand` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EnumerableExpansion-Element (indeling)](./enumerableexpansion-element-format.md)|Hiermee definieert u hoe specifieke .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef een van de volgende waarden:

- EnumOnly: Geeft alleen de eigenschappen van de objecten in de verzameling.

- CoreOnly: Geeft alleen de eigenschappen van het verzamelingsobject.

- Beide: Geeft de eigenschappen van de objecten in de verzameling en de eigenschappen van het verzamelingsobject.

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe de verzameling en de objecten in de verzameling worden weergegeven. In dit geval een verzamelingsobject verwijst naar objecten die ondersteuning biedt voor de **System.Collections.ICollection** interface.

Het standaardgedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
