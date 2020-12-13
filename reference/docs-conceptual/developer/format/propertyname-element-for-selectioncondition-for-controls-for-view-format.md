---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)
description: Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 7783e5a9b7f8ec3d3077d87778e9f77ffe858a7f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665869"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a>Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor de weer gave (Format) CustomEntries-element Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor de weer gave (indeling) eigenschaps element voor SelectionCondition voor besturings elementen

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef de .NET-eigenschaps naam op.

## <a name="remarks"></a>Opmerkingen

De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
