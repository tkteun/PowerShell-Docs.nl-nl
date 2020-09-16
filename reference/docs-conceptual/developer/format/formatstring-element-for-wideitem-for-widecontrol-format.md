---
title: Element formats Tring voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4f1f0826a1cebb1526858875df640baac9d4ce48
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781525"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>Het element FormatString voor WideItem voor WideControl (opmaak)

Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element voor WideControl (Format) WideItem-element voor WideControl (Format) voor WideItem-element voor WideControl (Format)

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
|[Het element WideItem voor WideControl (opmaak)](./wideitem-element-for-widecontrol-format.md)|Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef het patroon op dat wordt gebruikt om de gegevens op te maken. U kunt dit patroon bijvoorbeeld gebruiken om de waarde van een eigenschap van het type [System. time span](/dotnet/api/System.TimeSpan): {0: mmm} {0: dd} {0: uu}: {0: mm} in te delen.

## <a name="remarks"></a>Opmerkingen

Opmaak teken reeksen kunnen worden gebruikt bij het maken van tabel weergaven, lijst weergaven, brede weer gaven of aangepaste weer gaven. Zie voor meer informatie over het opmaken van een waarde die wordt weer gegeven in een weer gave, [weer gegeven gegevens opmaken](./formatting-displayed-data.md).

Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over het gebruik van opmaak reeksen in brede weer gaven.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Zie ook

[Een brede weergave maken](./creating-a-wide-view.md)

[Het element WideItem voor WideControl (opmaak)](./wideitem-element-for-widecontrol-format.md)

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
