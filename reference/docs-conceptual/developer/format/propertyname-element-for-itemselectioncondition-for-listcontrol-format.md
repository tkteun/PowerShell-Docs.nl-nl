---
title: PropertyName-element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354094"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)

Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Als deze eigenschap aanwezig is of als deze wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de weer gave gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type-element (indeling) List item (Format) List items-element Element voor list items voor ListControl (Format) ItemSelectionCondition-element voor lijst item voor ListControls PropertyName-element voor ItemSelectionCondition voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `PropertyName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ItemSelectionCondition-element voor lijst item voor ListControl (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Tekst waarde

Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.

## <a name="remarks"></a>Opmerkingen

Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.

## <a name="see-also"></a>Zie ook

[Script block-element voor ItemSelectionCondition voor ListIControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition-element voor lijst item voor ListControl (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
