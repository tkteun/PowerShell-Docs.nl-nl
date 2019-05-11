---
title: ScriptBlock-Element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229314"
---
# <a name="scriptblock-element-for-groupby-format"></a>Het element ScriptBlock voor GroupBy (opmaak)

Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) ScriptBlock-Element voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe u een groep van .NET-objecten worden weergegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef het script dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

PowerShell wordt een nieuwe groep gestart wanneer de waarde van dit script wordt gewijzigd.

Wanneer dit element is opgegeven, wordt u niet opgeven de [PropertyName](propertyname-element-for-groupby-format.md) element naar een nieuwe groep.

## <a name="see-also"></a>Zie ook

[PropertyName-Element voor GroupBy (indeling)](propertyname-element-for-groupby-format.md)

[GroupBy-Element voor weergave (indeling)](groupby-element-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](writing-a-powershell-formatting-file.md)
