---
title: Element een label voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065407"
---
# <a name="label-element-for-groupby-format"></a>Het element Label voor GroupBy (opmaak)

Hiermee geeft u een label dat wordt weergegeven wanneer een nieuwe groep is opgetreden.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) Label-Element voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Label` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe een nieuwe groep objecten worden weergegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de tekst die wordt weergegeven als Windows PowerShell wordt een nieuwe eigenschap of Scriptwaarde aangetroffen.

## <a name="remarks"></a>Opmerkingen

Windows PowerShell bevat naast de tekst die is opgegeven door dit element, de nieuwe waarde die wordt gestart van de groep en voegt een lege regel voor en na de groep.

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld toont het label voor een nieuwe groep. Het weergegeven label zou er ongeveer als volgt: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Zie voor een voorbeeld van een volledige opmaak bestand waarin dit element [brede weergave (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Zie ook

[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
