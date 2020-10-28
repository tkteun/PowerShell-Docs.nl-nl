---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomControl voor Weergave (opmaak)
description: Het element CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 41352be55f0c03b2eaca0dbe2d7345e7cf804a7c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655471"
---
# <a name="customcontrol-element-for-view-format"></a>Het element CustomControl voor Weergave (opmaak)

Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControl` element beschreven. U moet één onderliggend element opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntries voor CustomControl voor Weergave (opmaak)](./customentries-element-for-customcontrol-for-view-format.md)|Vereist element.<br /><br /> Biedt de definities van de aangepaste beheer weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen is er slechts één definitie vereist voor elke controle weergave, maar het is mogelijk om meerdere definities op te geven als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[Het element CustomEntries voor CustomControl voor Weergave (opmaak)](./customentries-element-for-customcontrol-for-view-format.md)

[Het element Weergave (opmaak)](./view-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
