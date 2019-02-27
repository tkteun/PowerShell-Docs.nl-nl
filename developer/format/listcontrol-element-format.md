---
title: ListControl Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847829"
---
# <a name="listcontrol-element-format"></a>Het element ListControl (opmaak)

Hiermee definieert u een indeling voor de weergave heeft.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) ListControl Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ListControl` element. Dit element moet slechts één onderliggend element bevatten.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)|Vereist element.<br /><br /> Bevat de definities van de lijstweergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave die wordt gebruikt om de leden van een of meer objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over het maken van een lijstweergave [het maken van een lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een lijst weergeven voor de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[Weergave-Element (indeling)](./view-element-format.md)

[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Schrijven van een Windows PowerShell opmaak en het bestand van het type](./writing-a-powershell-formatting-file.md)
