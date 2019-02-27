---
title: ViewSelectedBy-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851840"
---
# <a name="viewselectedby-element-format"></a>Het element ViewSelectedBy (opmaak)

Hiermee definieert u de .NET-objecten die worden weergegeven in de weergave. Elke weergave moet ten minste één .NET-object opgeven.

ViewDefinitions-Element (indeling) weergave Element (indeling) ViewSelectedBy Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ViewSelectedBy` element. Dit element moet ten minste één bevatten `TypeName` of `SelectionSetName` onderliggend element. Er is geen limiet voor het aantal onderliggende elementen die kunnen worden opgegeven of is de volgorde belangrijk.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[TypeName-Element voor ViewSelectedBy (indeling)](./typename-element-for-viewselectedby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-object dat door de weergave wordt weergegeven.|
|[SelectionSetName-Element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set van .NET-objecten die worden weergegeven in de weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave met een of meer .NET-objecten.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weergaven, [tabel weergave onderdelen](./creating-a-table-view.md), [lijst weergave onderdelen](./creating-a-list-view.md), [brede weergave onderdelen](./creating-a-wide-view.md), en [Aangepast besturingselement onderdelen](./creating-custom-controls.md).

De `SelectionSetName` element wordt gebruikt wanneer de opmaak-bestand definieert een set van objecten die door meerdere weergaven worden weergegeven. Zie voor meer informatie over hoe selectiesets zijn gedefinieerd en waarnaar wordt verwezen, [ingesteld definiëren van objecten](./defining-selection-sets.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) -object voor een lijst weergeven. Hetzelfde schema wordt gebruikt voor de tabel, breed en aangepaste weergaven.

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

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Het maken van aangepaste besturingselementen](./creating-custom-controls.md)

[Selectiesets definiëren](./defining-selection-sets.md)

[SelectionSetName-Element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName Element (indeling)](./typename-element-for-viewselectedby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
