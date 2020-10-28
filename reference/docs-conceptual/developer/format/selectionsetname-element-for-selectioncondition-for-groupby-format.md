---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654992"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)

Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) SelectionCondition voor EntrySelectedBy voor GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.

Als dit element is opgegeven, kunt u het element [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) niet opgeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element TypeName voor SelectionCondition voor GroupBy (opmaak)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
