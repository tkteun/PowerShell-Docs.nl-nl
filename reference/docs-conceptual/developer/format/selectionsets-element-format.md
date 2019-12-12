---
title: SelectionSets-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353730"
---
# <a name="selectionsets-element-format"></a>Het element SelectionSets (opmaak)

Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand. De weer gaven en besturings elementen van het opmaak bestand kunnen verwijzen naar de volledige set met objecten door alleen de naam van de selectieset te gebruiken.

SelectionSets element indeling van configuratie-element

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionSets` beschreven. Elk onderliggend element definieert een set objecten waarnaar kan worden verwezen door de naam van de set. De volg orde van de onderliggende elementen is niet significant.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Selectie verzamelings element (indeling)](./selectionset-element-format.md)|Vereist element.<br /><br /> Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Configuratie-element](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname. Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.

Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven. In dergelijke gevallen specificeert het `SelectionSetName` onderliggende element van de `ViewSelectedBy` en `EntrySelectedBy` elementen de set die moet worden gebruikt. Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.

## <a name="see-also"></a>Zie ook

[Configuratie-element](./configuration-element-format.md)

[Selectie sets definiëren](./defining-selection-sets.md)

[Selectie verzamelings element (indeling)](./selectionset-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
