---
title: CustomEntries-element voor CustomControl voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b1f494cf1a254d71362830ba9eb0f4905a2a484d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785979"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)

Biedt de definities van een gemeen schappelijk besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomEntries` element beschreven. U moet een of meer onderliggende elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Biedt een definitie van het algemene besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomControl-element voor besturings element voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Hiermee definieert u een algemeen besturings element.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is gedefinieerd `CustomEntry` . Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[CustomControl-element voor besturings element voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
