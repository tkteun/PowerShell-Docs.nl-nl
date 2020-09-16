---
title: TypeName-element voor SelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 28409604b8905440890161f66981264748bc2c33
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785061"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a>Het element TypeName voor SelectionCondition voor CustomControl voor Weergave (opmaak)

Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (Format) CustomControl element voor weer gave (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor het object CustomControl voor weer gave (Format) voor SelectionCondition

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
|[SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
