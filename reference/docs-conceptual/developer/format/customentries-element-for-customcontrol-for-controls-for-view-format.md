---
title: CustomEntries-element voor CustomControl voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359026"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)

Bevat de definities voor het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling)

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
|[CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Vereist element.<br /><br /> Biedt een definitie van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomControl-element voor besturings elementen voor de weer gave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Hiermee definieert u het besturings element dat wordt gebruikt door de weer gave.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die is opgegeven in één `CustomEntry`-element. Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een `CustomEntry`-element definiëren voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-element voor besturings elementen voor de weer gave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
