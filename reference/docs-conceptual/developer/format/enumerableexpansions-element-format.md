---
title: EnumerableExpansions-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354731"
---
# <a name="enumerableexpansions-element-format"></a>Het element EnumerableExpansions (opmaak)

Hiermee definieert u hoe .NET-verzamelings objecten worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EnumerableExpansions` beschreven. Er is geen limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EnumerableExpansion-element (indeling)](./enumerableexpansion-element-format.md)|Optioneel element.<br /><br /> Hiermee worden de specifieke .NET-verzamelings objecten gedefinieerd die worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[DefaultSettings-element (indeling)](./defaultsettings-element-format.md)|Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven. In dit geval verwijst een verzamelings object naar een object dat de interface **System. Collections. ICollection** ondersteunt.

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
