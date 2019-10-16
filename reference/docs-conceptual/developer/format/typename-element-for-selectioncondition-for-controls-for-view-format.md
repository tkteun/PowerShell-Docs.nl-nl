---
title: TypeName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353541"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a>Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy for Controls ( Format) TypeName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekst waarde

Geef de volledig gekwalificeerde naam van het .NET-type op, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
