---
title: Control-element voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359087"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)

Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.

Configuratie-element (Format) Controls element van configuratie-element (Format) voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element voor het `Control`-element beschreven. U moet slechts één van beide onderliggende elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomControl-element voor besturings elementen voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee wordt het besturings element gedefinieerd.|
|[Naam element voor besturings element voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Beheert element van configuratie (indeling)](./controls-element-for-configuration-format.md)|Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand of door andere besturings elementen.|

## <a name="remarks"></a>Opmerkingen

In de volgende elementen kan worden verwezen naar de naam die aan dit besturings element wordt gegeven:

- [ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Beheert element van configuratie (indeling)](./controls-element-for-configuration-format.md)

[CustomControl-element voor besturings element voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

[Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
