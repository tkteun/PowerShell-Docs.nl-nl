---
title: SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064226"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor besturingselementen voor weergave ( -Indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[PropertyName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-eigenschap die de voorwaarde wordt geactiveerd.|
|[ScriptBlock-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.|
|[SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set van .NET-typen die de voorwaarde wordt geactiveerd.|
|[TypeName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|

## <a name="remarks"></a>Opmerkingen

Wanneer u een selectievoorwaarde definieert, wordt de volgende vereisten gelden:

- De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.

- De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.

Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Zie ook

[PropertyName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[ScriptBlock-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[TypeName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
