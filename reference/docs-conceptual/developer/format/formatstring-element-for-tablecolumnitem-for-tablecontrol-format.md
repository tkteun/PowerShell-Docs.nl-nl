---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FormatString voor TableColumnItem voor TableControl (opmaak)
description: Het element FormatString voor TableColumnItem voor TableControl (opmaak)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667892"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>Het element FormatString voor TableColumnItem voor TableControl (opmaak)

Hiermee geeft u een indelings patroon op dat definieert hoe de eigenschap of script waarde van de tabel wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) TableColumnItems element (indeling) TableColumnItem element (opmaak) formats element voor TableColumnItem (indeling)

## <a name="syntax"></a>Syntax

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `FormatString` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnItem-element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.|

## <a name="text-value"></a>Tekstwaarde

Geef het patroon op dat wordt gebruikt om de gegevens op te maken. Dit patroon kan bijvoorbeeld worden gebruikt voor het opmaken van de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm}.

## <a name="remarks"></a>Opmerkingen

Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven. Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).

Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Zie ook

[Een tabelweergave maken](./creating-a-table-view.md)

[Weergegeven gegevens opmaken](./formatting-displayed-data.md)

[TableColumnItem-element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
