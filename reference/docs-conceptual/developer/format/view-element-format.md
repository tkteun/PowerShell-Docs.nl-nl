---
title: Element weer geven (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353443"
---
# <a name="view-element-format"></a>Het element Weergave (opmaak)

Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven. Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling)

## <a name="syntax"></a>Syntaxis

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

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `View` beschreven. U moet één en slechts één van de onderliggende elementen van het besturings element opgeven, en u moet de naam van de weer gave opgeven en de objecten die gebruikmaken van de weer gave. Aangepaste besturings elementen definiëren, objecten groeperen en opgeven of de weer gave out-of-band optioneel is.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element Controls voor weer gave (indeling)](./controls-element-for-view-format.md)|Optioneel element.<br /><br /> Hiermee wordt een set besturings elementen gedefinieerd waarnaar kan worden verwezen met hun naam in de weer gave.|
|[CustomControl-element (indeling)](./customcontrol-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.|
|[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)|Optioneel element.<br /><br /> Hiermee wordt gedefinieerd hoe de leden van de .NET-objecten worden gegroepeerd.|
|[ListControl-element (indeling)](./listcontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u een lijst indeling voor de weer gave.|
|[Naam element voor weer gave (indeling)](./name-element-for-view-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de weer gave.|
|[TableControl-element (indeling)](./tablecontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u een tabel indeling voor de weer gave.|
|[Element ViewSelectedBy voor weer gave (indeling)](./viewselectedby-element-format.md)|Vereist element.<br /><br /> Hiermee worden de .NET-objecten gedefinieerd die in deze weer gave worden weer gegeven.|
|[WideControl-element (indeling)](./widecontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ViewDefinitions-element (indeling)](./viewdefinitions-element-format.md)|Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Zie de volgende onderwerpen voor meer informatie over de onderdelen van verschillende weer gaven en aangepaste besturings elementen:

- [Onderdelen van de tabel weergave](./creating-a-table-view.md)

- [Lijst weergave onderdelen](./creating-a-list-view.md)

- [Brede weergave onderdelen](./creating-a-wide-view.md)

- [Aangepaste besturings elementen](./creating-custom-controls.md)

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `View`-element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .

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

[ViewDefinitions-element (indeling)](./viewdefinitions-element-format.md)

[Naam element voor weer gave (indeling)](./name-element-for-view-format.md)

[ViewSelectedBy-element (indeling)](./viewselectedby-element-format.md)

[Element Controls voor weer gave (indeling)](./controls-element-for-view-format.md)

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

[TableControl-element (indeling)](./tablecontrol-element-format.md)

[ListControl-element (indeling)](./listcontrol-element-format.md)

[WideControl-element (indeling)](./widecontrol-element-format.md)

[CustomControl-element (indeling)](./customcontrol-element-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
