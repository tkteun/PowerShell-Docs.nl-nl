---
title: EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359003"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)

Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (Format) EntrySelectedBy element voor CustomEntry voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van de algemene controle definitie.|
|[SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het gemeen schappelijke besturings element.|
|[TypeName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het algemene besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Biedt een definitie van het algemene besturings element.|

## <a name="remarks"></a>Opmerkingen

Elke definitie moet mini maal één .NET-type,-selectieset of-selectie voorwaarde hebben opgegeven. Er is geen maximum limiet voor het aantal typen, de selectie sets of de selectie voorwaarden die u kunt opgeven.

## <a name="see-also"></a>Zie ook

[SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[TypeName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
