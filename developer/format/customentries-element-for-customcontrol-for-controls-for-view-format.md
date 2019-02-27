---
title: CustomEntries-Element voor CustomControl voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850874"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Het element CustomEntries voor CustomControl voor Besturingselementen voor Weergave (opmaak)

Bevat de definities voor het besturingselement. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen van de `CustomEntries` element. Er is geen maximale limiet voor het aantal onderliggende elementen die kunnen worden opgegeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Vereist element.<br /><br /> Bevat een definitie van het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Hiermee definieert u het besturingselement wordt gebruikt door de weergave.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen een besturingselement heeft slechts één definitie die is opgegeven in een enkel `CustomEntry` element. Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven. In deze gevallen kunt u een `CustomEntry` -element voor elk object of een set van objecten.

## <a name="see-also"></a>Zie ook

[CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
