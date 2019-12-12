---
title: CustomEntries-element voor CustomControl voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359042"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)

Biedt de definities van een gemeen schappelijk besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Formatteer

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomEntries` beschreven. U moet een of meer onderliggende elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Biedt een definitie van het algemene besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomControl-element voor besturings element voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Hiermee definieert u een algemeen besturings element.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen heeft een besturings element slechts één definitie, die in één `CustomEntry` element is gedefinieerd. Het is echter mogelijk om meerdere definities te hebben als u hetzelfde besturings element wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een `CustomEntry` element definiëren voor elk object of set met objecten.

## <a name="see-also"></a>Zie ook

[CustomControl-element voor besturings element voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
