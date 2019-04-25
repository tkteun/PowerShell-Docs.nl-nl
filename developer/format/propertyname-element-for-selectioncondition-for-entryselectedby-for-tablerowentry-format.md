---
title: PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064659"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)

Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding in de tabel wordt gebruikt.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element voor TableRowEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling) PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Hiermee definieert u de voorwaarde die moet aanwezig zijn voor de vermelding in deze tabel moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de .NET-eigenschap.

## <a name="remarks"></a>Opmerkingen

De selectievoorwaarde moet ten minste één eigenschap name of een scriptblok opgeven, maar u kunt niet beide opgeven. Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
