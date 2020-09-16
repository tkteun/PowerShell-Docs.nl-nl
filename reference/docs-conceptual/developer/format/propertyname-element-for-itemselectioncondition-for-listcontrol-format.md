---
title: PropertyName-element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780862"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de weer gave gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) (Format) List item (Format) element-element (indeling) List items element voor ListControl (Format) voor List entry voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) ItemSelectionCondition-element voor ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `PropertyName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.

## <a name="see-also"></a>Zie ook

[Script block-element voor ItemSelectionCondition voor ListIControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
