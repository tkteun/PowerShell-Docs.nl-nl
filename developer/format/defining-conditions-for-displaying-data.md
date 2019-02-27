---
title: Voorwaarden voor het weergeven van gegevens definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846562"
---
# <a name="defining-conditions-for-displaying-data"></a>Voorwaarden voor het weergeven van gegevens definiëren

Bij het definiëren van welke gegevens door een weergave of een besturingselement wordt weergegeven, kunt u een voorwaarde die moet aanwezig zijn voor de gegevens moet worden weergegeven. De voorwaarde kan worden geactiveerd door een bepaalde eigenschap, of wanneer een script of de waarde van de eigenschap resulteert in `true`. Wanneer de selectievoorwaarde wordt voldaan, wordt de definitie van de weergave of het besturingselement gebruikt.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Een Selectievoorwaarde voor een definitie op te geven

Bij het maken van een definitie voor een weergave of een besturingselement, de `EntrySelectedBy` element wordt gebruikt om op te geven welke objecten de definitie wordt gebruikt of welke voorwaarde moet bestaan voor de definitie moet worden gebruikt. De voorwaarde wordt opgegeven door de `SelectionCondition` element.

In het volgende voorbeeld wordt een selectievoorwaarde opgegeven voor een definitie van een tabelweergave. In dit voorbeeld wordt de definitie wordt alleen gebruikt als het opgegeven script wordt geëvalueerd naar `true`.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

Er is geen limiet voor het aantal selectie voorwaarden die u voor een definitie van een weergave of een besturingselement opgeven kunt. De enige vereisten zijn als volgt:

- De selectievoorwaarde moet één naam van de eigenschap of een script voor het activeren van de voorwaarde opgeven, maar u kunt niet beide opgeven.

- De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.

## <a name="specifying-a-selection-condition-for-an-item"></a>Een Selectievoorwaarde van een Item op te geven

U kunt ook opgeven wanneer een item van een lijst of een besturingselement wordt gebruikt door de `ItemSelectionCondition` -element in de definitie van het item. In het volgende voorbeeld wordt een selectievoorwaarde opgegeven voor een item van een lijst weergeven. In dit voorbeeld wordt het item wordt alleen gebruikt als het script wordt geëvalueerd naar `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

U kunt slechts één selectievoorwaarde voor een item opgeven. En de voorwaarde moet één naam van de eigenschap of een script voor het activeren van de voorwaarde opgeven, maar niet beide opgeven.

## <a name="xml-elements"></a>XML-elementen

 De volgende XML-elementen worden gebruikt om de selectievoorwaarde van een te maken.

- De volgende elementen opgeven selectie voorwaarden voor weergavedefinities:

    - [SelectionCondition-Element voor EntrySelectedBy voor TableControl (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionCondition-Element voor EntrySelectedBy voor WideControl (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionCondition-Element voor EntrySelectedBy voor CustomControl (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- De volgende elementen opgeven selectie voorwaarden voor algemene en weergave definities beheren:

    - [SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Het volgende element Hiermee geeft u de selectievoorwaarde voor het uitbreiden van verzameling objecten:

    - [SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Het volgende element Hiermee geeft u de selectievoorwaarde voor het weergeven van een nieuwe groep van gegevens:

    - [SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Het volgende element Hiermee geeft u de voorwaarde van een item selecteren voor een lijst weergeven:

    - [ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- De volgende elementen opgeven een voorwaarde voor de selectie van item voor besturingselementen:

    - [ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [ItemSelectionCondition-Element voor ExpressionBinding voor CustomControl (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
