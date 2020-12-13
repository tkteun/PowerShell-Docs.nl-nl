---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Weergave (opmaak)
description: Het element Weergave (opmaak)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649747"
---
# <a name="view-element-format"></a>Het element Weergave (opmaak)

Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven. Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling)

## <a name="syntax"></a>Syntax

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `View` element beschreven. U moet één en slechts één van de onderliggende elementen van het besturings element opgeven, en u moet de naam van de weer gave opgeven en de objecten die gebruikmaken van de weer gave. Aangepaste besturings elementen definiëren, objecten groeperen en opgeven of de weer gave out-of-band optioneel is.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Besturingselementen voor Weergave (opmaak)](./controls-element-for-view-format.md)|Optioneel element.<br /><br /> Hiermee wordt een set besturings elementen gedefinieerd waarnaar kan worden verwezen met hun naam in de weer gave.|
|[CustomControl-element (indeling)](./customcontrol-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.|
|[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)|Optioneel element.<br /><br /> Hiermee wordt gedefinieerd hoe de leden van de .NET-objecten worden gegroepeerd.|
|[Het element ListControl (opmaak)](./listcontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u een lijst indeling voor de weer gave.|
|[Het element Naam voor Weergave (opmaak)](./name-element-for-view-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de weer gave.|
|[Het element TableControl (opmaak)](./tablecontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u een tabel indeling voor de weer gave.|
|[Element ViewSelectedBy voor weer gave (indeling)](./viewselectedby-element-format.md)|Vereist element.<br /><br /> Hiermee worden de .NET-objecten gedefinieerd die in deze weer gave worden weer gegeven.|
|[Het element WideControl (opmaak)](./widecontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ViewDefinitions (opmaak)](./viewdefinitions-element-format.md)|Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Zie de volgende onderwerpen voor meer informatie over de onderdelen van verschillende weer gaven en aangepaste besturings elementen:

- [Onderdelen van de tabel weergave](./creating-a-table-view.md)

- [Lijst weergave onderdelen](./creating-a-list-view.md)

- [Brede weergave onderdelen](./creating-a-wide-view.md)

- [Aangepaste besturings elementen](./creating-custom-controls.md)

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `View` element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Zie ook

[Het element ViewDefinitions (opmaak)](./viewdefinitions-element-format.md)

[Het element Naam voor Weergave (opmaak)](./name-element-for-view-format.md)

[Het element ViewSelectedBy (opmaak)](./viewselectedby-element-format.md)

[Het element Besturingselementen voor Weergave (opmaak)](./controls-element-for-view-format.md)

[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)

[Het element TableControl (opmaak)](./tablecontrol-element-format.md)

[Het element ListControl (opmaak)](./listcontrol-element-format.md)

[Het element WideControl (opmaak)](./widecontrol-element-format.md)

[CustomControl-element (indeling)](./customcontrol-element-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
