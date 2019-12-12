---
title: EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358998"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling) EntrySelectedBy Element voor CustomEntry voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.|
|[SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van de beheer weergave.|
|[TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de controle weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Hiermee worden de besturings elementen gedefinieerd die worden gebruikt door specifieke .NET-objecten.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde voor een vermelding opgeven. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die moet bestaan voor het gebruik van de vermelding, zoals wanneer een object een specifieke eigenschap heeft of wanneer een specifieke eigenschaps waarde of script `true`. Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

Zie [aangepaste besturings elementen weer geven](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[TypeName-element voor EntrySelectedBy voor CustomEntry (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Aangepaste besturings elementen weer geven](./creating-custom-controls.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
