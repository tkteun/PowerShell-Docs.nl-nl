---
title: ViewDefinitions-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353415"
---
# <a name="viewdefinitions-element-format"></a>Het element ViewDefinitions (opmaak)

Hiermee worden de weer gaven gedefinieerd die worden gebruikt om .NET-objecten weer te geven. Deze weer gaven kunnen de eigenschappen en script waarden van een object in tabel indeling, lijst opmaak, brede indeling en aangepaste besturings elementen weer geven.

Element configuratie-element (indeling) ViewDefinitions (XML-indeling)

## <a name="syntax"></a>Syntaxis

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ViewDefinitions` beschreven. Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand en ze kunnen in elke wille keurige volg orde worden toegevoegd.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element weer geven (indeling)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Configuratie-element (indeling)](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

Zie de volgende onderwerpen voor meer informatie over de onderdelen van de verschillende typen weer gaven:

- [Een tabel weergave maken](./creating-a-table-view.md)

- [Een lijst weergave maken](./creating-a-list-view.md)

- [Een brede weer gave maken](./creating-a-wide-view.md)

- [Aangepaste besturings elementen](./creating-custom-controls.md)

## <a name="example"></a>Voorbeeld

In dit voor beeld wordt een `ViewDefinitions`-element weer gegeven dat de bovenliggende elementen voor een tabel weergave en een lijst weergave bevat.

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

[Configuratie-element (indeling)](./configuration-element-format.md)

[Element weer geven (indeling)](./view-element-format.md)

[Een tabel weergave maken](./creating-a-table-view.md)

[Een lijst weergave maken](./creating-a-list-view.md)

[Een brede weer gave maken](./creating-a-wide-view.md)

[Aangepaste besturings elementen](./creating-custom-controls.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
