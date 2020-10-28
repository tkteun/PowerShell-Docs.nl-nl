---
ms.date: 09/13/2016
ms.topic: reference
title: Selectiereeksen definiëren
description: Selectiereeksen definiëren
ms.openlocfilehash: d709a368a45623d56fdbf4e98a11a5e5f8a193fa
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648256"
---
# <a name="defining-selection-sets"></a>Selectiereeksen definiëren

Wanneer u meerdere weer gaven en besturings elementen maakt, kunt u sets van objecten definiëren die worden aangeduid als selectie sets. Met een selectieset kunt u de objecten één keer definiëren, zonder dat u ze herhaaldelijk hoeft te definiëren voor elke weer gave of elk besturings element. Selectie sets worden meestal gebruikt wanneer u een set gerelateerde .NET-objecten hebt. Bijvoorbeeld, het `FileSystem` Opmaak bestand (FileSystem.format.ps1XML) definieert een selectie reeks van de bestandssysteem typen die door verschillende weer gaven worden gebruikt.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Waar worden selectie sets gedefinieerd en waarnaar wordt verwezen

U definieert selectie sets als onderdeel van de algemene gegevens die kunnen worden gebruikt door alle weer gaven en besturings elementen die in het opmaak bestand zijn gedefinieerd. In het volgende voor beeld ziet u hoe u drie selectie sets definieert.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

U kunt op de volgende manieren naar een selectie sets verwijzen:

- Elke weer gave bevat een `ViewSelectedBy` element dat bepaalt welke objecten worden weer gegeven met behulp van de weer gave. Het `ViewSelectedBy` element heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven die alle definities van de weer gave gebruiken. Er is geen beperking voor het aantal selectie sets waarnaar u kunt verwijzen vanuit een weer gave.

- In elke definitie van een weer gave of besturings element `EntrySelectedBy` definieert het element welke objecten worden weer gegeven met behulp van de definitie. Normaal gesp roken bevat een weer gave of besturings element slechts één definitie, zodat de objecten door het element worden gedefinieerd `ViewSelectedBy` . Het `EntrySelectedBy` element van de definitie heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven. Als u de selectie sets voor een definitie opgeeft, kunt u geen van de onderliggende elementen van het element opgeven `EntrySelectedBy` .

- In elke definitie van een weer gave of besturings element `SelectionCondition` kan het element worden gebruikt om een voor waarde op te geven voor het gebruik van de definitie. Het `SelectionCondition` element heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven waarmee de voor waarde wordt geactiveerd. De voor waarde wordt geactiveerd wanneer een van de objecten die in de selectieset zijn gedefinieerd, worden weer gegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het instellen van deze voor waarden.

## <a name="selection-set-example"></a>Voor beeld van selectie sets

In het volgende voor beeld ziet u een selectie reeks die rechtstreeks afkomstig is uit het `FileSystem` Opmaak bestand dat wordt meegeleverd met Windows Power shell. Zie [Windows Power shell-indelings bestanden](./powershell-formatting-files.md)voor meer informatie over andere Windows Power shell-indelings bestanden.

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

Er wordt naar de vorige selectieset verwezen in het `ViewSelectedBy` element van een tabel weergave.

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

 Er is geen limiet voor het aantal selectie sets dat u kunt definiëren. De volgende XML-elementen worden gebruikt voor het maken van een selectieset.

- Het [SelectionSets](./selectionsets-element-format.md) -element definieert de sets .net-objecten waarnaar wordt verwezen door de weer gaven en besturings elementen van het opmaak bestand.

- Met het element [selectionset](./selectionset-element-format.md) wordt één set .net-objecten gedefinieerd.

- Het element [name](./name-element-for-selectionset-format.md) bevat de naam die wordt gebruikt om te verwijzen naar de selectieset.

- Het element [types](./types-element-for-selectionset-format.md) specificeert de .net-typen van de objecten van de selectieset. (Bij het format teren van bestanden worden objecten door hun .NET-type opgegeven.)

 De volgende XML-elementen worden gebruikt om een selectieset op te geven.

- Met het volgende element wordt de selectie ingesteld die moet worden gebruikt in alle definities van de weer gave:

  - [Het element SelectionSetName voor ViewSelectedBy (opmaak)](./selectionsetname-element-for-viewselectedby-format.md)

  - [Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt door een enkele weergave definitie:

  - [Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt door algemene en besturings definities weer geven:

  - [Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt wanneer u definieert welk object moet worden uitgebreid:

  - [Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt voor de selectie omstandigheden.

  - [Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Zie ook

[SelectionSets](./selectionsets-element-format.md)

[Selectieset](./selectionset-element-format.md)

[Naam](./name-element-for-selectionset-format.md)

[Typen](./types-element-for-selectionset-format.md)

[PowerShell-opmaakbestanden](./powershell-formatting-files.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Een Power shell-indeling en-typen bestand schrijven](./writing-a-powershell-formatting-file.md)
