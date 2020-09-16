---
title: SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783412"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor besturings elementen voor configuratie (Format) CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor configuratie (indeling)

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
|[Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee worden de .NET-typen gedefinieerd die dit item van de algemene besturings definitie gebruiken.|

## <a name="remarks"></a>Opmerkingen

De volgende richt lijnen moeten worden gevolgd bij het definiëren van een selectie voorwaarde:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
