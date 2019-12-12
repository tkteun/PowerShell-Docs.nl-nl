---
title: SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358897"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries-element voor besturings elementen voor Configuratie (indeling) CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de configuratie (indeling) SelectionCondition element voor EntrySelectedBy voor CustomEntry voor Configuratie (indeling)

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
|[Het element PropertyName voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.|
|[Script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.|
|[SelectionSetName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.|
|[TypeName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee worden de .NET-typen gedefinieerd die dit item van de algemene besturings definitie gebruiken.|

## <a name="remarks"></a>Opmerkingen

De volgende richt lijnen moeten worden gevolgd bij het definiëren van een selectie voorwaarde:

- De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.

- Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.

Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[Het element PropertyName voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionSetName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[TypeName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
