---
title: SelectionSetName-Element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063758"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)

Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object met behulp van dit besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionCondition Element voor EntrySelectedBy voor GroupBy (indeling) SelectionSetName Element voor SelectionCondition voor GroupBy (indeling)

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
|[SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de selectie is ingesteld.

## <a name="remarks"></a>Opmerkingen

Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert. Zie voor meer informatie over het maken en verwijst naar een selectiesets [definiëren voor de selectie wordt ingesteld](./defining-selection-sets.md).

Wanneer dit element is opgegeven, wordt u niet opgeven de [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element. Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zie ook

[TypeName-Element voor SelectionCondition voor GroupBy (indeling)](./typename-element-for-selectioncondition-for-groupby-format.md)

[SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[Selectiesets definiëren](./defining-selection-sets.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
