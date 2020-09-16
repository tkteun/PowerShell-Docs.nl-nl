---
title: TypeName-element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9a391565c3e66041dd9a340455dccfce9ce929b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780029"
---
# <a name="typename-element-for-viewselectedby-format"></a>Het element TypeName voor ViewSelectedBy (opmaak)

Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy element (Format) voor ViewSelectedBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `TypeName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ViewSelectedBy (opmaak)](./viewselectedby-element-format.md)|Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md), een [lijst weergave](./creating-a-list-view.md)maken, [een brede weer gave](./creating-a-wide-view.md)en [aangepaste weergave onderdelen](./creating-custom-controls.md)maken voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven.

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

[Het element ViewSelectedBy (opmaak)](./viewselectedby-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
