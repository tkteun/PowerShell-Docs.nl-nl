---
title: SelectionCondition-element voor EntrySelectedBy voor CustomControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358889"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)

Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave ( Format) CustomItem-element voor CustomEntry voor CustomControl voor weer gave (Format) EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (Format) SelectionCondition element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)

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
|[Het element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[TypeName-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="remarks"></a>Opmerkingen

Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[TypeName-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
