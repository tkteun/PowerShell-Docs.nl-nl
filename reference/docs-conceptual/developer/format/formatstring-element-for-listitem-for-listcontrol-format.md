---
ms.date: 09/13/2016
ms.topic: reference
title: Het element FormatString voor ListItem voor ListControl (opmaak)
description: Het element FormatString voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 1c16da92928ea632241942f4f2c63390c4fea706
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667909"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>Het element FormatString voor ListItem voor ListControl (opmaak)

Geeft een opmaak patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) List item voor ListControl (Format) element Entry List voor ListControl (Format) List items element voor ListControl (Format) lijst item element voor ListControl (Format) formats-element voor ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `FormatString` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef het patroon op dat wordt gebruikt om de gegevens op te maken. U kunt dit patroon bijvoorbeeld gebruiken om de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm} in te delen.

## <a name="remarks"></a>Opmerkingen

Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven. Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).

Zie [lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van opmaak teken reeksen in lijst weergaven.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
