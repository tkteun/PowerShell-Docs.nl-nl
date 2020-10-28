---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ListEntry voor ListControl (opmaak)
description: Het element ListEntry voor ListControl (opmaak)
ms.openlocfilehash: 96ae5fcdd837d2491d6c7ff6a375fef1d83ae3e9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666566"
---
# <a name="listentry-element-for-listcontrol-format"></a>Het element ListEntry voor ListControl (opmaak)

Geeft een definitie van de lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl-element (indeling) element (indeling) List item (Format)

## <a name="syntax"></a>Syntax

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListEntry` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-objecten die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.|
|[List items-element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)|Vereist element.<br /><br /> Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de lijst weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element List Entries (indeling)](./listentries-element-for-listcontrol-format.md)|Biedt de definities van de lijst weergave.|

## <a name="remarks"></a>Opmerkingen

Een lijst weergave is een lijst indeling waarin eigenschapwaarden of script waarden voor elk object worden weer gegeven. Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over lijst weergaven.

## <a name="example"></a>Voorbeeld

In dit voor beeld worden de XML-elementen weer gegeven die de lijst weergave definiëren voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[Een lijstweergave maken](./creating-a-list-view.md)

[Element EntrySelectedBy voor List entry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Element List Entries (indeling)](./listentries-element-for-listcontrol-format.md)

[List items-element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
