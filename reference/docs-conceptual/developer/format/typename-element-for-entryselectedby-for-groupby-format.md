---
title: TypeName-element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353590"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)

Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het aangepaste besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (indeling) EntrySelectedBy voor CustomEntry voor het element GroupBy (Format) voor EntrySelectedBy voor GroupBy (indeling)

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
|[EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|

## <a name="text-value"></a>Tekst waarde

Geef de volledig gekwalificeerde naam van het .NET-type op, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

Voor elke controle definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over de onderdelen van een aangepaste beheer weergave.

## <a name="see-also"></a>Zie ook

[Aangepaste besturings elementen maken](./creating-custom-controls.md)

[EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
