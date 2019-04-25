---
title: TypeName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083940"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor besturingselementen voor het besturingselement Configuratie (-indeling) CustomEntry-Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor Configuratie (-indeling) TypeName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` Element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor configuratie (-indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor configuratie (-indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
