---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)
description: Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 16b048e73195b3d6168724714ff223851dc1b20b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664849"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)

Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="remarks"></a>Opmerkingen

Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
