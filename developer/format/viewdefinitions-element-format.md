---
title: ViewDefinitions-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083702"
---
# <a name="viewdefinitions-element-format"></a>Het element ViewDefinitions (opmaak)

Definieert de weergaven die wordt gebruikt om .NET-objecten weer te geven. Deze weergaven kunnen de eigenschappen en waarden van script van een object in een tabelindeling, lijstweergave, beeldschermen en indeling van aangepast besturingselement weergegeven.

Configuration Element (Format) ViewDefinitions (Format XML) Element

## <a name="syntax"></a>Syntaxis

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ViewDefinitions` element. Er is geen limiet voor het aantal weergaven die kunnen worden gedefinieerd in een bestand met opmaak, en ze kunnen in willekeurige volgorde worden toegevoegd.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave die wordt gebruikt om een of meer .NET-objecten weer te geven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Configuratie-Element (indeling)](./configuration-element-format.md)|Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.|

## <a name="remarks"></a>Opmerkingen

Zie de volgende onderwerpen voor meer informatie over de onderdelen van de verschillende typen weergaven:

- [Het maken van een tabelweergave](./creating-a-table-view.md)

- [Het maken van een lijst weergeven](./creating-a-list-view.md)

- [Het maken van een brede weergave](./creating-a-wide-view.md)

- [Aangepaste besturingselementen](./creating-custom-controls.md)

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `ViewDefinitions` element met de bovenliggende elementen voor een overzicht van de tabel en een lijst weergeven.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Zie ook

[Configuratie-Element (indeling)](./configuration-element-format.md)

[Weergave-Element (indeling)](./view-element-format.md)

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Aangepaste besturingselementen](./creating-custom-controls.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
