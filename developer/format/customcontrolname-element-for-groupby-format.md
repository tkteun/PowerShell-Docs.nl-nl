---
title: CustomControlName-Element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849824"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Het element CustomControlName voor GroupBy (opmaak)

Hiermee geeft u de naam van een aangepast besturingselement dat wordt gebruikt om de nieuwe groep weer te geven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepast besturingselement weergeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControlName-Element van GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en de bovenliggende elementen van de `CustomControlName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)|Hiermee definieert u hoe een nieuwe groep objecten worden weergegeven in Windows PowerShell.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het aangepaste besturingselement dat wordt gebruikt om een nieuwe groep weer te geven.

## <a name="remarks"></a>Opmerkingen

Kunt u algemene besturingselementen die kunnen worden gebruikt door alle weergaven van een opmaak bestand maken en u kunt besturingselementen weergeven die kunnen worden gebruikt door een specifieke weergave maken. De volgende elementen geeft de namen van deze aangepaste besturingselementen:

- [Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md)

[Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Naamelement voor controle van besturingselementen voor weergave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
