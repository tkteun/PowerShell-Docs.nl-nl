---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)
description: Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651602"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)

Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) EntrySelectedBy element voor CustomEntry voor weer gave (indeling)

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
|[SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.

Met de selectie voorwaarde kan een selectieset of .NET-type worden opgegeven, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
