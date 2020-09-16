---
title: TableControl-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 34e20006a7501650f2a22f71a3d7e999fb8b2337
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785129"
---
# <a name="tablecontrol-element-format"></a>Het element TableControl (opmaak)

Definieert een tabel indeling voor een weer gave.

ViewDefinitions element (indeling) element weer geven (indeling) TableControl-element (indeling)

## <a name="syntax"></a>Syntax

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TableControl` element beschreven. U moet de rijen van de tabel opgeven. Alle onderliggende elementen zijn optioneel.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element AutoSize voor TableControl (opmaak)](./autosize-element-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.|
|[HideTableHeaders-element voor TableControl (indeling)](./hidetableheaders-element-format.md)|Optioneel element.<br /><br /> Hiermee wordt aangegeven of de koptekst van de tabel niet wordt weer gegeven.|
|[TableHeaders-element voor TableControl (indeling)](./tableheaders-element-format.md)|Vereist element.<br /><br /> Hiermee worden de labels, de breedten en de uitlijning van de gegevens voor de kolommen van de tabel weergave gedefinieerd.|
|[Het element TableRowEntries voor TableControl (opmaak)](./tablerowentries-element-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Biedt de definities van de tabel weergave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer objecten weer te geven.|

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een- `TableControl` element dat wordt gebruikt om de eigenschappen van het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) weer te geven.

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

[Een tabelweergave maken](./creating-a-table-view.md)

[Het element Weergave (opmaak)](./view-element-format.md)

[Het element AutoSize voor TableControl (opmaak)](./autosize-element-for-tablecontrol-format.md)

[Het element HideTableHeaders (opmaak)](./hidetableheaders-element-format.md)

[Het element TableHeaders (opmaak)](./tableheaders-element-format.md)

[TableRowEntries-element (indeling)](./tablerowentries-element-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
