---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 5e4368a9546307c5ff223ae42ecaa1d2872bc587
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665954"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (Format) CustomEntry-element voor CustomControl voor besturings elementen voor de configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor de configuratie (Format) eigenschap naam van SelectionCondition for EntrySelectedBy voor List entry (Format)

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
|[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef de .NET-eigenschaps naam op.

## <a name="remarks"></a>Opmerkingen

De selectie voorwaarde moet ten minste één eigenschaps naam of een script opgeven, maar kan niet beide opgeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
