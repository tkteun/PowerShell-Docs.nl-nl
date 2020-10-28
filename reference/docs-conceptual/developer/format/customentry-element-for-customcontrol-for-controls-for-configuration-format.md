---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)
description: Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 3967be86a1d6c12c7215ef19d50bac9fafd5ad6d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648284"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)

Biedt een definitie van het algemene besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling)

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
|[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element.|
|[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntries-element voor CustomControl voor configuratie (indeling)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Biedt de definities van het algemene besturings element.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen is slechts één definitie vereist voor elk algemeen aangepast besturings element, maar het is mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[CustomEntries-element voor CustomControl voor configuratie (indeling)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
