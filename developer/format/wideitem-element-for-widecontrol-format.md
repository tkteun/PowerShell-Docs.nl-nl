---
title: WideItem-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083634"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Het element WideItem voor WideControl (opmaak)

Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) WideItem-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `WideItem` element. De `FormatString` element is optioneel. Echter, moet u een `PropertyName` of `ScriptBlock` element, maar u kunt niet beide opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[FormatString-Element voor WideItem voor WideControl (indeling)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave.|
|[PropertyName-Element voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Hiermee geeft u de eigenschap van het object waarvan de waarde wordt weergegeven in de brede weergave.|
|[ScriptBlock-Element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Hiermee geeft u het script waarvan de waarde wordt weergegeven in de brede weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideEntry-Element (indeling)](./wideentry-element-for-widecontrol-format.md)|Bevat een definitie van de brede weergave.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een brede weergave [brede weergave](./creating-a-wide-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `WideEntry` element waarin één `WideItem` element. De `WideItem` element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de weergave.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).

## <a name="see-also"></a>Zie ook

[FormatString-Element voor WideItem voor WideControl (indeling)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName-Element voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[ScriptBlock-Element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry-Element (indeling)](./wideentry-element-for-widecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
