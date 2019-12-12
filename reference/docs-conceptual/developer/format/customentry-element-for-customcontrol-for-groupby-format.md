---
title: CustomEntry-element voor CustomControl voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355263"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Het element CustomEntry voor CustomControl voor GroupBy (opmaak)

Biedt een definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `CustomEntry` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.|
|[CustomItem-element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)|Vereist element.<br /><br /> Hiermee wordt gedefinieerd hoe de gegevens worden weer gegeven in het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntries-element voor CustomControl voor GroupBy (indeling)](./customentries-element-for-customcontrol-for-groupby-format.md)|Bevat de definities voor het besturings element.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[CustomItem-element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md)

[CustomEntries-element voor CustomControl voor GroupBy (indeling)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
