---
title: CustomEntries-element voor CustomControl voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783701"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)

Bevat de definities voor het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor weer gave (Format) CustomEntries element voor weer gave (indeling)

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
|[Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Vereist element.<br /><br /> Biedt een definitie van het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Hiermee definieert u het besturings element dat wordt gebruikt door de weer gave.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die in één element is opgegeven `CustomEntry` . Het is echter mogelijk om meerdere definities op te geven als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een element definiëren `CustomEntry` voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Het element CustomControl voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
