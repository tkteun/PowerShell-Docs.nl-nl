---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ListItem voor ListControl (opmaak)
description: Het element ScriptBlock voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 0635ac2622cc203a2dc895873621901d956f87da
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664975"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Het element ScriptBlock voor ListItem voor ListControl (opmaak)

Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) van het element list item (Format) voor de ListControl (indeling) element list item voor ListControl (Format) List items element voor List entry voor ListControl (Format) lijst item element voor de ListControl (indeling) script block-element

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.

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

[Het element PropertyName voor ListItem voor ListControl (opmaak)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Een lijstweergave maken](./creating-a-list-view.md)

[Het element ListItem voor ListItems voor ListControl (opmaak)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
