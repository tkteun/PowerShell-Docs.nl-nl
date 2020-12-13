---
ms.date: 09/13/2016
ms.topic: reference
title: Het element GroupBy voor Weergave (opmaak)
description: Het element GroupBy voor Weergave (opmaak)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652101"
---
# <a name="groupby-element-for-view-format"></a>Het element GroupBy voor Weergave (opmaak)

Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (indeling)

## <a name="syntax"></a>Syntax

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomControl voor GroupBy (opmaak)](./customcontrol-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u het aangepaste besturings element waarmee nieuwe groepen worden weer gegeven.|
|[Het element CustomControlName voor GroupBy (opmaak)](./customcontrolname-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een besturings element dat wordt gebruikt om de nieuwe groep weer te geven.|
|[Het element Label voor GroupBy (opmaak)](./label-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.|
|[Het element PropertyName voor GroupBy (opmaak)](./propertyname-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde wordt gewijzigd.|
|[Het element ScriptBlock voor GroupBy (opmaak)](./scriptblock-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Wanneer u definieert hoe een nieuwe groep objecten wordt weer gegeven, moet u de eigenschap of het script opgeven waarmee de nieuwe groep wordt gestart. u kunt echter niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Het element CustomControlName voor GroupBy (opmaak)](./customcontrolname-element-for-groupby-format.md)

[Het element Label voor GroupBy (opmaak)](./label-element-for-groupby-format.md)

[Het element PropertyName voor GroupBy (opmaak)](./propertyname-element-for-groupby-format.md)

[Het element ScriptBlock voor GroupBy (opmaak)](./scriptblock-element-for-groupby-format.md)

[Het element Weergave (opmaak)](./view-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
