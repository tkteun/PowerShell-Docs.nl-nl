---
title: EnumerableExpansion-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 81a8959c19502a2e56f4cfa48a1e480509d84b6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774045"
---
# <a name="enumerableexpansion-element-format"></a>Het element EnumerableExpansion (opmaak)

Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EnumerableExpansion` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor EnumerableExpansion (opmaak)](./entryselectedby-element-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee definieert u welke .NET-verzamelings objecten worden uitgevouwen door deze definitie.|
|[Het element Uitvouwen (opmaak)](./expand-element-format.md)|Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EnumerableExpansions (opmaak)](./enumerableexpansions-element-format.md)|Definieert de verschillende manieren waarop .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven. In dit geval verwijst een verzamelings object naar een object dat de interface  **System. Collections. ICollection** ondersteunt.

Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.

## <a name="see-also"></a>Zie ook

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
