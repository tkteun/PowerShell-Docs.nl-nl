---
title: Script block-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355788"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Het element ScriptBlock voor ListItem voor ListControl (opmaak)

Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) voor ListControl voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) script block-element voor de lijst item voor ListControl (Format)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op waarvan de waarde wordt weer gegeven in de rij.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het kenmerk [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) niet opgeven.

Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het opgeven van scripts in een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u de eigenschap kunt opgeven waarvan de waarde wordt weer gegeven.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[PropertyName-element voor lijst item voor ListControl (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Een lijst weergave maken](./creating-a-list-view.md)

[Lijst item-element voor list items voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
