---
title: PropertyName-Element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851896"
---
# <a name="propertyname-element-for-groupby-format"></a>Het element PropertyName voor GroupBy (opmaak)

Hiermee geeft u de .NET-eigenschap die een nieuwe groep wordt gestart wanneer de waarde ervan verandert.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) PropertyName-Element voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe u een groep van .NET-objecten worden weergegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de .NET-eigenschap.

## <a name="remarks"></a>Opmerkingen

Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van deze eigenschap wordt gewijzigd.

Wanneer dit element is opgegeven, wordt u niet opgeven de [ScriptBlock](./scriptblock-element-for-groupby-format.md) element naar een nieuwe groep.

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u een nieuwe groep wordt gestart wanneer de waarde van een eigenschap wijzigt.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Zie voor een voorbeeld van een volledige opmaak bestand waarin dit element [brede weergave (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Zie ook

[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)

[ScriptBlock-Element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
