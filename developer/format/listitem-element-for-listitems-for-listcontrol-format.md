---
title: Lijstitem-Element voor ListItems voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846219"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Het element ListItem voor ListItems voor ListControl (opmaak)

Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListControl (indeling) ListItems Element voor ListControl (indeling) ListItem voor ListControl-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ListItem` element. Slechts één eigenschap of het script kan worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[FormatString-Element voor ListItem voor ListControl (indeling)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een opmaaktekenreeks waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven.|
|[ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor dit item in de lijst moet worden gebruikt.|
|[Label-Element voor ListItem voor ListControl (indeling)](./label-element-for-listitem-for-listcontrol-format.md)|Optioneel element<br /><br /> Hiermee geeft u het label dat wordt weergegeven aan de linkerkant van de waarde voor eigenschap of het script in de rij.|
|[PropertyName-Element voor ListItem voor ListControl (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap waarvan de waarde wordt weergegeven in de rij.|
|[ScriptBlock-Element voor ListItem voor ListControl (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListItems-Element voor het besturingselement (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definieert de eigenschappen en -scripts waarvan de waarden worden weergegeven in de lijstweergave.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u de XML-elementen die drie rijen van de lijstweergave definiëren. De waarde van een .NET-eigenschap van de eerste twee rijen weergeven en de laatste rij wordt een waarde die is gegenereerd door een script.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Zie ook

[ListItems Element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)

[FormatString-Element voor ListItem (indeling)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Label-Element voor ListItem (indeling)](./label-element-for-listitem-for-listcontrol-format.md)

[PropertyName-Element voor ListItem (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ScriptBlock-Element voor ListItem (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Schrijven van een Windows PowerShell opmaak en het bestand van het type](./writing-a-powershell-formatting-file.md)
