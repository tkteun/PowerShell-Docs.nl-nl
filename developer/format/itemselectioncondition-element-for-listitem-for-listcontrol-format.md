---
title: ItemSelectionCondition-Element voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065441"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)

Hiermee definieert u de voorwaarde die moet bestaan voor dit item in de lijst moet worden gebruikt.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntries voor ListControl (indeling) ListItems Element voor ListEntry voor ListControl (indeling) ListItem Element voor ListItems voor ListControl (indeling) ItemSelectionCondition Element voor ListItem voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ItemSelectionCondition` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[PropertyName-Element voor ItemSelectionCondition voor ListControl (indeling)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.|
|[ScriptBlock-Element voor ItemSelectionCondition voor ListControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Lijstitem-Element voor ListItems voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.|

## <a name="remarks"></a>Opmerkingen

U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Lijstitem-Element voor ListItems voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[PropertyName-Element voor ItemSelectionCondition voor ListControl (indeling)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[ScriptBlock-Element voor ItemSelectionCondition voor ListControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
