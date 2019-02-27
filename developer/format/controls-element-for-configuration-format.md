---
title: Hiermee bepaalt u Element voor configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850433"
---
# <a name="controls-element-for-configuration-format"></a>Het element Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u de algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen-Element van de configuratie (-indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Controls` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Controle-Element voor besturingselementen voor de configuratie (-indeling)](./control-element-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee definieert u een algemene besturingselement dat kan worden gebruikt door alle weergaven van de opmaak-bestand.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Configuratie-Element (indeling)](./configuration-element-format.md)|Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.|

## <a name="remarks"></a>Opmerkingen

U kunt een willekeurig aantal veelgebruikte besturingselementen kunt maken. Voor elk besturingselement, moet u de naam die wordt gebruikt om te verwijzen naar het besturingselement en de onderdelen van het besturingselement opgeven.

## <a name="see-also"></a>Zie ook

[Configuratie-Element (indeling)](./configuration-element-format.md)

[Controle-Element voor besturingselementen voor de configuratie (-indeling)](./control-element-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
