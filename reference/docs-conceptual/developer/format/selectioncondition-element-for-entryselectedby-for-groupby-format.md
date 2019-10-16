---
title: SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358885"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)

Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (indeling) EntrySelectedBy voor CustomEntry voor GroupBy (Format) SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionCondition` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element PropertyName voor SelectionCondition voor GroupBy (indeling)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor SelectionCondition voor GroupBy (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[SelectionSetName-element voor SelectionCondition voor GroupBy (indeling)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[TypeName-element voor SelectionCondition voor GroupBy (indeling)](./typename-element-for-selectioncondition-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="remarks"></a>Opmerkingen

Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[TypeName-element voor SelectionCondition voor GroupBy (indeling)](./typename-element-for-selectioncondition-for-groupby-format.md)

[EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
