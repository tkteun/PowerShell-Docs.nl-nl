---
title: PropertyName-element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354185"
---
# <a name="propertyname-element-for-groupby-format"></a>Het element PropertyName voor GroupBy (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor de eigenschap element van de weer gave (indeling) voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.|

## <a name="text-value"></a>Tekst waarde

Geef de .NET-eigenschaps naam op.

## <a name="remarks"></a>Opmerkingen

Windows Power shell start een nieuwe groep wanneer de waarde van deze eigenschap wordt gewijzigd.

Als dit element is opgegeven, kunt u het [script Block](./scriptblock-element-for-groupby-format.md) -element niet opgeven om een nieuwe groep te starten.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een nieuwe groep kunt starten wanneer de waarde van een eigenschap wordt gewijzigd.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand dat dit element bevat.

## <a name="see-also"></a>Zie ook

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

[Script block-element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
