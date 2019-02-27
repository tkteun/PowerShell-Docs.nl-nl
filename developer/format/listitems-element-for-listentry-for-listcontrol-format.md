---
title: ListItems-Element voor ListEntry voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848620"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Het element ListItems voor ListEntry voor ListControl (opmaak)

Definieert de eigenschappen en -scripts waarvan de waarden worden weergegeven in de rijen van de lijstweergave.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor lijst besturingselement (indeling) ListEntry-Element voor ListControl (indeling) ListItems Element voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ListItems` element. Er is geen limiet voor het aantal onderliggende elementen die kunnen worden opgegeven. De volgorde van de onderliggende elementen bepaalt de volgorde die waarden worden weergegeven in de lijstweergave.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Lijstitem-Element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Vereist element.<br /><br /> Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de lijstweergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListEntry-Element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)|Bevat een definitie van de lijstweergave.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over dit type weergave [het maken van een lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u de XML-elementen die drie rijen van de lijstweergave definiëren.

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

[ListEntry-Element voor ListControl (indeling)](./listentry-element-for-listcontrol-format.md)

[Lijstitem-Element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
