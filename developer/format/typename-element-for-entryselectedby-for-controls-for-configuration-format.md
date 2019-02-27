---
title: TypeName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30bb1382-8c6b-4371-82e6-baf427fa0781
caps.latest.revision: 6
ms.openlocfilehash: cec8c5d76bded321ec1d6a1cd0409d7c88863c03
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849817"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a>Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) TypeName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)

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
|[EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)