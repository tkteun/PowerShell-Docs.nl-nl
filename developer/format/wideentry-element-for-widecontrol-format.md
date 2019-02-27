---
title: WideEntry-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847178"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Het element WideEntry voor WideControl (opmaak)

Bevat een definitie van de brede weergave.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `WideEntry` element. U moet een enkel `WideItem` onderliggend element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor WideEntry (indeling)](./entryselectedby-element-for-wideentry-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie breed vermelding of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.|
|[WideItem-Element (indeling)](./wideitem-element-for-widecontrol-format.md)|Vereist element.<br /><br /> Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)|Bevat de definities van de brede weergave.|

## <a name="remarks"></a>Opmerkingen

Een brede weergave wordt een lijst met-indeling die een waarde van één eigenschap of Scriptwaarde voor elk object wordt weergegeven. In tegenstelling tot andere typen weergaven, kunt u slechts één itemelement voor de weergavedefinitie van elke opgeven. Zie voor meer informatie over de andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `WideEntry` element waarin één `WideItem` element. De `WideItem` element wordt gedefinieerd voor de eigenschap waarvan de waarde wordt weergegeven in de weergave.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).

## <a name="see-also"></a>Zie ook

[Het maken van een brede weergave](./creating-a-wide-view.md)

[SelectionCondition-Element voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-Element voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-Element voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)

[WideItem-Element (indeling)](./wideitem-element-for-widecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
