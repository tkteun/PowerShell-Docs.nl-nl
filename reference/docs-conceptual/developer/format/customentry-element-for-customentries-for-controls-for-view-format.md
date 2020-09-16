---
title: CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785894"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)

Biedt een definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Element van het configuratie-element (indeling) ViewDefinitions element (indeling) besturings element element (indeling) Controls-element (Format) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor Controls voor Controls (Format) CustomEntries element voor de weer gave van besturings elementen (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `CustomEntry` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|
|[Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Vereist element.<br /><br /> Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntries voor CustomControl voor Weergave (opmaak)](./customentries-element-for-customcontrol-for-view-format.md)|Bevat de definities voor het besturings element.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Het element CustomEntries voor CustomControl voor Weergave (opmaak)](./customentries-element-for-customcontrol-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
