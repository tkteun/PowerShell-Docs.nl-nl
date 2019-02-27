---
title: SelectionSetName-Element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848445"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Het element SelectionSetName voor ViewSelectedBy (opmaak)

Hiermee geeft u een set van .NET-objecten die worden weergegeven in de weergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ViewSelectedBy-Element (indeling) SelectionSetName Element voor ViewSelectedBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ViewSelectedBy-Element (indeling)](./viewselectedby-element-format.md)|Hiermee definieert u de .NET-objecten die worden weergegeven in de weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de van selectieset die wordt gedefinieerd door de `Name` -element voor de selectieset.

## <a name="remarks"></a>Opmerkingen

U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt. Zie voor meer informatie over het definiëren en verwijst naar een selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u een selectie instellen voor een lijst weergeven. Hetzelfde schema wordt gebruikt voor de tabel, breed en aangepaste weergaven.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[Selectiesets definiëren](./defining-selection-sets.md)

[ViewSelectedBy-Element (indeling)](./viewselectedby-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
