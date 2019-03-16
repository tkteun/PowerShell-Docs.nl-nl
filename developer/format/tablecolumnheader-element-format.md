---
title: TableColumnHeader-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057872"
---
# <a name="tablecolumnheader-element-format"></a>Het element TableColumnHeader (opmaak)

Het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel definieert.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders Element voor TableControl (indeling) TableColumnHeader-Element voor TableHeaders voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TableColumnHeader` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Label-Element voor TableColumnHeader voor TableControl (indeling)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee definieert u het label dat wordt weergegeven aan de bovenkant van de kolom. Als u geen naam opgeeft, wordt de naam van de eigenschap waarvan de waarde wordt weergegeven in de rijen gebruikt.|
|[Breedte van Element voor TableColumnHeader voor TableControl (indeling)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Vereist element.<br /><br /> Geeft de breedte (in tekens) van de kolom.|
|[Uitlijning-Element voor TableColumnHeader voor TableControl (indeling)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op hoe het label van de kolom wordt weergegeven. Als er geen uitlijning is opgegeven, wordt het label links uitgelijnd.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableHeaders-Element (indeling)](./tableheaders-element-format.md)|Hiermee definieert u de kolommen van een tabelweergave.|

## <a name="remarks"></a>Opmerkingen

Hiermee geeft u een koptekst voor elke kolom van de tabel. De kolommen worden weergegeven in de volgorde waarin de `TableColumnHeader` elementen worden gedefinieerd.

Een tabel moet hetzelfde aantal `TableColumnHeader` elementen als `TableRowEntry` elementen. De kolomkop wordt gedefinieerd hoe de tekst boven aan de tabel wordt weergegeven. De rij-vermeldingen definiëren welke gegevens worden weergegeven in de rijen van de tabel.

Zie voor meer informatie over de onderdelen van een tabelweergave [tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u twee `TableColumnHeader` elementen. Het eerste element definieert een kolom waarvan de label 'Kolom 1' is, een breedte van 16 tekens heeft en waarvan de label aan de linkerkant is uitgelijnd. Het tweede element definieert een kolom waarvan de label "Kolom 2" is, een breedte van 10 tekens heeft en waarvan de label in de kolom wordt gecentreerd.

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

[Uitlijning-Element voor TableColumnHeader voor TableControl (indeling)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Label-Element voor TableColumnHeader voor TableControl (indeling)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableHeaders-Element voor TableControl (indeling)](./tableheaders-element-format.md)

[Breedte voor TableColumnHeader voor TableControl-Element (indeling)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
