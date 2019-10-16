---
title: TableControl-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358793"
---
# <a name="tablecontrol-element-format"></a>Het element TableControl (opmaak)

Definieert een tabel indeling voor een weer gave.

ViewDefinitions element (indeling) element weer geven (indeling) TableControl-element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TableControl` beschreven. U moet de rijen van de tabel opgeven. Alle onderliggende elementen zijn optioneel.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element AutoSize voor TableControl (Format)](./autosize-element-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.|
|[HideTableHeaders-element voor TableControl (indeling)](./hidetableheaders-element-format.md)|Optioneel element.<br /><br /> Hiermee wordt aangegeven of de koptekst van de tabel niet wordt weer gegeven.|
|[TableHeaders-element voor TableControl (indeling)](./tableheaders-element-format.md)|Vereist element.<br /><br /> Hiermee worden de labels, de breedten en de uitlijning van de gegevens voor de kolommen van de tabel weergave gedefinieerd.|
|[TableRowEntries-element voor TableControl (indeling)](./tablerowentries-element-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Biedt de definities van de tabel weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element weer geven (indeling)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `TableControl`-element dat wordt gebruikt om de eigenschappen van het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) weer te geven.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Zie ook

[Een tabel weergave maken](./creating-a-table-view.md)

[Element weer geven (indeling)](./view-element-format.md)

[Het element AutoSize voor TableControl (Format)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders-element (indeling)](./hidetableheaders-element-format.md)

[TableHeaders-element (indeling)](./tableheaders-element-format.md)

[TableRowEntries-element (indeling)](./tablerowentries-element-for-tablecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
