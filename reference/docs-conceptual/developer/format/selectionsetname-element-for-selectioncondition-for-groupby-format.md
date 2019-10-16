---
title: SelectionSetName-element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353723"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)

Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (Format) EntrySelectedBy voor CustomEntry voor het element GroupBy (Format) SelectionCondition voor EntrySelectedBy voor het element GroupBy (Format) SelectionSetName voor SelectionCondition voor GroupBy (Format)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekst waarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Selectie sets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een wille keurige weer gave waarin het opmaak bestand is gedefinieerd. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken en verwijzen van selectie sets.

Als dit element is opgegeven, kunt u het element [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) niet opgeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[TypeName-element voor SelectionCondition voor GroupBy (indeling)](./typename-element-for-selectioncondition-for-groupby-format.md)

[SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Selectie sets definiëren](./defining-selection-sets.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
