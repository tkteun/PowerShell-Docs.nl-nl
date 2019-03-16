---
title: DefaultSettings-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059062"
---
# <a name="defaultsettings-element-format"></a>Het element DefaultSettings (opmaak)

Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert. Algemene instellingen omvatten weergeven van fouten, tekstterugloop in tabellen, definiëren hoe verzamelingen zijn uitgevouwen, en meer.

Configuratie-Element (indeling)-DefaultSettings Element (indeling)

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

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `DefaultSettings` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[DisplayError-Element (indeling)](./displayerror-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de tekenreeks #ERR wordt weergegeven wanneer een fout optreedt bij het weergeven van een hoeveelheid gegevens.|
|[EnumerableExpansions-Element (indeling)](./enumerableexpansions-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de verschillende manieren waarop .NET-worden uitgevouwen objecten wanneer ze worden weergegeven in een weergave.|
|[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het minimum aantal eigenschappen die een object hebben moet om het object in een tabel weer te geven.|
|[ShowError Element (indeling)](./showerror-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de volledige foutrecord wordt weergegeven wanneer een fout optreedt bij het weergeven van een hoeveelheid gegevens.|
|[WrapTables-Element (indeling)](./wraptables-element-format.md)|Optioneel element.<br /><br /> Hiermee geeft u op dat de gegevens in een tabel is verplaatst naar de volgende regel als niet in de breedte van de kolom past.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Configuratie-Element](./configuration-element-format.md)|Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[Configuratie-Element](./configuration-element-format.md)

[DisplayError-Element (indeling)](./displayerror-element-format.md)

[EnumerableExpansions-Element (indeling)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)

[ShowError Element (indeling)](./showerror-element-format.md)

[WrapTables-Element (indeling)](./wraptables-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
