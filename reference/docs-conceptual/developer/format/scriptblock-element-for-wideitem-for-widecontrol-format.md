---
title: Script block-element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353842"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Het element ScriptBlock voor WideItem voor WideControl (opmaak)

Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling) script block element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.

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

In dit voor beeld ziet u een `WideItem`-element dat een script definieert waarvan de waarde in de weer gave wordt weer gegeven.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Zie ook

[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md)

[Een brede weer gave maken](./creating-a-wide-view.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
