---
title: ViewDefinitions-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a108c4f8b03e3dec3905181b390aee2c82ab0028
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772481"
---
# <a name="viewdefinitions-element-format"></a>Het element ViewDefinitions (opmaak)

Hiermee worden de weer gaven gedefinieerd die worden gebruikt om .NET-objecten weer te geven. Deze weer gaven kunnen de eigenschappen en script waarden van een object in tabel indeling, lijst opmaak, brede indeling en aangepaste besturings elementen weer geven.

Element configuratie-element (indeling) ViewDefinitions (XML-indeling)

## <a name="syntax"></a>Syntax

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ViewDefinitions` element beschreven. Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand en ze kunnen in elke wille keurige volg orde worden toegevoegd.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Configuratie (opmaak)](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

Zie de volgende onderwerpen voor meer informatie over de onderdelen van de verschillende typen weer gaven:

- [Een tabelweergave maken](./creating-a-table-view.md)

- [Een lijstweergave maken](./creating-a-list-view.md)

- [Een brede weergave maken](./creating-a-wide-view.md)

- [Aangepaste besturings elementen](./creating-custom-controls.md)

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `ViewDefinitions` element dat de bovenliggende elementen bevat voor een tabel weergave en een lijst weergave.

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

[Het element Configuratie (opmaak)](./configuration-element-format.md)

[Het element Weergave (opmaak)](./view-element-format.md)

[Een tabelweergave maken](./creating-a-table-view.md)

[Een lijstweergave maken](./creating-a-list-view.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Aangepaste besturings elementen](./creating-custom-controls.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
