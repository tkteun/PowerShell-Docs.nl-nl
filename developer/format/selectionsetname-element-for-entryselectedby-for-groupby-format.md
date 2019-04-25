---
title: SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064064"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a>Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)

Hiermee geeft u een set van .NET-objecten voor de vermelding in de lijst. Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionSetName Element voor EntrySelectedBy voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de selectie is ingesteld.

## <a name="remarks"></a>Opmerkingen

De definitie van elk aangepast besturingselement moet ten minste één typenaam, selectie instellen of selectievoorwaarde gedefinieerd hebben.

Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven. U wilt bijvoorbeeld een tabel en een lijstweergave voor dezelfde set objecten maken. Zie voor meer informatie over het definiëren van selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).

Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [het maken van aangepaste besturingselementen](./creating-custom-controls.md).

## <a name="see-also"></a>Zie ook

[EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Het maken van aangepaste besturingselementen](./creating-custom-controls.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
