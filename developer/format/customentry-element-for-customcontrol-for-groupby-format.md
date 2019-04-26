---
title: CustomEntry-Element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066470"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Het element CustomEntry voor CustomControl voor GroupBy (opmaak)

Bevat een definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `CustomEntry` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|
|[CustomItem-Element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)|Vereist element.<br /><br /> Hiermee definieert u hoe de gegevens in het besturingselement wordt weergegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntries-Element voor CustomControl voor GroupBy (indeling)](./customentries-element-for-customcontrol-for-groupby-format.md)|Bevat de definities voor het besturingselement.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[CustomItem-Element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)

[CustomEntries-Element voor CustomControl voor GroupBy (indeling)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
