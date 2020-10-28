---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ListItem voor ListControl (opmaak)
description: Het element PropertyName voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665971"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>Het element PropertyName voor ListItem voor ListControl (opmaak)

Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de lijst.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) ListControl element (indeling) (Format) List item (Format) element Entry element (indeling) List items element (Format) lijst item element (indeling) eigenschap Naam element voor lijst item (indeling)

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
|[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de rij van de lijst weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -element niet opgeven.

Naast het weer geven van de eigenschaps waarde, kunt u ook een label opgeven voor de waarde of een opmaak teken reeks die kan worden gebruikt om de weer gave van de waarde te wijzigen. Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het opgeven van gegevens in een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u het label en de eigenschap opgeeft waarvan de waarde wordt weer gegeven.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[Het element ScriptBlock voor ListItem voor ListControl (opmaak)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Een lijstweergave maken](./creating-a-list-view.md)

[Lijst item-element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
