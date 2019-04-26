---
title: GroupBy-Element voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065532"
---
# <a name="groupby-element-for-view-format"></a>Het element GroupBy voor Weergave (opmaak)

Hiermee definieert u hoe een nieuwe groep objecten worden weergegeven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepast besturingselement weergeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u het aangepaste besturingselement die nieuwe groepen worden weergegeven.|
|[CustomControlName-Element voor GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam van een besturingselement dat wordt gebruikt om de nieuwe groep weer te geven.|
|[Label-Element voor GroupBy (indeling)](./label-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een label dat wordt weergegeven wanneer een nieuwe groep is opgetreden.|
|[PropertyName-Element voor GroupBy (indeling)](./propertyname-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap voor de start een nieuwe groep wanneer de waarde ervan verandert.|
|[ScriptBlock-Element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave met een of meer .NET-objecten.|

## <a name="remarks"></a>Opmerkingen

Bij het definiëren van hoe een nieuwe groep objecten worden weergegeven, moet u de eigenschap of het script waarmee de nieuwe groep; wordt gestart u kunt niet, beide opgeven.

## <a name="see-also"></a>Zie ook

[CustomControlName-Element voor GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md)

[Label-Element voor GroupBy (indeling)](./label-element-for-groupby-format.md)

[PropertyName-Element voor GroupBy (indeling)](./propertyname-element-for-groupby-format.md)

[ScriptBlock-Element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md)

[Weergave-Element (indeling)](./view-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
