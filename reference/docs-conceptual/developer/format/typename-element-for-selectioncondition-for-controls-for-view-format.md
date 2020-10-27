---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)
description: Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: e70fc05667c27fa3b68f3c9a1802c1e3bba8b7ce
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651334"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a>Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor het SelectionCondition-element van de EntrySelectedBy voor besturings elementen voor de weer gave (Format) voor SelectionCondition voor besturings elementen voor weer gave (indeling)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
