---
title: Element GroupBy voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354962"
---
# <a name="groupby-element-for-view-format"></a>Het element GroupBy voor Weergave (opmaak)

Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (indeling)

## <a name="syntax"></a>Syntaxis

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
|[CustomControl-element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee definieert u het aangepaste besturings element waarmee nieuwe groepen worden weer gegeven.|
|[CustomControlName-element voor GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een besturings element dat wordt gebruikt om de nieuwe groep weer te geven.|
|[Label element voor GroupBy (indeling)](./label-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.|
|[PropertyName-element voor GroupBy (indeling)](./propertyname-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde wordt gewijzigd.|
|[Script block-element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element weer geven (indeling)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd waarin een of meer .NET-objecten worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

Wanneer u definieert hoe een nieuwe groep objecten wordt weer gegeven, moet u de eigenschap of het script opgeven waarmee de nieuwe groep wordt gestart. u kunt echter niet beide opgeven.

## <a name="see-also"></a>Zie ook

[CustomControlName-element voor GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md)

[Label element voor GroupBy (indeling)](./label-element-for-groupby-format.md)

[PropertyName-element voor GroupBy (indeling)](./propertyname-element-for-groupby-format.md)

[Script block-element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md)

[Element weer geven (indeling)](./view-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
