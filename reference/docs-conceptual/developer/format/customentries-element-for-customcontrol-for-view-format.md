---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomEntries voor CustomControl voor Weergave (opmaak)
description: Het element CustomEntries voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649970"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Het element CustomEntries voor CustomControl voor Weergave (opmaak)

Biedt de definities van de aangepaste beheer weergave. In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) CustomControl element (indeling) CustomEntries element voor CustomControl voor weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomControlEntries` element beschreven. U moet een of meer onderliggende elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Vereist element.<br /><br /> Biedt een definitie van de aangepaste beheer weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomControl voor Weergave (opmaak)](./customcontrol-element-for-view-format.md)|Vereist element.<br /><br /> Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is gedefinieerd `CustomEntry` . Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[Het element CustomControl voor Weergave (opmaak)](./customcontrol-element-for-view-format.md)

[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
