---
title: SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d5858145e092dc962174a776889a4f62db366d71
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785333"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)

Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.

Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven. U moet één `PropertyName` element of opgeven `ScriptBlock` . De `SelectionSetName` `TypeName` elementen en zijn optioneel. U kunt een van beide elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[Het element TypeName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor EnumerableExpansion (opmaak)](./entryselectedby-element-for-enumerableexpansion-format.md)|Hiermee definieert u welke .NET-verzamelings objecten worden uitgevouwen door deze definitie.|

## <a name="remarks"></a>Opmerkingen

Voor elke definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor Diplaying-gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Voor waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
