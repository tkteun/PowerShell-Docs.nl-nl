---
title: CustomEntries-Element voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066512"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Het element CustomEntries voor CustomControl voor Weergave (opmaak)

Bevat de definities van de weergave van het aangepaste besturingselement. De weergave van het aangepaste besturingselement moet een of meer netwerkdefinities opgeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControlEntries` element. U moet een of meer onderliggende elementen.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomEntries voor weergave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Vereist element.<br /><br /> Bevat een definitie van de weergave van het aangepaste besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element voor weergave (indeling)](./customcontrol-element-for-view-format.md)|Vereist element.<br /><br /> Hiermee definieert u een aangepast besturingselement-indeling voor de weergave.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen een besturingselement heeft slechts één definitie die is gedefinieerd in een enkel `CustomEntry` element. Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven. In deze gevallen kunt u een `CustomEntry` -element voor elk object of een set van objecten.

## <a name="see-also"></a>Zie ook

[CustomControl-Element voor weergave (indeling)](./customcontrol-element-for-view-format.md)

[CustomEntry-Element voor CustomEntries voor weergave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
