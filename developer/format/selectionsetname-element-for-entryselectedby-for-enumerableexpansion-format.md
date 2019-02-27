---
title: SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851532"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)

Hiermee geeft u de set met .NET-typen die door deze definitie zijn uitgebreid.

Configuratie van Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling) SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor EnumerableExpansion (indeling)](./entryselectedby-element-for-enumerableexpansion-format.md)|Hiermee definieert u de .NET-verzameling objecten die door deze definitie zijn uitgebreid.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de selectie is ingesteld.

## <a name="remarks"></a>Opmerkingen

Elke definitie moet opgeven voor een of meer namen, een selectie instellen of een selectievoorwaarde.

Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven. Bijvoorbeeld, als u wilt weergeven als een tabel en een lijst weergeven voor dezelfde set objecten maken. Zie voor meer informatie over het definiëren van selectiesets [definiëren ingesteld van objecten voor een weergave](./defining-selection-sets.md).

## <a name="see-also"></a>Zie ook

[Selectiesets definiëren](./defining-selection-sets.md)

[EntrySelectedBy-Element voor EnumerableExpansion (indeling)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
