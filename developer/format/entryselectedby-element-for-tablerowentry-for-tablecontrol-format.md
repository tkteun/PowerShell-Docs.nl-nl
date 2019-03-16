---
title: EntrySelectedBy-Element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058756"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie van de tabelweergave of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor TableControl (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie voor het weergeven van tabel moet worden gebruikt.|
|[SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set van .NET-typen die gebruikmaken van de definitie van deze tabel weergeven.|
|[TypeName-Element voor EntrySelectedBy voor TableControl (indeling)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat gebruikmaakt van de definitie van deze tabel weergeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableRowEntry-Element voor TableControl (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|De gegevens die worden weergegeven in een rij van de tabel definieert.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van een tabel weergeven. Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.

Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde die moet aanwezig zijn voor de definitie moet worden gebruikt, zoals wanneer een object een bepaalde eigenschap heeft of die een bepaalde eigenschapwaarde of een script wordt geëvalueerd als `true`. Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `TableRowEntry` element dat wordt gebruikt om weer te geven van de eigenschappen van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[SelectionCondition-Element voor EntrySelectedBy voor TableControl (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry-Element voor TableControl (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TypeName-Element voor EntrySelectedBy voor TableControl (indeling)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
