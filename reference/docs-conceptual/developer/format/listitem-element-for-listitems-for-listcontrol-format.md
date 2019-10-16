---
title: Lijst item-element voor list items voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356012"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Het element ListItem voor ListItems voor ListControl (opmaak)

Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (indeling) element entry View voor ListControl (Format) List items element voor ListControl Lijst item voor het element ListControl (indeling)

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

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ListItem` beschreven. Er kan slechts één eigenschap of script worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element formats Tring voor lijst item voor ListControl (indeling)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Geeft een indelings teken reeks die definieert hoe de eigenschap of script waarde wordt weer gegeven.|
|[ItemSelectionCondition-element voor lijst item voor ListControl (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.|
|[Element label voor lijst item voor ListControl (indeling)](./label-element-for-listitem-for-listcontrol-format.md)|Optioneel element<br /><br /> Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.|
|[PropertyName-element voor lijst item voor ListControl (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de rij.|
|[Script block-element voor lijst item voor ListControl (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[List items-element voor lijst besturings element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)|Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de lijst weergave.|

## <a name="remarks"></a>Opmerkingen

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld worden de XML-elementen weer gegeven waarmee drie rijen van de lijst weergave worden gedefinieerd. In de eerste twee rijen wordt de waarde van een .NET-eigenschap weer gegeven en in de laatste rij wordt een waarde weer gegeven die door een script is gegenereerd.

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

[List items-element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Element formats Tring voor lijst item (indeling)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Element label voor lijst item (indeling)](./label-element-for-listitem-for-listcontrol-format.md)

[Het element PropertyName voor lijst item (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Script block-element voor lijst item (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Een lijst weergave maken](./creating-a-list-view.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
