---
title: WideControl-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849488"
---
# <a name="widecontrol-element-format"></a>Het element WideControl (opmaak)

Definieert een breed (één waarde) lijstweergave voor de weergave. Deze weergave bevat een waarde van één eigenschap of een Scriptwaarde voor elk object.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) WideControl Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `WideControl` element. U kunt geen opgeven de `AutoSize` en `ColumnNumber` elementen op hetzelfde moment.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[AutoSize-Element voor WideControl (indeling)](./autosize-element-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.|
|[ColumnNumber-Element voor WideControl (indeling)](./columnnumber-element-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal kolommen in de brede weergave.|
|[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)|Vereist element.<br /><br /> Bevat de definities van de brede weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave die wordt gebruikt om een of meer .NET-objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Bij het definiëren van een brede weergave, kunt u toevoegen de `AutoSize` element of de `ColumnNumber` , maar u kunt beide niet toevoegen.

In de meeste gevallen slechts één definitie is vereist voor elke brede weergave, maar het is mogelijk dat meerdere definities als u wilt de dezelfde weergave gebruiken om verschillende .NET-objecten weer te geven. In deze gevallen kunt u de definitie van een afzonderlijke voor elk object of een set van objecten opgeven.

Zie voor meer informatie over de onderdelen van een brede weergave [brede weergave onderdelen](./creating-a-wide-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `WideControl` element dat wordt gebruikt om weer te geven van een eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).

## <a name="see-also"></a>Zie ook

[AutoSize-Element voor WideControl (indeling)](./autosize-element-for-widecontrol-format.md)

[ColumnNumber-Element voor WideControl (indeling)](./columnnumber-element-for-widecontrol-format.md)

[Weergave-Element (indeling)](./view-element-format.md)

[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)

[Brede weergave (basis)](./wide-view-basic.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
