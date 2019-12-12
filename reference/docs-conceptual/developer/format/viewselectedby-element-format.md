---
title: ViewSelectedBy-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358733"
---
# <a name="viewselectedby-element-format"></a>Het element ViewSelectedBy (opmaak)

Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave. Elke weer gave moet ten minste één .NET-object opgeven.

ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy-element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ViewSelectedBy` beschreven. Dit element moet ten minste één `TypeName` of `SelectionSetName` onderliggend element bevatten. Er is geen limiet voor het aantal onderliggende elementen dat kan worden opgegeven, en de volg orde hiervan is aanzienlijk.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TypeName-element voor ViewSelectedBy (indeling)](./typename-element-for-viewselectedby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.|
|[SelectionSetName-element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element weer geven (indeling)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven de [tabel weergave onderdelen](./creating-a-table-view.md), [lijst weergave onderdelen](./creating-a-list-view.md), [brede weer gave](./creating-a-wide-view.md)-onderdelen en [aangepaste besturings elementen](./creating-custom-controls.md).

Het element `SelectionSetName` wordt gebruikt wanneer het opmaak bestand een set objecten definieert die door meerdere weer gaven worden weer gegeven. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over de manier waarop selectie sets worden gedefinieerd en waarnaar wordt verwezen.

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

[Een lijst weergave maken](./creating-a-list-view.md)

[Een tabel weergave maken](./creating-a-table-view.md)

[Een brede weer gave maken](./creating-a-wide-view.md)

[Aangepaste besturings elementen maken](./creating-custom-controls.md)

[Selectie sets definiëren](./defining-selection-sets.md)

[SelectionSetName-element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName-element (Format)](./typename-element-for-viewselectedby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
