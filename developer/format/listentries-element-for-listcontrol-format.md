---
title: ListEntries-Element voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847360"
---
# <a name="listentries-element-for-listcontrol-format"></a>Het element ListEntries voor ListControl (opmaak)

Bevat de definities van de lijstweergave. De lijstweergave moet een of meer netwerkdefinities opgeven.

Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)

## <a name="syntax"></a>Syntaxis

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ListEntries` element. Ten minste één onderliggend element moet worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListEntry-Element (indeling)](./listentry-element-for-listcontrol-format.md)|Bevat een definitie van de lijstweergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListControl Element (indeling)](./listcontrol-element-format.md)|Hiermee definieert u een indeling voor de weergave heeft.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over lijstweergaven [lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u de XML-elementen die definiëren in de lijstweergave voor de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[ListControl Element (indeling)](./listcontrol-element-format.md)

[ListEntry-Element (indeling)](./listentry-element-for-listcontrol-format.md)

[Lijstweergave](./creating-a-list-view.md)

[Schrijven van een Windows PowerShell opmaak en het bestand van het type](./writing-a-powershell-formatting-file.md)
