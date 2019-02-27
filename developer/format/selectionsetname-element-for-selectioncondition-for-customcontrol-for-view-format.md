---
title: SelectionSetName-Element voor SelectionCondition voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851546"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)

Hiermee geeft u de set met .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van dit besturingselement. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor EntrySelectedBy weergeven (indeling) Element voor CustomEntry voor weergave (indeling)

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
|[SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de selectie is ingesteld.

## <a name="remarks"></a>Opmerkingen

Selectiesets zijn algemene groepen van .NET-objecten die kunnen worden gebruikt door een weergave met de opmaak-bestand definieert. Zie voor meer informatie over het maken en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).

De selectievoorwaarde een selectie instellen of .NET-type kunt opgeven, maar u kunt niet beide opgeven. Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zie ook

[SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Voorwaarden voor wanneer gegevens worden weergegeven definiëren](./defining-conditions-for-displaying-data.md)

[Selectiesets definiëren](./defining-selection-sets.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
