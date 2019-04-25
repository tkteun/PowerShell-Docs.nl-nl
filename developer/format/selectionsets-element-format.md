---
title: SelectionSets-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063763"
---
# <a name="selectionsets-element-format"></a>Het element SelectionSets (opmaak)

Hiermee definieert u de algemene sets met .NET-objecten die kunnen worden gebruikt door alle weergaven van de opmaak-bestand. De weergaven en besturingselementen van het bestand opmaak kunnen de volledige set van objecten verwijzen naar een met behulp van alleen de naam van de selectie op.

Indeling van de configuratie-Element SelectionSets-Element

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `SelectionSets` element. Elk onderliggend element definieert een set van objecten die kan worden verwezen door de naam van de set. De volgorde van de onderliggende elementen is niet belangrijk.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionSet-Element (indeling)](./selectionset-element-format.md)|Vereist element.<br /><br /> Definieert één set met .NET-objecten die kan worden verwezen door de naam van de set.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Configuratie-Element](./configuration-element-format.md)|Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.|

## <a name="remarks"></a>Opmerkingen

U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt. Bij het definiëren van uw weergaven, kunt u de set objecten opgeven met behulp van de naam van de selectie instellen in plaats van de lijst van alle objecten in elke weergave.

Algemene selectiesets worden opgegeven door de naam bij het definiëren van de weergaven van de opmaak bestand of de definities van de weergaven. In dergelijke gevallen de `SelectionSetName` onderliggend element van de `ViewSelectedBy` en `EntrySelectedBy` elementen Hiermee geeft u de set moet worden gebruikt. Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).

## <a name="see-also"></a>Zie ook

[Configuratie-Element](./configuration-element-format.md)

[Selectiesets definiëren](./defining-selection-sets.md)

[SelectionSet-Element (indeling)](./selectionset-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
