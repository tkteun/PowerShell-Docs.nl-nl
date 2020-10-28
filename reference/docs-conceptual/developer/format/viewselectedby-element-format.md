---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ViewSelectedBy (opmaak)
description: Het element ViewSelectedBy (opmaak)
ms.openlocfilehash: ac3c7de299b3009a067a476a024c6a6fcb5dce02
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667705"
---
# <a name="viewselectedby-element-format"></a>Het element ViewSelectedBy (opmaak)

Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave. Elke weer gave moet ten minste één .NET-object opgeven.

ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy-element (indeling)

## <a name="syntax"></a>Syntax

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ViewSelectedBy` element beschreven. Dit element moet ten minste één `TypeName` of een `SelectionSetName` onderliggend element bevatten. Er is geen limiet voor het aantal onderliggende elementen dat kan worden opgegeven, en de volg orde hiervan is aanzienlijk.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TypeName voor ViewSelectedBy (opmaak)](./typename-element-for-viewselectedby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.|
|[Het element SelectionSetName voor ViewSelectedBy (opmaak)](./selectionsetname-element-for-viewselectedby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven de [tabel weergave onderdelen](./creating-a-table-view.md), [lijst weergave onderdelen](./creating-a-list-view.md), [brede weer gave](./creating-a-wide-view.md)-onderdelen en [aangepaste besturings elementen](./creating-custom-controls.md).

Het `SelectionSetName` element wordt gebruikt wanneer het opmaak bestand een set objecten definieert die door meerdere weer gaven worden weer gegeven. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over de manier waarop selectie sets worden gedefinieerd en waarnaar wordt verwezen.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) opgeeft voor een lijst weergave. Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Een tabelweergave maken](./creating-a-table-view.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Aangepaste besturingselementen maken](./creating-custom-controls.md)

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Het element SelectionSetName voor ViewSelectedBy (opmaak)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName-element (Format)](./typename-element-for-viewselectedby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
