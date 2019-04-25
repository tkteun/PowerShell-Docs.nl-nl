---
title: WideEntries-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083685"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Het element WideEntries voor WideControl (opmaak)

Bevat de definities van de brede weergave. De brede weergave moet een of meer netwerkdefinities opgeven.

Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)

## <a name="syntax"></a>Syntaxis

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `WideEntries` element. Ten minste één onderliggend element moet worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideEntry-Element (indeling)](./wideentry-element-for-widecontrol-format.md)|Bevat een definitie van de brede weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideControl-Element (indeling)](./widecontrol-element-format.md)|Definieert een breed (één waarde) lijstweergave voor de weergave.|

## <a name="remarks"></a>Opmerkingen

Een brede weergave wordt een lijst met-indeling die een waarde van één eigenschap of Scriptwaarde voor elk object wordt weergegeven. Zie voor meer informatie over de onderdelen van een brede weergave [brede weergave onderdelen](./creating-a-wide-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `WideEntries` element waarin één `WideEntry` element. De `WideEntry` element bevat één `WideItem` element waarmee wordt gedefinieerd welke waarde voor eigenschap of het script wordt weergegeven in de weergave.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).

## <a name="see-also"></a>Zie ook

[Het maken van een brede weergave](./creating-a-wide-view.md)

[WideControl-Element (indeling)](./widecontrol-element-format.md)

[WideEntry-Element (indeling)](./wideentry-element-for-widecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
