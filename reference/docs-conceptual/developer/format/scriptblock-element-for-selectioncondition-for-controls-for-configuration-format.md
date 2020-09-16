---
title: Script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24584aacd7869abd3dcfc6ff546e6dea4c2c04fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785435"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries-element voor het element CustomControl voor configuratie (Format) CustomEntry CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (Format) script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de algemene definitie van het besturings element.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
