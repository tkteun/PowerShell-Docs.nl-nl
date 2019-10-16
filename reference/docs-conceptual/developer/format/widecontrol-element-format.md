---
title: WideControl-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358706"
---
# <a name="widecontrol-element-format"></a>Het element WideControl (opmaak)

Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave. In deze weer gave wordt één eigenschaps waarde of script waarde voor elk object weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl-element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `WideControl` beschreven. U kunt de elementen `AutoSize` en `ColumnNumber` niet tegelijk opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element AutoSize voor WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.|
|[ColumnNumber-element voor WideControl (indeling)](./columnnumber-element-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal kolommen op dat wordt weer gegeven in de brede weer gave.|
|[WideEntries-element (indeling)](./wideentries-element-for-widecontrol-format.md)|Vereist element.<br /><br /> Biedt de definities van de brede weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element weer geven (indeling)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Bij het definiëren van een brede weer gave kunt u het element `AutoSize` of de `ColumnNumber` toevoegen, maar u kunt niet beide toevoegen.

In de meeste gevallen is er slechts één definitie vereist voor elke brede weer gave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.

Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `WideControl`-element dat wordt gebruikt om een eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.

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

Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Het element AutoSize voor WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[ColumnNumber-element voor WideControl (indeling)](./columnnumber-element-for-widecontrol-format.md)

[Element weer geven (indeling)](./view-element-format.md)

[WideEntries-element (indeling)](./wideentries-element-for-widecontrol-format.md)

[Brede weer gave (basis)](./wide-view-basic.md)

[Een brede weer gave maken](./creating-a-wide-view.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
