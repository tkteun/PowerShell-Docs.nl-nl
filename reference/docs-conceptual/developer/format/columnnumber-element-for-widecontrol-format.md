---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ColumnNumber voor WideControl (opmaak)
description: Het element ColumnNumber voor WideControl (opmaak)
ms.openlocfilehash: 1ddbbfbd5b53065afcc6c1326d6abf1fadedc67b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648396"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Het element ColumnNumber voor WideControl (opmaak)

Hiermee geeft u het aantal kolommen op dat wordt weer gegeven in de brede weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (Format) ColumnNumber element voor WideControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ColumnNumber` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element WideControl (opmaak)](./widecontrol-element-format.md)|Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.|

## <a name="text-value"></a>Tekstwaarde

Geef een positief geheel getal op.

## <a name="remarks"></a>Opmerkingen

Bij het definiëren van een brede weer gave kunt u het `AutoSize` element of het `ColumnNumber` element toevoegen, maar u kunt niet beide toevoegen.

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Het element AutoSize voor WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Brede weergave (Basis)](./wide-view-basic.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
