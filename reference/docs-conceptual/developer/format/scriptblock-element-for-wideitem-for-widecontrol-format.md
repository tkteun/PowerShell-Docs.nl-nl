---
title: Script block-element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787594"
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
