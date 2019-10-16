---
title: CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355235"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)

Biedt een definitie van de aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomEntry` beschreven. U moet de items opgeven die worden weer gegeven door de definitie.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de aangepaste beheer weergave of de voor waarde die voor deze definitie moet worden gebruikt.|
|[CustomItem-element voor CustomEntry voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u een besturings element voor de aangepaste besturings element definitie.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntries-element voor CustomControl voor weer gave (indeling)](./customentries-element-for-customcontrol-for-view-format.md)|Biedt de definities van de aangepaste beheer weergave. In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen is er slechts één definitie vereist voor elke aangepaste controle weergave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[CustomControl-element voor weer gave (indeling)](./customcontrol-element-for-view-format.md)

[CustomItem-element voor CustomEntry voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
