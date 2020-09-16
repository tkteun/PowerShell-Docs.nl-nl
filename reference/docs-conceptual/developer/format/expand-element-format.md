---
title: Element uitbreiden (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783650"
---
# <a name="expand-element-format"></a>Het element Uitvouwen (opmaak)

Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) element uitbreiden (indeling)

## <a name="syntax"></a>Syntax

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Expand` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EnumerableExpansion (opmaak)](./enumerableexpansion-element-format.md)|Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef een van de volgende waarden op:

- EnumOnly: alleen de eigenschappen van de objecten in de verzameling worden weer gegeven.

- CoreOnly: alleen de eigenschappen van het verzamelings object worden weer gegeven.

- Beide: Hiermee worden de eigenschappen van de objecten in de verzameling en de eigenschappen van het verzamelings object weer gegeven.

## <a name="remarks"></a>Opmerkingen

Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven. In dit geval verwijst een verzamelings object naar een object dat de interface  **System. Collections. ICollection** ondersteunt.

Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.

## <a name="see-also"></a>Zie ook

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
