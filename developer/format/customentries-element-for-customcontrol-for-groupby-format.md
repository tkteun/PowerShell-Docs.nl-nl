---
title: CustomEntries-Element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845183"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>Het element CustomEntries voor CustomControl voor GroupBy (opmaak)

Bevat de definities voor het besturingselement. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl-Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen van de `CustomEntries` element. Er is geen maximale limiet voor het aantal onderliggende elementen die kunnen worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md)|Vereist element.<br /><br /> Bevat een definitie van het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md)|Hiermee definieert u het aangepaste besturingselement weergegeven met de nieuwe groep.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen een besturingselement heeft slechts één definitie die is opgegeven in een enkel `CustomEntry` element. Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende groepen weer te geven. In deze gevallen kunt u een `CustomEntry` -element voor een groep.

## <a name="see-also"></a>Zie ook

[CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-Element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
