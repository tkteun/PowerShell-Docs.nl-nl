---
title: CustomEntries-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847024"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)

Bevat de definities van een algemene besturingselementen. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomEntries` element. U moet een of meer onderliggende elementen.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Bevat een definitie van de algemene besturingselementen.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element voor controle voor de configuratie (-indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Hiermee definieert u een algemene besturingselement.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen een besturingselement heeft slechts één definitie die is gedefinieerd in een enkel `CustomEntry` element. Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven. In deze gevallen kunt u een `CustomEntry` -element voor elk object of een set van objecten.

## <a name="see-also"></a>Zie ook

[CustomControl-Element voor controle voor de configuratie (-indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
