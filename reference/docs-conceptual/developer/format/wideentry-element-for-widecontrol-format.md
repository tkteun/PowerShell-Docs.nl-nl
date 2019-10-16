---
title: WideEntry-element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353156"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Het element WideEntry voor WideControl (opmaak)

Biedt een definitie van de brede weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `WideEntry` beschreven. U moet één onderliggend `WideItem`-element opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[EntrySelectedBy-element voor WideEntry (indeling)](./entryselectedby-element-for-wideentry-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie voor grote vermeldingen of de voor waarde die voor deze definitie moet worden gebruikt.|
|[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md)|Vereist element.<br /><br /> Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[WideEntries-element (indeling)](./wideentries-element-for-widecontrol-format.md)|Biedt de definities van de brede weer gave.|

## <a name="remarks"></a>Opmerkingen

Een brede weer gave is een lijst indeling waarin één eigenschaps waarde of script waarde voor elk object wordt weer gegeven. In tegens telling tot andere typen weer gaven kunt u slechts één item element voor elke weergave definitie opgeven. Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de andere onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `WideEntry`-element dat één `WideItem`-element definieert. Het element `WideItem` definieert de eigenschap waarvan de waarde wordt weer gegeven in de weer gave.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Een brede weer gave maken](./creating-a-wide-view.md)

[SelectionCondition-element voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-element voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-element voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries-element (indeling)](./wideentries-element-for-widecontrol-format.md)

[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
