---
title: TableControl-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848851"
---
# <a name="tablecontrol-element-format"></a>Het element TableControl (opmaak)

Hiermee definieert u een tabelindeling voor een weergave.

ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl Element (indeling)

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

De volgende secties worden de kenmerken en onderliggende elementen bovenliggend element van de `TableControl` element. U moet de rijen van de tabel opgeven. Alle onderliggende elementen zijn optioneel.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[AutoSize-Element voor TableControl (indeling)](./autosize-element-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.|
|[HideTableHeaders-Element voor TableControl (indeling)](./hidetableheaders-element-format.md)|Optioneel element.<br /><br /> Geeft aan of de header van de tabel niet wordt weergegeven.|
|[TableHeaders-Element voor TableControl (indeling)](./tableheaders-element-format.md)|Vereist element.<br /><br /> Definieert de labels, de breedte en de uitlijning van de gegevens voor de kolommen van de tabelweergave.|
|[TableRowEntries-Element voor TableCotrol (indeling)](./tablerowentries-element-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Bevat de definities van de tabelweergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave die wordt gebruikt om de leden van een of meer objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `TableControl` element dat wordt gebruikt om weer te geven van de eigenschappen van de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.

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

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Weergave-Element (indeling)](./view-element-format.md)

[AutoSize-Element voor TableControl (indeling)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders-Element (indeling)](./hidetableheaders-element-format.md)

[TableHeaders-Element (indeling)](./tableheaders-element-format.md)

[TableRowEntries Element (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
