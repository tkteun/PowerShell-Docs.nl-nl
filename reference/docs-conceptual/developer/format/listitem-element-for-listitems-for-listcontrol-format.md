---
title: Lijst item-element voor list items voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e72a887e8bd1f93bacb663e3079eeaec34bdfa51
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785673"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Het element ListItem voor ListItems voor ListControl (opmaak)

Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (Format) element list item voor ListControl (Format) List items element voor ListControl (Format) lijst item voor ListControl-element (Format)

## <a name="syntax"></a>Syntax

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

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListItem` element beschreven. Er kan slechts één eigenschap of script worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element formats Tring voor lijst item voor ListControl (indeling)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Geeft een indelings teken reeks die definieert hoe de eigenschap of script waarde wordt weer gegeven.|
|[Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.|
|[Het element Label voor ListItem voor ListControl (opmaak)](./label-element-for-listitem-for-listcontrol-format.md)|Optioneel element<br /><br /> Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.|
|[Het element PropertyName voor ListItem voor ListControl (opmaak)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de rij.|
|[Het element ScriptBlock voor ListItem voor ListControl (opmaak)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.|

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

[Een lijstweergave maken](./creating-a-list-view.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
