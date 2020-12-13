---
ms.date: 09/13/2016
ms.topic: reference
title: Voorwaarden voor het weergeven van gegevens definiëren
description: Voorwaarden voor het weergeven van gegevens definiëren
ms.openlocfilehash: 9a8b7a618da8c64de978c13b527435a2d7793677
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660321"
---
# <a name="defining-conditions-for-displaying-data"></a>Voorwaarden voor het weergeven van gegevens definiëren

Wanneer u definieert welke gegevens door een weer gave of een besturings element worden weer gegeven, kunt u een voor waarde opgeven die moet bestaan voor de gegevens die moeten worden weer gegeven. De voor waarde kan worden geactiveerd door een specifieke eigenschap of wanneer de waarde van een script of eigenschap wordt geëvalueerd `true` . Wanneer aan de voor waarde voor de selectie wordt voldaan, wordt de definitie van de weer gave of het besturings element gebruikt.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Een selectie voorwaarde voor een definitie opgeven

Wanneer u een definitie voor een weer gave of besturings element maakt, `EntrySelectedBy` wordt het element gebruikt om op te geven welke objecten de definitie zullen gebruiken, of welke voor waarde moet bestaan om de definitie te gebruiken. De voor waarde wordt opgegeven door het `SelectionCondition` element.

In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een definitie van een tabel weergave. In dit voor beeld wordt de definitie alleen gebruikt wanneer het opgegeven script wordt geëvalueerd `true` .

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

Er is geen limiet voor het aantal selectie omstandigheden dat u kunt opgeven voor een definitie van een weer gave of besturings element. De enige vereisten zijn de volgende:

- De selectie voorwaarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

## <a name="specifying-a-selection-condition-for-an-item"></a>Een selectie voorwaarde voor een item opgeven

U kunt ook opgeven wanneer een item van een lijst weergave of besturings element wordt gebruikt door het `ItemSelectionCondition` element op te nemen in de definitie van het item. In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een item van een lijst weergave. In dit voor beeld wordt het item alleen gebruikt wanneer het script wordt geëvalueerd `true` .

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

U kunt slechts één selectie voorwaarde voor een item opgeven. En de voor waarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.

## <a name="xml-elements"></a>XML-elementen

 De volgende XML-elementen worden gebruikt om een selectie voorwaarde te maken.

- In de volgende elementen worden de selectie voorwaarden voor weergave definities opgegeven:

  - [Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- In de volgende elementen worden de selectie voorwaarden voor algemene en de weer gave van besturings definities opgegeven:

  - [Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Het volgende element specificeert de selectie voorwaarde voor het uitbreiden van verzamelings objecten:

  - [Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Het volgende element specificeert de selectie voorwaarde voor het weer geven van een nieuwe groep gegevens:

  - [Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Met het volgende element wordt een item selectie voorwaarde voor een lijst weergave opgegeven:

  - [Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- De volgende elementen geven een item selectie voorwaarde voor besturings elementen aan:

  - [Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Zie ook

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
