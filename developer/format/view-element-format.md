---
title: Weergeven van Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083719"
---
# <a name="view-element-format"></a>Het element Weergave (opmaak)

Hiermee definieert u een weergave met een of meer .NET-objecten. Er is geen limiet voor het aantal weergaven die kunnen worden gedefinieerd in een bestand met opmaak.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling)

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

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `View` element. Moet u slechts één van de onderliggende elementen van controle en moet u de naam van de weergave en de objecten die gebruikmaken van de weergave opgeven. Aangepaste besturingselementen te definiëren, hoe u aan de groep objecten en op te geven als de weergave is het out-of-band zijn optioneel.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Element van de besturingselementen voor weergave (indeling)](./controls-element-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert een set besturingselementen die kan worden verwezen door de naam in de weergave.|
|[CustomControl Element (Format)](./customcontrol-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u een aangepast besturingselement-indeling voor de weergave.|
|[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u hoe de leden van de .NET-objecten worden gegroepeerd.|
|[ListControl Element (indeling)](./listcontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u een indeling voor de weergave heeft.|
|[Naamelement voor weergave (indeling)](./name-element-for-view-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de weergave.|
|[TableControl-Element (indeling)](./tablecontrol-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u een tabelindeling voor de weergave.|
|[ViewSelectedBy-Element voor weergave (indeling)](./viewselectedby-element-format.md)|Vereist element.<br /><br /> Hiermee definieert u de .NET-objecten die deze weergave worden weergegeven.|
|[WideControl-Element (indeling)](./widecontrol-element-format.md)|Optioneel element.<br /><br /> Definieert een breed (één waarde) lijstweergave voor de weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ViewDefinitions-Element (indeling)](./viewdefinitions-element-format.md)|Definieert de weergaven die wordt gebruikt om objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van de verschillende weergaven en aangepaste besturingselementen in de volgende onderwerpen:

- [Onderdelen van de tabel weergeven](./creating-a-table-view.md)

- [Lijst met weergave-onderdelen](./creating-a-list-view.md)

- [Onderdelen van de brede weergave](./creating-a-wide-view.md)

- [Aangepaste besturingselementen](./creating-custom-controls.md)

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `View` element dat een tabelweergave voor definieert de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.

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

[ViewDefinitions-Element (indeling)](./viewdefinitions-element-format.md)

[Naamelement voor weergave (indeling)](./name-element-for-view-format.md)

[ViewSelectedBy-Element (indeling)](./viewselectedby-element-format.md)

[Element van de besturingselementen voor weergave (indeling)](./controls-element-for-view-format.md)

[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)

[TableControl-Element (indeling)](./tablecontrol-element-format.md)

[ListControl Element (indeling)](./listcontrol-element-format.md)

[WideControl-Element (indeling)](./widecontrol-element-format.md)

[CustomControl Element (Format)](./customcontrol-element-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
