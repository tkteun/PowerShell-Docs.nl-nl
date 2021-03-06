---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
description: Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 85d095b9b0c25b68b2353bce56b85333aff91b98
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652246"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie frame-element voor CustomItem voor besturings elementen voor configuratie van het type configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomItem Element`|Vereist element|
|[Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.|
|[Het element FirstLineIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.|
|[Het element LeftIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.|
|[Het element RightIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen in hetzelfde element niet opgeven `Frame` .

## <a name="see-also"></a>Zie ook

[Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Het element FirstLineIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Het element LeftIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Het element RightIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
