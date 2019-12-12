---
title: ItemSelectionCondition-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356054"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)

Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) voor ListControl voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) ItemSelectionCondition-element voor de lijst item voor ListControl (Format)

## <a name="syntax"></a>Syntaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ItemSelectionCondition` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[PropertyName-element voor ItemSelectionCondition voor ListControl (indeling)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor ItemSelectionCondition voor ListControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Lijst item-element voor list items voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.|

## <a name="remarks"></a>Opmerkingen

U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Lijst item-element voor list items voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName-element voor ItemSelectionCondition voor ListControl (indeling)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Script block-element voor ItemSelectionCondition voor ListControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
