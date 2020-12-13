---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TableColumnHeader (opmaak)
description: Het element TableColumnHeader (opmaak)
ms.openlocfilehash: 30368512875b7c5c4cf3c686f3d09540dea1bd26
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651532"
---
# <a name="tablecolumnheader-element-format"></a>Het element TableColumnHeader (opmaak)

Hiermee definieert u het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (indeling)

## <a name="syntax"></a>Syntax

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TableColumnHeader` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Label element voor TableColumnHeader voor TableControl (indeling)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee wordt het label gedefinieerd dat boven aan de kolom wordt weer gegeven. Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.|
|[Het element Breedte voor TableColumnHeader voor TableControl (opmaak)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Vereist element.<br /><br /> Geeft de breedte van de kolom aan (in tekens).|
|[Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee wordt aangegeven hoe het label van de kolom wordt weer gegeven. Als er geen uitlijning is opgegeven, wordt het label links uitgelijnd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element TableHeaders (opmaak)](./tableheaders-element-format.md)|Hiermee worden de kolommen van een tabel weergave gedefinieerd.|

## <a name="remarks"></a>Opmerkingen

Geef een koptekst op voor elke kolom van de tabel. De kolommen worden weer gegeven in de volg orde waarin de `TableColumnHeader` elementen zijn gedefinieerd.

Een tabel moet hetzelfde aantal `TableColumnHeader` elementen als `TableRowEntry` elementen hebben. De kolomkop geeft aan hoe de tekst boven aan de tabel wordt weer gegeven. De rij-items bepalen welke gegevens in de rijen van de tabel worden weer gegeven.

Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u twee `TableColumnHeader` elementen. Het eerste element definieert een kolom waarvan het label kolom 1, een breedte van 16 tekens en waarvan het label aan de linkerkant wordt uitgelijnd. Het tweede element definieert een kolom waarvan het label kolom 2 is, heeft een breedte van 10 tekens en waarvan het label in de kolom is gecentreerd.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Zie ook

[Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Een tabelweergave maken](./creating-a-table-view.md)

[Het element Label voor TableColumnHeader voor TableControl (opmaak)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableHeaders-element voor TableControl (indeling)](./tableheaders-element-format.md)

[Breedte voor TableColumnHeader voor het TableControl-element (indeling)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
