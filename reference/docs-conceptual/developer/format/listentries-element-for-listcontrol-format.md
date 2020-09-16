---
title: Element List entries voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0fe07e739c2d2fec153599ec6c0c0b3ecc14df18
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785707"
---
# <a name="listentries-element-for-listcontrol-format"></a>Het element ListEntries voor ListControl (opmaak)

Biedt de definities van de lijst weergave. In de lijst weergave moeten een of meer definities worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) ListControl element (indeling) element (indeling)

## <a name="syntax"></a>Syntax

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListEntries` element beschreven. Er moet mini maal één onderliggend element worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element List entry (indeling)](./listentry-element-for-listcontrol-format.md)|Geeft een definitie van de lijst weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ListControl (opmaak)](./listcontrol-element-format.md)|Hiermee definieert u een lijst indeling voor de weer gave.|

## <a name="remarks"></a>Opmerkingen

Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over lijst weergaven.

## <a name="example"></a>Voorbeeld

In dit voor beeld worden de XML-elementen weer gegeven die de lijst weergave definiëren voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[Het element ListControl (opmaak)](./listcontrol-element-format.md)

[Element List entry (indeling)](./listentry-element-for-listcontrol-format.md)

[Lijst weergave](./creating-a-list-view.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
