---
title: WideControl-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b6f19cf94dcb440eeaf53547db407287e5462520
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784976"
---
# <a name="widecontrol-element-format"></a>Het element WideControl (opmaak)

Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave. In deze weer gave wordt één eigenschaps waarde of script waarde voor elk object weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl-element (indeling)

## <a name="syntax"></a>Syntax

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideControl` element beschreven. U kunt de `AutoSize` elementen en niet `ColumnNumber` tegelijkertijd opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element AutoSize voor WideControl (opmaak)](./autosize-element-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.|
|[Het element ColumnNumber voor WideControl (opmaak)](./columnnumber-element-for-widecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het aantal kolommen op dat wordt weer gegeven in de brede weer gave.|
|[WideEntries-element (indeling)](./wideentries-element-for-widecontrol-format.md)|Vereist element.<br /><br /> Biedt de definities van de brede weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Bij het definiëren van een brede weer gave kunt u het `AutoSize` element toevoegen of het, `ColumnNumber` maar u kunt niet beide toevoegen.

In de meeste gevallen is er slechts één definitie vereist voor elke brede weer gave, maar het is mogelijk om meerdere definities te hebben als u dezelfde weer gave wilt gebruiken om verschillende .NET-objecten weer te geven. In dergelijke gevallen kunt u een afzonderlijke definitie opgeven voor elk object of set met objecten.

Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `WideControl` element dat wordt gebruikt om een eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.

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

[Het element ColumnNumber voor WideControl (opmaak)](./columnnumber-element-for-widecontrol-format.md)

[Het element Weergave (opmaak)](./view-element-format.md)

[WideEntries-element (indeling)](./wideentries-element-for-widecontrol-format.md)

[Brede weergave (Basis)](./wide-view-basic.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
