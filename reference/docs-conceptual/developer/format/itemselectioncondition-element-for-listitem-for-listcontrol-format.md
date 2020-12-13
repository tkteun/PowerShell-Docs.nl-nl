---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)
description: Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667807"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) van het element list item (Format) voor de ListControl (indeling) element list item voor ListControl (Format) List items element voor List entry voor ListControl (Format) lijst item element voor de ListControl (indeling) ItemSelectionCondition-element

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ListItem voor ListItems voor ListControl (opmaak)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Het element ListItem voor ListItems voor ListControl (opmaak)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
