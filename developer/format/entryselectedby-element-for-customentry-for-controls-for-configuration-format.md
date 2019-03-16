---
title: EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059215"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u de .NET-typen die gebruikmaken van de definitie van de algemene controle of de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)

## <a name="syntax"></a>Syntaxis

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet aanwezig zijn voor de definitie van de algemene controle moet worden gebruikt.|
|[SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van de algemene besturingselementen.|
|[TypeName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van de algemene besturingselementen.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Bevat een definitie van de algemene besturingselementen.|

## <a name="remarks"></a>Opmerkingen

Ten minste hebt elke definitie ten minste één .NET-type, selectie instellen of selectievoorwaarde die is opgegeven. Er is geen maximale limiet voor het aantal typen, sets selecteren of selectie voorwaarden die u kunt opgeven.

## <a name="see-also"></a>Zie ook

[SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[TypeName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
