---
title: EnumerableExpansions-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066087"
---
# <a name="enumerableexpansions-element-format"></a>Het element EnumerableExpansions (opmaak)

Hiermee definieert u hoe .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.

Configuratie Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EnumerableExpansions` element. Er is geen limiet voor het aantal onderliggende elementen die u kunt gebruiken.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[EnumerableExpansion-Element (indeling)](./enumerableexpansion-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de specifieke versie van .NET verzameling objecten die worden uitgevouwen wanneer ze worden weergegeven in een weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[DefaultSettings-Element (indeling)](./defaultsettings-element-format.md)|Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert.|

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe de verzameling en de objecten in de verzameling worden weergegeven. In dit geval een verzamelingsobject verwijst naar objecten die ondersteuning biedt voor de **System.Collections.ICollection** interface.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
