---
title: SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846877"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)

Hiermee geeft u dat een set met .NET typen het gebruik van deze vermelding van de tabelweergave. Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy-Element (indeling) SelectionSetName-Element voor EntrySelectedBy voor TableRowEntry (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de selectie is ingesteld.

## <a name="remarks"></a>Opmerkingen

Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven. Bijvoorbeeld, als u wilt weergeven als een tabel en een lijst weergeven voor dezelfde set objecten maken. Zie voor meer informatie over het definiëren van selectiesets [van objecten voor een weergave definiëren ingesteld](./defining-selection-sets.md).

Als u een selectie instellen voor een vermelding opgeeft, kunt u de typenaam van een kan niet opgeven. Zie voor meer informatie over het opgeven van een .NET-type [TypeName-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="see-also"></a>Zie ook

[EntrySelectedBy-Element (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Sets van objecten voor een weergave definiëren](./defining-selection-sets.md)

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
