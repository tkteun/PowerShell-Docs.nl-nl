---
title: CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a13e83ec941bed80eaab02e40131054432fcce00
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785877"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)

Biedt een definitie van de aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomEntry` element beschreven. U moet de items opgeven die worden weer gegeven door de definitie.

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
|[Het element CustomEntries voor CustomControl voor Weergave (opmaak)](./customentries-element-for-customcontrol-for-view-format.md)|Biedt de definities van de aangepaste beheer weergave. In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen is er slechts één definitie vereist voor elke aangepaste controle weergave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[Het element CustomControl voor Weergave (opmaak)](./customcontrol-element-for-view-format.md)

[CustomItem-element voor CustomEntry voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
