---
title: Script block-element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355872"
---
# <a name="scriptblock-element-for-groupby-format"></a>Het element ScriptBlock voor GroupBy (opmaak)

Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (Format) script block-element voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.|

## <a name="text-value"></a>Tekst waarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Power shell start een nieuwe groep wanneer de waarde van dit script wordt gewijzigd.

Als dit element is opgegeven, kunt u het element [PropertyName](propertyname-element-for-groupby-format.md) niet opgeven om een nieuwe groep te starten.

## <a name="see-also"></a>Zie ook

[PropertyName-element voor GroupBy (indeling)](propertyname-element-for-groupby-format.md)

[Element GroupBy voor weer gave (indeling)](groupby-element-for-view-format.md)

[Een Power shell-indelings bestand schrijven](writing-a-powershell-formatting-file.md)
