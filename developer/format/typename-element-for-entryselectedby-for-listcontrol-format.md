---
title: TypeName-Element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084025"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)

Hiermee geeft u een .NET-type dat deze vermelding van de lijstweergave gebruikt. Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor een lijstitem.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) TypeName-Element voor EntrySelectedBy voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor ListEntry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding lijst of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

Elk lijstitem moet hebben ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd.

Zie voor meer informatie over hoe dit element wordt gebruikt in een lijst weergeven, [lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u een selectie instellen voor een vermelding van een lijst weergeven.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Zie ook

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[EntrySelectedBy-Element voor ListEntry (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[SelectionSetName-Element voor EntrySelectedBy voor ListEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
