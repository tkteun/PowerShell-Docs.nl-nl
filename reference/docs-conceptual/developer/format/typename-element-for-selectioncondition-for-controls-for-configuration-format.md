---
title: TypeName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2db856d1b84dded315204d8c8574ae86acb63515
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780063"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)

Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control-element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het beheer van de configuratie (Format) CustomEntry-element voor het EntrySelectedBy-element voor het configureren van de configuratie (indeling) voor CustomEntry voor besturings elementen voor de configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor de configuratie (indeling) TypeName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)

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
|[SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor configuratie (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor configuratie (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
