---
title: List items-element voor List entry voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354339"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Het element ListItems voor ListEntry voor ListControl (opmaak)

Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de rijen van de lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element van het type list item (indeling) voor het besturings element List Control (Format) voor ListControl (Format) List items element voor ListControl (Format)

## <a name="syntax"></a>Syntaxis

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ListItems` beschreven. Er is geen limiet voor het aantal onderliggende elementen dat kan worden opgegeven. De volg orde van de onderliggende elementen definieert de volg orde waarin waarden worden weer gegeven in de lijst weergave.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Lijst item-element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Vereist element.<br /><br /> Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de lijst weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[List Entry-element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)|Geeft een definitie van de lijst weergave.|

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

[List Entry-element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)

[Lijst item-element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een lijst weergave maken](./creating-a-list-view.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
