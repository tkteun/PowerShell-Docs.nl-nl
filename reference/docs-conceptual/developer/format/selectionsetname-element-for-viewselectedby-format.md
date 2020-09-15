---
title: SelectionSetName-element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6410b463bcb00d2758849c2f7e13cd839277e50
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772600"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Het element SelectionSetName voor ViewSelectedBy (opmaak)

Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy element (Format) SelectionSetName element voor ViewSelectedBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element ViewSelectedBy (opmaak)](./viewselectedby-element-format.md)|Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van de selectieset die is gedefinieerd door het `Name` element voor de selectieset.

## <a name="remarks"></a>Opmerkingen

U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren en verwijzen van selectie sets.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een lijst weergave. Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Het element ViewSelectedBy (opmaak)](./viewselectedby-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
