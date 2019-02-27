---
title: CustomControl-Element voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850489"
---
# <a name="customcontrol-element-for-view-format"></a>Het element CustomControl voor Weergave (opmaak)

Hiermee definieert u een aangepast besturingselement-indeling voor de weergave.

Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)

## <a name="syntax"></a>Syntaxis

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControl` element. U kunt één onderliggend element moet opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntries-Element voor CustomControl voor weergave (indeling)](./customentries-element-for-customcontrol-for-view-format.md)|Vereist element.<br /><br /> Bevat de definities van de weergave van het aangepaste besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave die wordt gebruikt om een of meer .NET-objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

In de meeste gevallen slechts één definitie is vereist voor de weergave van elk besturingselement, maar het is mogelijk om meerdere definities als u wilt de dezelfde weergave gebruiken om verschillende .NET-objecten weer te geven. In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.

## <a name="see-also"></a>Zie ook

[CustomEntries-Element voor CustomControl voor weergave (indeling)](./customentries-element-for-customcontrol-for-view-format.md)

[Weergave-Element (indeling)](./view-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
