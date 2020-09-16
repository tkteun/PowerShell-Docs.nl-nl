---
title: Element label voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783633"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Het element Label voor ListItem voor ListControl (opmaak)

Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) List item voor ListControl (Format) element Entry List voor ListControl (Format) List items voor List entry voor ListControl element (Format) lijst item-element voor list items voor ListControl (Format) label-element (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ListItem voor ListItems voor ListControl (opmaak)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef het label op dat links van de eigenschap of script waarde moet worden weer gegeven.

## <a name="remarks"></a>Opmerkingen

Als er geen label is opgegeven, wordt de naam van de eigenschap of het script weer gegeven. Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van labels in een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een label aan een rij toevoegt.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
