---
title: DefaultSettings-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355130"
---
# <a name="defaultsettings-element-format"></a>Het element DefaultSettings (opmaak)

Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand. Algemene instellingen zijn onder meer het weer geven van fouten, tekst terugloop in tabellen, definiëren hoe verzamelingen worden uitgevouwen en meer.

Configuratie-element (indeling) DefaultSettings element (indeling)

## <a name="syntax"></a>Syntaxis

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

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `DefaultSettings` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Display error-element (indeling)](./displayerror-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.|
|[EnumerableExpansions-element (indeling)](./enumerableexpansions-element-format.md)|Optioneel element.<br /><br /> Definieert de verschillende manieren waarop .NET-objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.|
|[PropertyCountForTable (indeling)](./propertycountfortable-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het minimum aantal eigenschappen op dat een object moet hebben om het object weer te geven in een tabel weergave.|
|[Show Error-element (indeling)](./showerror-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de volledige fout record wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.|
|[WrapTables-element (indeling)](./wraptables-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de gegevens in een tabel naar de volgende regel worden verplaatst als deze niet in de kolom breedte passen.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Configuratie-element](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Configuratie-element](./configuration-element-format.md)

[Display error-element (indeling)](./displayerror-element-format.md)

[EnumerableExpansions-element (indeling)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (indeling)](./propertycountfortable-element-format.md)

[Show Error-element (indeling)](./showerror-element-format.md)

[WrapTables-element (indeling)](./wraptables-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
