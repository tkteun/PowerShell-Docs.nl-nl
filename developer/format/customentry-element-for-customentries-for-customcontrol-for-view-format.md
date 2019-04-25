---
title: CustomEntry-Element voor CustomEntries voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066444"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)

Bevat een definitie van de weergave van het aangepaste besturingselement.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomEntry` element. U moet de items worden weergegeven door de definitie opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de weergave van het aangepaste besturingselement of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|
|[CustomItem-Element voor CustomEntry voor weergave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u een besturingselement voor de definitie van het aangepaste besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntries-Element voor CustomControl voor weergave (indeling)](./customentries-element-for-customcontrol-for-view-format.md)|Bevat de definities van de weergave van het aangepaste besturingselement. De weergave van het aangepaste besturingselement moet een of meer netwerkdefinities opgeven.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen slechts één definitie is vereist voor elke weergave aangepast besturingselement, maar het is mogelijk dat meerdere definities als u wilt de dezelfde weergave gebruiken om verschillende .NET-objecten weer te geven. In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.

## <a name="see-also"></a>Zie ook

[CustomControl-Element voor weergave (indeling)](./customcontrol-element-for-view-format.md)

[CustomItem-Element voor CustomEntry voor weergave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
