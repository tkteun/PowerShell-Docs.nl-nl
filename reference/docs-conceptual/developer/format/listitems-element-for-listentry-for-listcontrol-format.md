---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ListItems voor ListEntry voor ListControl (opmaak)
description: Het element ListItems voor ListEntry voor ListControl (opmaak)
ms.openlocfilehash: 1553c81bc559020223a3c1fea10336baf017c9a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666532"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Het element ListItems voor ListEntry voor ListControl (opmaak)

Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de rijen van de lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element van het type list item (indeling) voor het besturings element List Control (Format) voor ListControl (Format) List items element voor ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListItems` element beschreven. Er is geen limiet voor het aantal onderliggende elementen dat kan worden opgegeven. De volg orde van de onderliggende elementen definieert de volg orde waarin waarden worden weer gegeven in de lijst weergave.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Lijst item-element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Vereist element.<br /><br /> Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de lijst weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ListEntry voor ListControl (opmaak)](./listentry-element-for-listcontrol-format.md)|Geeft een definitie van de lijst weergave.|

## <a name="remarks"></a>Opmerkingen

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over dit type weer gave.

## <a name="example"></a>Voorbeeld

In dit voor beeld worden de XML-elementen weer gegeven waarmee drie rijen van de lijst weergave worden gedefinieerd.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Zie ook

[Het element ListEntry voor ListControl (opmaak)](./listentry-element-for-listcontrol-format.md)

[Lijst item-element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een lijstweergave maken](./creating-a-list-view.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
