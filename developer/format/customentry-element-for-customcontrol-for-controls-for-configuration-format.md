---
title: CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849474"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)

Bevat een definitie van de algemene besturingselementen. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)

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
|[EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de algemene controle of de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.|
|[CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntries-Element voor CustomControl voor configuratie (-indeling)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Bevat de definities van de algemene besturingselementen.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen slechts één definitie is vereist voor elke algemene aangepast besturingselement, maar het is mogelijk dat meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven. In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.

## <a name="see-also"></a>Zie ook

[CustomEntries-Element voor CustomControl voor configuratie (-indeling)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
