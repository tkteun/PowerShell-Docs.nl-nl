---
title: TypeName-element voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353562"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)

Hiermee geeft u een .NET-type op dat gebruikmaakt van dit item van de tabel weergave. Er is geen limiet voor het aantal typen dat voor een tabel vermelding kan worden opgegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling) element-TypeName voor EntrySelectedBy voor TableRowEntry (indeling)

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
|[EntrySelectedBy-element (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van dit item of de voor waarde die voor deze vermelding moet worden gebruikt.|

## <a name="text-value"></a>Tekst waarde

Geef de naam van het .NET-type op.

## <a name="remarks"></a>Opmerkingen

Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="see-also"></a>Zie ook

[Een tabel weergave maken](./creating-a-table-view.md)

[EntrySelectedBy-element (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
