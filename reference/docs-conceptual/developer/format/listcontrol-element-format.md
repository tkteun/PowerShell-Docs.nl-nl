---
title: ListControl-element (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785724"
---
# <a name="listcontrol-element-format"></a>Het element ListControl (opmaak)

Hiermee definieert u een lijst indeling voor de weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl-element (indeling)

## <a name="syntax"></a>Syntax

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListControl` element beschreven. Dit element mag slechts één onderliggend element bevatten.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element List Entries (indeling)](./listentries-element-for-listcontrol-format.md)|Vereist element.<br /><br /> Biedt de definities van de lijst weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het maken van een lijst weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een lijst weergave voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[Het element Weergave (opmaak)](./view-element-format.md)

[Element List Entries (indeling)](./listentries-element-for-listcontrol-format.md)

[Een lijstweergave maken](./creating-a-list-view.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
