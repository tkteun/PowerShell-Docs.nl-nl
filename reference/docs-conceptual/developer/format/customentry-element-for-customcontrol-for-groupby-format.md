---
title: CustomEntry-element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4df8e5b96868b3814c6d84fa329950bb5345ef6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785911"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Het element CustomEntry voor CustomControl voor GroupBy (opmaak)

Biedt een definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor GroupBy (Format) CustomEntry-element voor het object GroupBy (indeling)

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
|[Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|
|[Het element CustomItem voor CustomEntry voor GroupBy (opmaak)](./customitem-element-for-customentry-for-groupby-format.md)|Vereist element.<br /><br /> Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntries voor CustomControl voor GroupBy (opmaak)](./customentries-element-for-customcontrol-for-groupby-format.md)|Bevat de definities voor het besturings element.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Het element EntrySelectedBy voor CustomEntry voor GroupBy (opmaak)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Het element CustomItem voor CustomEntry voor GroupBy (opmaak)](./customitem-element-for-customentry-for-groupby-format.md)

[Het element CustomEntries voor CustomControl voor GroupBy (opmaak)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
