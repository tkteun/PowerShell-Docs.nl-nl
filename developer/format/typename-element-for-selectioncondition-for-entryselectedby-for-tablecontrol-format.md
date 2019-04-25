---
title: TypeName-Element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083838"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Het element TypeName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)

Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de voorwaarde wordt voldaan en wordt een rij in de tabel wordt gebruikt.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element voor TableRowEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling) TypeName Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)

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
|[SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Hiermee definieert u de voorwaarde die moet aanwezig zijn voor een rij in deze tabel moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven. Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
