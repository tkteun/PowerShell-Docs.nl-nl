---
title: PropertyName-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354087"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>Het element PropertyName voor ListItem voor ListControl (opmaak)

Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de lijst.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl-element (indeling) element (indeling) List item (Format) element (notatie) List items element (Format) lijst item element (indeling) eigenschap naam Lijst item (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de rij van de lijst weergave.|

## <a name="text-value"></a>Tekst waarde

Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.

## <a name="remarks"></a>Opmerkingen

Als dit element is opgegeven, kunt u het [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -element niet opgeven.

Naast het weer geven van de eigenschaps waarde, kunt u ook een label opgeven voor de waarde of een opmaak teken reeks die kan worden gebruikt om de weer gave van de waarde te wijzigen. Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het opgeven van gegevens in een lijst weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u het label en de eigenschap opgeeft waarvan de waarde wordt weer gegeven.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[Script block-element voor lijst item voor ListControl (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Een lijst weergave maken](./creating-a-list-view.md)

[Lijst item-element voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
