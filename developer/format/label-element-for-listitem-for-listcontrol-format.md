---
title: Element een label voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845953"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Het element Label voor ListItem voor ListControl (opmaak)

Hiermee geeft u het label dat wordt weergegeven aan de linkerkant van de waarde voor eigenschap of het script in de rij.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListItems voor ListEntry voor ListControl Element (ListControl (indeling) -Indeling) ListItem Element voor ListItems voor ListControl (indeling) Label-Element voor ListItem voor ListControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Label` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Lijstitem-Element voor ListItems voor ListControl (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.|

## <a name="text-value"></a>Tekstwaarde

Geef het label om te worden weergegeven aan de linkerkant van de waarde voor eigenschap of script.

## <a name="remarks"></a>Opmerkingen

Als een label niet opgegeven is, wordt de naam van de eigenschap of het script wordt weergegeven. Zie voor meer informatie over het gebruik van de labels in een lijst weergeven [het maken van een lijstweergave](./creating-a-list-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u een label toevoegen aan een rij.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Zie ook

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[ListItem Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
