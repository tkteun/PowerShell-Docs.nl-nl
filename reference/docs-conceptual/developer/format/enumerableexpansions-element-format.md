---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EnumerableExpansions (opmaak)
description: Het element EnumerableExpansions (opmaak)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660171"
---
# <a name="enumerableexpansions-element-format"></a>Het element EnumerableExpansions (opmaak)

Hiermee definieert u hoe .NET-verzamelings objecten worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EnumerableExpansions` element beschreven. Er is geen limiet voor het aantal onderliggende elementen dat u kunt gebruiken.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EnumerableExpansion (opmaak)](./enumerableexpansion-element-format.md)|Optioneel element.<br /><br /> Hiermee worden de specifieke .NET-verzamelings objecten gedefinieerd die worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element DefaultSettings (opmaak)](./defaultsettings-element-format.md)|Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven. In dit geval verwijst een verzamelings object naar een object dat de interface  **System. Collections. ICollection** ondersteunt.

## <a name="see-also"></a>Zie ook

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
