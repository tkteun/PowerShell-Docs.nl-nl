---
title: ListEntry-Element voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065220"
---
# <a name="listentry-element-for-listcontrol-format"></a>Het element ListEntry voor ListControl (opmaak)

Bevat een definitie van de lijstweergave.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ListEntry` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor ListEntry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-objecten die gebruikmaken van de definitie van deze lijst weergeven of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|
|[ListItems Element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)|Vereist element.<br /><br /> Definieert de eigenschappen en -scripts waarvan de waarden worden weergegeven door de lijstweergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)|Bevat de definities van de lijstweergave.|

## <a name="remarks"></a>Opmerkingen

Een lijst weergeven is een lijstindeling eigenschapswaarden of script waarden voor elk object wordt weergegeven. Zie voor meer informatie over lijstweergaven [het maken van een lijstweergave](./creating-a-list-view.md).

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

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[EntrySelectedBy-Element voor ListEntry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md)

[ListItems Element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Schrijven van een Windows PowerShell opmaak en het bestand van het type](./writing-a-powershell-formatting-file.md)
