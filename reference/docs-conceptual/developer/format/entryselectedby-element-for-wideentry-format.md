---
title: EntrySelectedBy-element voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354752"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Het element EntrySelectedBy voor WideEntry (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie van de brede weer gave of de voor waarde die voor deze definitie moet worden gebruikt.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy-element voor WideEntry (indeling)

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
|[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze brede weergave definitie.|
|[SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze brede weergave definitie.|
|[TypeName-element voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze brede weergave definitie.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)|Biedt een definitie van de brede weer gave.|

## <a name="remarks"></a>Opmerkingen

U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een brede weergave definitie. Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of script waarde resulteert in `true`. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)

[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-element voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Een brede weer gave maken](./creating-a-wide-view.md)

[Voor waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
