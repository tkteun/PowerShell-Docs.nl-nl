---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor WideItem voor WideControl (opmaak)
description: Het element PropertyName voor WideItem voor WideControl (opmaak)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665614"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>Het element PropertyName voor WideItem voor WideControl (opmaak)

Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling) eigenschap Naam element voor WideItem (indeling)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de brede weer gave.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.

## <a name="remarks"></a>Opmerkingen

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een breed overzicht waarin de waarde van de eigenschap proces naam van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) wordt weer gegeven.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Zie ook

[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
