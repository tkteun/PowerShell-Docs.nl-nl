---
title: ScriptBlock-Element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848228"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Het element ScriptBlock voor WideItem voor WideControl (opmaak)

Hiermee geeft u het script waarvan de waarde wordt weergegeven in de brede weergave.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) WideItem Element (indeling) ScriptBlock-Element voor WideItem (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideItem-Element (indeling)](./wideitem-element-for-widecontrol-format.md)|Hiermee definieert u de eigenschap of script blok waarvan de waarde wordt weergegeven in de brede weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef het script waarvan de waarde wordt weergegeven.

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `WideItem` element dat een script waarvan de waarde wordt weergegeven in de weergave wordt gedefinieerd.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Zie ook

[WideItem-Element (indeling)](./wideitem-element-for-widecontrol-format.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
