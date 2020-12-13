---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
description: Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: fadcdb69ac71269ba2f2f80baf139bb363d4acba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666668"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)

Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) EntrySelectedBy

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van de algemene controle definitie.|
|[Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het gemeen schappelijke besturings element.|
|[Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het algemene besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Biedt een definitie van het algemene besturings element.|

## <a name="remarks"></a>Opmerkingen

Elke definitie moet mini maal één .NET-type,-selectieset of-selectie voorwaarde hebben opgegeven. Er is geen maximum limiet voor het aantal typen, de selectie sets of de selectie voorwaarden die u kunt opgeven.

## <a name="see-also"></a>Zie ook

[Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Het element TypeName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
