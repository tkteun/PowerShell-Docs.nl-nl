---
ms.date: 09/13/2016
ms.topic: reference
title: Het element WideEntries voor WideControl (opmaak)
description: Het element WideEntries voor WideControl (opmaak)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651240"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Het element WideEntries voor WideControl (opmaak)

Biedt de definities van de brede weer gave. In de brede weer gave moeten een of meer definities worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling)

## <a name="syntax"></a>Syntax

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideEntries` element beschreven. Er moet mini maal één onderliggend element worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)|Biedt een definitie van de brede weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element WideControl (opmaak)](./widecontrol-element-format.md)|Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.|

## <a name="remarks"></a>Opmerkingen

Een brede weer gave is een lijst indeling waarin één eigenschaps waarde of script waarde voor elk object wordt weer gegeven. Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `WideEntries` element dat één `WideEntry` element definieert. Het `WideEntry` element bevat één `WideItem` element waarmee wordt gedefinieerd welke eigenschap of script waarde wordt weer gegeven in de weer gave.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Het element WideControl (opmaak)](./widecontrol-element-format.md)

[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
