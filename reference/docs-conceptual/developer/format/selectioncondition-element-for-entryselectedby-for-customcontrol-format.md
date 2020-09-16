---
title: SelectionCondition-element voor EntrySelectedBy voor CustomControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 52858dba5c7a5222b5410835f3374546ce8b88a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785350"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)

Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (Format) CustomControl element voor weer gave (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor het object CustomControl voor weer gave (Format) EntrySelectedBy voor CustomEntry

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
|[Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[Het element TypeName voor SelectionCondition voor CustomControl voor Weergave (opmaak)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="remarks"></a>Opmerkingen

Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Het element TypeName voor SelectionCondition voor CustomControl voor Weergave (opmaak)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
