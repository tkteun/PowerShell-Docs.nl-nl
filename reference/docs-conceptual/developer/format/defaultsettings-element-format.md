---
ms.date: 09/13/2016
ms.topic: reference
title: Het element DefaultSettings (opmaak)
description: Het element DefaultSettings (opmaak)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666719"
---
# <a name="defaultsettings-element-format"></a>Het element DefaultSettings (opmaak)

Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand. Algemene instellingen zijn onder meer het weer geven van fouten, tekst terugloop in tabellen, definiëren hoe verzamelingen worden uitgevouwen en meer.

Configuratie-element (indeling) DefaultSettings element (indeling)

## <a name="syntax"></a>Syntax

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `DefaultSettings` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element DisplayError (opmaak)](./displayerror-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.|
|[Het element EnumerableExpansions (opmaak)](./enumerableexpansions-element-format.md)|Optioneel element.<br /><br /> Definieert de verschillende manieren waarop .NET-objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|
|[PropertyCountForTable (indeling)](./propertycountfortable-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het minimum aantal eigenschappen op dat een object moet hebben om het object weer te geven in een tabel weergave.|
|[Het element ShowError (opmaak)](./showerror-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de volledige fout record wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.|
|[Het element WrapTables (opmaak)](./wraptables-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de gegevens in een tabel naar de volgende regel worden verplaatst als deze niet in de kolom breedte passen.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Configuratie-element](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Configuratie-element](./configuration-element-format.md)

[Het element DisplayError (opmaak)](./displayerror-element-format.md)

[Het element EnumerableExpansions (opmaak)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (indeling)](./propertycountfortable-element-format.md)

[Het element ShowError (opmaak)](./showerror-element-format.md)

[Het element WrapTables (opmaak)](./wraptables-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
