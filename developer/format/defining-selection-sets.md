---
title: Selectiesets definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066308"
---
# <a name="defining-selection-sets"></a>Selectiereeksen definiëren

Bij het maken van meerdere weergaven en besturingselementen, kunt u sets van objecten die worden aangeduid als selectiesets definiëren. Een selectie kunt u de objecten definiëren die één keer zonder herhaaldelijk definiëren voor elke weergave of het besturingselement. Selectiesets worden meestal gebruikt wanneer u een set van gerelateerde .NET-objecten. Bijvoorbeeld, de `FileSystem` opmaak-bestand (FileSystem.format.ps1xml) definieert een van selectieset-systeem met de bestandstypen die gebruikmaken van verschillende weergaven.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Waar selectiesets zijn gedefinieerd en referentie

U definiëren selectiesets als onderdeel van de algemene gegevens die kunnen worden gebruikt door alle weergaven en besturingselementen die zijn gedefinieerd in het bestand met opmaak. Het volgende voorbeeld ziet drie selectiesets definiëren.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

U kunt verwijzen naar een selectie wordt ingesteld op de volgende manieren:

- Elke weergave bevat een `ViewSelectedBy` element waarmee wordt gedefinieerd welke objecten worden weergegeven met behulp van de weergave. De `ViewSelectedBy` element heeft een `SelectionSetName` onderliggende element dat Hiermee geeft u de selectie instellen dat de definities van het gebruik van de weergave. Er is geen beperking voor het aantal opgegeven selecteren waarnaar u vanuit een weergave verwijzen kunt.

- In elke definitie van een weergave of een besturingselement, de `EntrySelectedBy` element wordt gedefinieerd welke objecten worden weergegeven met behulp van deze definitie. Een weergave of een besturingselement heeft meestal slechts één definitie, zodat de objecten worden gedefinieerd door de `ViewSelectedBy` element. De `EntrySelectedBy` -element van de definitie is een `SelectionSetName` onderliggende element dat Hiermee geeft u de selectie. Als u de selectie instellen voor een definitie opgeeft, u niet opgeven een van de andere onderliggende elementen van de `EntrySelectedBy` element.

- In elke definitie van een weergave of een besturingselement, de `SelectionCondition` element kan worden gebruikt om op te geven van een voorwaarde voor wanneer de definitie wordt gebruikt. De `SelectionCondition` element heeft een `SelectionSetName` onderliggende element dat Hiermee geeft u de selectie ingesteld die wordt geactiveerd voor de voorwaarde. De voorwaarde wordt geactiveerd wanneer een van de objecten die zijn gedefinieerd in de selectie worden weergegeven. Zie voor meer informatie over het instellen van deze voorwaarden [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Voorbeeld van de selectie van instellen

Het volgende voorbeeld ziet u een selectie instellen die rechtstreeks vanuit de `FileSystem` opmaak bestand dat is opgegeven door de Windows PowerShell. Zie voor meer informatie over andere Windows PowerShell bestanden opmaak [bestanden van Windows PowerShell-opmaak](./powershell-formatting-files.md).

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

De voorgaande selectieset wordt verwezen in de `ViewSelectedBy` element van een tabelweergave.

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a>XML-elementen

 Er is geen limiet voor het aantal opgegeven selectie die u kunt definiëren. De volgende XML-elementen worden gebruikt voor het maken van een verzameling selecteren.

- De [SelectionSets](./selectionsets-element-format.md) element wordt gedefinieerd voor de sets met .NET-objecten waarnaar wordt verwezen door de weergaven en besturingselementen van het bestand opmaak.

- De [SelectionSet](./selectionset-element-format.md) element wordt gedefinieerd voor één set met .NET-objecten.

- De [naam](./name-element-for-selectionset-format.md) element Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de selectieset.

- De [typen](./types-element-for-selectionset-format.md) element Hiermee geeft u de .NET-typen van de objecten van de selectie is ingesteld. (In de opmaak van bestanden, objecten zijn opgegeven door hun .NET-type.)

 De volgende XML-elementen worden gebruikt om op te geven van een selectieset.

- Het volgende element Hiermee geeft u de selectie is ingesteld op in de definities van de weergave gebruiken:

    - [SelectionSetName-Element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md)

    - [SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- De volgende elementen geeft u de selectieset die worden gebruikt door de definitie van een enkelvoudige weergave:

    - [SelectionSetName-Element voor EntrySelectedBy voor ListControl (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-Element voor EntrySelectedBy voor WideControl (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionSetName-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- De volgende elementen selectie opgeven die worden gebruikt door de gemeenschappelijke en definities van besturingselement weer te geven:

    - [SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- De volgende elementen geeft u de selectieset die wordt gebruikt bij het definiëren van welk object om uit te vouwen:

    - [SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- De selectieset die worden gebruikt door de selectie voorwaarden opgeven die de volgende elementen.

    - [SelectionSetName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [SelectionSetName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [SelectionSetName-Element voor SelectionCondition voor GroupBy (indeling)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Zie ook

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Naam](./name-element-for-selectionset-format.md)

[Types](./types-element-for-selectionset-format.md)

[PowerShell-bestanden voor opmaak](./powershell-formatting-files.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[Schrijven van een PowerShell-opmaak en typen bestand](./writing-a-powershell-formatting-file.md)
