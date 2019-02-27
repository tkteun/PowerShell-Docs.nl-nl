---
title: Element beheren voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848830"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u een algemene besturingselement dat kan worden gebruikt door alle weergaven van de opmaak bestands- en de naam die wordt gebruikt om te verwijzen naar het besturingselement.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element voor besturingselementen voor de configuratie (-indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element voor de `Control` element. U moet slechts één van elk onderliggend element opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element voor het besturingselement voor besturingselementen voor de configuratie (-indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee definieert u het besturingselement.|
|[Naamelement voor controle voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar het besturingselement.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Besturingselementen Element van de configuratie (-indeling)](./controls-element-for-configuration-format.md)|Hiermee definieert u de algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak bestand of andere besturingselementen.|

## <a name="remarks"></a>Opmerkingen

De naam van dit besturingselement kan naar worden verwezen in de volgende elementen:

- [ExpressionBinding-Element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy-Element voor View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Besturingselementen Element van de configuratie (-indeling)](./controls-element-for-configuration-format.md)

[CustomControl-element voor controle voor de configuratie (-indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding-Element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy-Element voor View(Format)](./groupby-element-for-view-format.md)

[Naamelement voor controle van besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
