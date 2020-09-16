---
title: SelectionSets-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785197"
---
# <a name="selectionsets-element-format"></a>Het element SelectionSets (opmaak)

Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand. De weer gaven en besturings elementen van het opmaak bestand kunnen verwijzen naar de volledige set met objecten door alleen de naam van de selectieset te gebruiken.

SelectionSets element indeling van configuratie-element

## <a name="syntax"></a>Syntax

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSets` element beschreven. Elk onderliggend element definieert een set objecten waarnaar kan worden verwezen door de naam van de set. De volg orde van de onderliggende elementen is niet significant.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionSet (opmaak)](./selectionset-element-format.md)|Vereist element.<br /><br /> Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Configuratie-element](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname. Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.

Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven. In deze gevallen geeft het `SelectionSetName` onderliggende element van de- `ViewSelectedBy` en- `EntrySelectedBy` elementen de set op die moet worden gebruikt. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="see-also"></a>Zie ook

[Configuratie-element](./configuration-element-format.md)

[Selectiereeksen definiëren](./defining-selection-sets.md)

[Het element SelectionSet (opmaak)](./selectionset-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
