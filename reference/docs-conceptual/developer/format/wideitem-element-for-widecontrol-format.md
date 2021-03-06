---
ms.date: 09/13/2016
ms.topic: reference
title: Het element WideItem voor WideControl (opmaak)
description: Het element WideItem voor WideControl (opmaak)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647798"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Het element WideItem voor WideControl (opmaak)

Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling)

## <a name="syntax"></a>Syntax

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideItem` element beschreven. Het `FormatString` element is optioneel. U moet echter een or- `PropertyName` `ScriptBlock` element opgeven, maar u kunt niet beide opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element FormatString voor WideItem voor WideControl (opmaak)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Optioneel element.<br /><br /> Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.|
|[Het element PropertyName voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.|
|[Script block-element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)|Biedt een definitie van de brede weer gave.|

## <a name="remarks"></a>Opmerkingen

Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `WideEntry` element dat ????n `WideItem` element definieert. Het `WideItem` element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de weer gave.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Het element FormatString voor WideItem voor WideControl (opmaak)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Het element PropertyName voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Script block-element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
