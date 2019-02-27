---
title: ScriptBlock-Element voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846499"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Het element ScriptBlock voor ListItem voor ListControl (opmaak)

Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntries voor ListControl (indeling) ListItems Element voor ListEntry voor ListControl (indeling) ListItem Element voor ListItems voor ListControl (indeling) ScriptBlock Element voor ListItem voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.|

## <a name="text-value"></a>Tekstwaarde

Geef het script waarvan de waarde wordt weergegeven in de rij.

## <a name="remarks"></a>Opmerkingen

Wanneer dit element is opgegeven, wordt u niet opgeven de [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.

Zie voor meer informatie over het opgeven van scripts in een lijst weergeven [lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u de eigenschap waarvan de waarde wordt weergegeven.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[PropertyName-Element voor ListItem voor ListControl (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Lijstitem-Element voor ListItems voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
