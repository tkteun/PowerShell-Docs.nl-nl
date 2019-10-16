---
title: SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355774"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionSetName element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSetName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekst waarde

Geef de naam op van de selectieset.

## <a name="remarks"></a>Opmerkingen

Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.

## <a name="see-also"></a>Zie ook

[EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
