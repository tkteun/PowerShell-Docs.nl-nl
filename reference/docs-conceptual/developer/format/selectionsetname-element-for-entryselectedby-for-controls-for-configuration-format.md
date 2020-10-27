---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: b775aa8a3184aa3ebcbda17a8e3191c69d67a700
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645721"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (Format) EntrySelectedBy-element voor SelectionSetName voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

## <a name="see-also"></a>Zie ook

[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
