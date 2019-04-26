---
title: FormatString-Element voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065618"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>Het element FormatString voor TableColumnItem voor TableControl (opmaak)

Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script van de tabel wordt weergegeven.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) TableColumnItems-Element (indeling) TableColumnItem-Element (indeling) FormatString-Element voor TableColumnItem (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `FormatString` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnItem-Element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.|

## <a name="text-value"></a>Tekstwaarde

Geef het patroon dat wordt gebruikt om de opmaak van de gegevens. Dit patroon kan bijvoorbeeld worden gebruikt om de waarde van elke eigenschap die is van het type [System.DateTime](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Opmerkingen

Opmaaktekenreeksen kunnen worden gebruikt bij het maken van tabelweergaven, lijst met weergaven, breed weergaven of aangepaste weergaven. Zie voor meer informatie over het opmaken van een waarde die wordt weergegeven in een weergave [weergegeven gegevens opmaak](./formatting-displayed-data.md).

Zie voor meer informatie over de onderdelen van een tabelweergave [tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Opmaak gegevens weergegeven](./formatting-displayed-data.md)

[TableColumnItem-Element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
