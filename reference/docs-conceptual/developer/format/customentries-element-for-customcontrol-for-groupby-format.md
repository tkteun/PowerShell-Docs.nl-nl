---
title: CustomEntries-element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355284"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>Het element CustomEntries voor CustomControl voor GroupBy (opmaak)

Bevat de definities voor het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het element GroupBy

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen van het element `CustomEntries` beschreven. Er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md)|Vereist element.<br /><br /> Biedt een definitie van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomControl-element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md)|Hiermee definieert u het aangepaste besturings element waarin de nieuwe groep wordt weer gegeven.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die is opgegeven in één `CustomEntry`-element. Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende groepen weer te geven. In dergelijke gevallen kunt u een `CustomEntry`-element definiëren voor een groep.

## <a name="see-also"></a>Zie ook

[CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
