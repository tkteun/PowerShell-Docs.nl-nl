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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846954"
---
# <a name="scriptblock-element-for-groupby-format"></a>Het element ScriptBlock voor GroupBy (opmaak)

Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) ScriptBlock-Element voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
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

Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van dit script wordt gewijzigd.

Wanneer dit element is opgegeven, wordt u niet opgeven de [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element naar een nieuwe groep.

## <a name="see-also"></a>Zie ook

[PropertyName-Element voor GroupBy (indeling)](./propertyname-element-for-groupby-format.md)

[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)