---
title: Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3506188d32ce85ad6345dc0d0866dd789a1f293
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785401"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)

Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (Format) CustomControl element voor weer gave (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor het object CustomControl voor weer gave (Format) SelectionCondition voor EntrySelectedBy

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
|[SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op dat wordt geëvalueerd.

## <a name="remarks"></a>Opmerkingen

Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
