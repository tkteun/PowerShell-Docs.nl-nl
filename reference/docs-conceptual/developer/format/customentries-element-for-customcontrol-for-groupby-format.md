---
title: CustomEntries-element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785945"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>Het element CustomEntries voor CustomControl voor GroupBy (opmaak)

Bevat de definities voor het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het element GroupBy

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen van het `CustomEntries` element beschreven. Er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomControl voor GroupBy (opmaak)](./customentry-element-for-customcontrol-for-groupby-format.md)|Vereist element.<br /><br /> Biedt een definitie van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomControl voor GroupBy (opmaak)](./customcontrol-element-for-groupby-format.md)|Hiermee definieert u het aangepaste besturings element waarin de nieuwe groep wordt weer gegeven.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is opgegeven `CustomEntry` . Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende groepen weer te geven. In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor een groep.

## <a name="see-also"></a>Zie ook

[Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Het element CustomControl voor GroupBy (opmaak)](./customcontrol-element-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
