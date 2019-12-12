---
title: Selectie sets definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359009"
---
# <a name="defining-selection-sets"></a>Selectiereeksen definiëren

Wanneer u meerdere weer gaven en besturings elementen maakt, kunt u sets van objecten definiëren die worden aangeduid als selectie sets. Met een selectieset kunt u de objecten één keer definiëren, zonder dat u ze herhaaldelijk hoeft te definiëren voor elke weer gave of elk besturings element. Selectie sets worden meestal gebruikt wanneer u een set gerelateerde .NET-objecten hebt. Bijvoorbeeld, het `FileSystem` opmaak bestand (File System. Format. ps1xml) definieert een selectie reeks van de bestandssysteem typen die door verschillende weer gaven worden gebruikt.

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

- Elke weer gave heeft een `ViewSelectedBy`-element waarmee wordt gedefinieerd welke objecten worden weer gegeven met behulp van de weer gave. Het `ViewSelectedBy`-element heeft een `SelectionSetName` onderliggend element waarmee de selectie reeks wordt opgegeven die alle definities van de weer gave gebruiken. Er is geen beperking voor het aantal selectie sets waarnaar u kunt verwijzen vanuit een weer gave.

- In elke definitie van een weer gave of besturings element definieert het `EntrySelectedBy`-element welke objecten worden weer gegeven met behulp van de definitie. Normaal gesp roken bevat een weer gave of besturings element slechts één definitie, zodat de objecten worden gedefinieerd door het `ViewSelectedBy` element. Het `EntrySelectedBy` element van de definitie heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven. Als u de selectie set voor een definitie opgeeft, kunt u geen van de andere onderliggende elementen van het `EntrySelectedBy`-element opgeven.

- In elke definitie van een weer gave of besturings element kan het `SelectionCondition`-element worden gebruikt om een voor waarde op te geven voor het gebruik van de definitie. Het `SelectionCondition`-element heeft een `SelectionSetName` onderliggend element dat de selectieset specificeert die de voor waarde activeert. De voor waarde wordt geactiveerd wanneer een van de objecten die in de selectieset zijn gedefinieerd, worden weer gegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het instellen van deze voor waarden.

## <a name="selection-set-example"></a>Voor beeld van selectie sets

In het volgende voor beeld ziet u een selectie reeks die rechtstreeks afkomstig is uit het `FileSystem` opmaak bestand dat wordt meegeleverd met Windows Power shell. Zie [Windows Power shell-indelings bestanden](./powershell-formatting-files.md)voor meer informatie over andere Windows Power shell-indelings bestanden.

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

Er wordt naar de vorige selectieset verwezen in het `ViewSelectedBy`-element van een tabel weergave.

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

    - [SelectionSetName-element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md)

    - [SelectionSetName-element voor EntrySelectedBy voor GroupBy (indeling)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt door een enkele weergave definitie:

    - [SelectionSetName-element voor EntrySelectedBy voor ListControl (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionSetName-element voor EntrySelectedBy voor TableControl (indeling)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-element voor EntrySelectedBy voor WideControl (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionSetName-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt door algemene en besturings definities weer geven:

    - [SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt wanneer u definieert welk object moet worden uitgebreid:

    - [SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- De volgende elementen geven de selectieset op die wordt gebruikt voor de selectie omstandigheden.

    - [SelectionSetName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [SelectionSetName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [SelectionSetName-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [SelectionSetName-element voor SelectionCondition voor GroupBy (indeling)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Zie ook

[SelectionSets](./selectionsets-element-format.md)

[Selectieset](./selectionset-element-format.md)

[Name](./name-element-for-selectionset-format.md)

[Dergelijke](./types-element-for-selectionset-format.md)

[Power shell-indelings bestanden](./powershell-formatting-files.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Een Power shell-indeling en-typen bestand schrijven](./writing-a-powershell-formatting-file.md)
