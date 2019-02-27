---
title: TypeName-Element voor EntrySelectedBy voor CustomEntry voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848795"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>Het element TypeName voor EntrySelectedBy voor CustomEntry voor Weergave (opmaak)

Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van de weergave van het aangepaste besturingselement. Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor een definitie.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor EntrySelectedBy weergeven (indeling) Element voor CustomEntry voor weergave (indeling) TypeName Element voor EntrySelectedBy voor CustomEntry voor weergave (indeling)

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
|[EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definieert de .NET-typen die gebruikmaken van deze definitie van het aangepaste besturingselement weergeven of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

De weergavedefinitie voor elk aangepast besturingselement moet ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd hebben.

Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [het maken van aangepaste besturingselementen](./creating-custom-controls.md).

## <a name="see-also"></a>Zie ook

[Het maken van aangepaste besturingselementen](./creating-custom-controls.md)

[EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
