---
title: CustomEntries-element voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355277"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Het element CustomEntries voor CustomControl voor Weergave (opmaak)

Biedt de definities van de aangepaste beheer weergave. In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) CustomControl element (indeling) CustomEntries element voor CustomControl voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlEntries` beschreven. U moet een of meer onderliggende elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Vereist element.<br /><br /> Biedt een definitie van de aangepaste beheer weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomControl-element voor weer gave (indeling)](./customcontrol-element-for-view-format.md)|Vereist element.<br /><br /> Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die is gedefinieerd in één `CustomEntry`-element. Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een `CustomEntry`-element definiëren voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[CustomControl-element voor weer gave (indeling)](./customcontrol-element-for-view-format.md)

[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
