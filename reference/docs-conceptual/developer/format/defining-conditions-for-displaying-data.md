---
title: Voor waarden definiëren voor het weer geven van gegevens | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355151"
---
# <a name="defining-conditions-for-displaying-data"></a>Voorwaarden voor het weergeven van gegevens definiëren

Wanneer u definieert welke gegevens door een weer gave of een besturings element worden weer gegeven, kunt u een voor waarde opgeven die moet bestaan voor de gegevens die moeten worden weer gegeven. De voor waarde kan worden geactiveerd door een specifieke eigenschap of wanneer een script of eigenschaps waarde wordt geëvalueerd als `true`. Wanneer aan de voor waarde voor de selectie wordt voldaan, wordt de definitie van de weer gave of het besturings element gebruikt.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Een selectie voorwaarde voor een definitie opgeven

Wanneer u een definitie voor een weer gave of besturings element maakt, wordt het element `EntrySelectedBy` gebruikt om op te geven welke objecten de definitie gebruiken of welke voor waarde moet bestaan om de definitie te gebruiken. De voor waarde wordt opgegeven door het element `SelectionCondition`.

In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een definitie van een tabel weergave. In dit voor beeld wordt de definitie alleen gebruikt wanneer het opgegeven script wordt geëvalueerd als `true`.

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

U kunt ook opgeven wanneer een item van een lijst weergave of besturings element wordt gebruikt door het element `ItemSelectionCondition` in de definitie van het item op te nemen. In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een item van een lijst weergave. In dit voor beeld wordt het item alleen gebruikt wanneer het script wordt geëvalueerd als `true`.

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

    - [SelectionCondition-element voor EntrySelectedBy voor TableControl (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionCondition-element voor EntrySelectedBy voor WideControl (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionCondition-element voor EntrySelectedBy voor CustomControl (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- In de volgende elementen worden de selectie voorwaarden voor algemene en de weer gave van besturings definities opgegeven:

    - [SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Het volgende element specificeert de selectie voorwaarde voor het uitbreiden van verzamelings objecten:

    - [SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Het volgende element specificeert de selectie voorwaarde voor het weer geven van een nieuwe groep gegevens:

    - [SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Met het volgende element wordt een item selectie voorwaarde voor een lijst weergave opgegeven:

    - [ItemSelectionCondition-element voor lijst item voor ListControl (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- De volgende elementen geven een item selectie voorwaarde voor besturings elementen aan:

    - [ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [ItemSelectionCondition-element voor ExpressionBinding voor CustomControl (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
