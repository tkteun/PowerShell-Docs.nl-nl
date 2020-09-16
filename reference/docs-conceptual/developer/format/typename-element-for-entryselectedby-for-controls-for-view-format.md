---
title: TypeName-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6eaa4f80a18c91ca351657fd40a8cac6f688c22f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783327"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-view-format"></a>Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)

Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) Controls-element (opmaak) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor object voor weer gave (Format) voor de besturings elementen voor de weer gave (Format)-element voor EntrySelectedBy

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
|[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
