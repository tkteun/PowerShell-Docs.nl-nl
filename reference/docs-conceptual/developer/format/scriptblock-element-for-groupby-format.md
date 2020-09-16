---
title: Script block-element voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e761e02a7910cd598449d564e827889162da9f25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787679"
---
# <a name="scriptblock-element-for-groupby-format"></a>Het element ScriptBlock voor GroupBy (opmaak)

Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (Format) script block-element voor GroupBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Power shell start een nieuwe groep wanneer de waarde van dit script wordt gewijzigd.

Als dit element is opgegeven, kunt u het element [PropertyName](propertyname-element-for-groupby-format.md) niet opgeven om een nieuwe groep te starten.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor GroupBy (opmaak)](propertyname-element-for-groupby-format.md)

[Het element GroupBy voor Weergave (opmaak)](groupby-element-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](writing-a-powershell-formatting-file.md)
