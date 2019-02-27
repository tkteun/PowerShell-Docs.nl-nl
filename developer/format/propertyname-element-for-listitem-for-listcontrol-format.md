---
title: PropertyName-Element voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846625"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>Het element PropertyName voor ListItem voor ListControl (opmaak)

Hiermee geeft u de .NET-eigenschap waarvan de waarde wordt weergegeven in de lijst.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) ListItems Element (indeling) ListItem-Element (indeling) PropertyName-Element voor ListItem (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de rij van de lijstweergave.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de eigenschap waarvan de waarde wordt weergegeven.

## <a name="remarks"></a>Opmerkingen

Wanneer dit element is opgegeven, wordt u niet opgeven de [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.

Naast de waarde van de eigenschap weer te geven, kunt u ook een label voor de waarde of een opmaaktekenreeks die kan worden gebruikt voor het wijzigen van de weergave van de waarde opgeven. Zie voor meer informatie over het opgeven van gegevens in een lijst weergeven [het maken van een lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u het label en de eigenschap waarvan de waarde wordt weergegeven.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[ScriptBlock-Element voor ListItem voor ListControl (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Lijstitem-Element voor ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
