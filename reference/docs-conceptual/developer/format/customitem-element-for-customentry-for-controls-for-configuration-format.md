---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
description: Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 06c399e982b6ac0fba9c11e20c468fe8bef6f694
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666770"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (Format) CustomEntry-element voor het voor het configureren van configuratie (Format) CustomItem-element voor besturings elementen

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven. Zie Opmerkingen voor meer informatie.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|
|[Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.|
|[Het element NewLine voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.|
|[Het element Tekst voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Biedt een definitie van het besturings element.|

## <a name="remarks"></a>Opmerkingen

Wanneer u de onderliggende elementen van het `CustomItem` element opgeeft, houdt u het volgende in acht:

- De onderliggende elementen moeten worden toegevoegd in de volgende volg orde:,, en `ExpressionBinding` `NewLine` `Text` `Frame` .

- Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.

- In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding` elementen dat u kunt gebruiken.

## <a name="see-also"></a>Zie ook

[Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Het element NewLine voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Het element Tekst voor CustomItem voor Besturingselementen voor Configuratie (opmaak)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
