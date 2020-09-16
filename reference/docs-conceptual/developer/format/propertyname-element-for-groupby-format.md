---
title: PropertyName-element voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e83ebd49e4f3087c817b3cc8772889dbe85113aa
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785605"
---
# <a name="propertyname-element-for-groupby-format"></a>Het element PropertyName voor GroupBy (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor de eigenschap element van de weer gave (indeling) voor GroupBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe een groep .NET-objecten wordt weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

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

[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)

[Het element ScriptBlock voor GroupBy (opmaak)](./scriptblock-element-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
