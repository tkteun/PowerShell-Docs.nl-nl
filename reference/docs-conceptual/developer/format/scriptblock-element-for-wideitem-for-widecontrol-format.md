---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor WideItem voor WideControl (opmaak)
description: Het element ScriptBlock voor WideItem voor WideControl (opmaak)
ms.openlocfilehash: 68e47926e5e6b846c8a0a3dbc16d1f0d59f11dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659871"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Het element ScriptBlock voor WideItem voor WideControl (opmaak)

Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling) script block element (indeling)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md)|Hiermee wordt de eigenschap of het script blok gedefinieerd waarvan de waarde wordt weer gegeven in de brede weer gave.|

## <a name="text-value"></a>Tekstwaarde

Geef het script op waarvan de waarde wordt weer gegeven.

## <a name="remarks"></a>Opmerkingen

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `WideItem` element dat een script definieert waarvan de waarde in de weer gave wordt weer gegeven.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Zie ook

[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
