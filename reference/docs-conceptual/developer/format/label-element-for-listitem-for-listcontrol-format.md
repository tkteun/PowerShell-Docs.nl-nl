---
title: Element label voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354444"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Het element Label voor ListItem voor ListControl (opmaak)

Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) List item voor ListControl (indeling) Format) lijst item-element voor list items voor ListControl (Format) label-element voor lijst item voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Label` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Lijst item-element voor list items voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.|

## <a name="text-value"></a>Tekst waarde

Geef het label op dat links van de eigenschap of script waarde moet worden weer gegeven.

## <a name="remarks"></a>Opmerkingen

Als er geen label is opgegeven, wordt de naam van de eigenschap of het script weer gegeven. Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van labels in een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een label aan een rij toevoegt.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[Een lijst weergave maken](./creating-a-list-view.md)

[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
