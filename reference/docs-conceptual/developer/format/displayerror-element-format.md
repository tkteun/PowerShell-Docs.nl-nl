---
ms.date: 09/13/2016
ms.topic: reference
title: Het element DisplayError (opmaak)
description: Het element DisplayError (opmaak)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649930"
---
# <a name="displayerror-element-format"></a>Het element DisplayError (opmaak)

Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven wanneer een fout optreedt bij het weer geven van een stukje gegevens.

Configuratie-element (indeling) DefaultSettings element (indeling) Display error element (indeling)

## <a name="syntax"></a>Syntax

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `DisplayError` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element DefaultSettings (opmaak)](./defaultsettings-element-format.md)|Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

Wanneer er een fout optreedt tijdens het weer geven van een stukje gegevens, blijft de locatie van de gegevens standaard leeg. Als dit element is ingesteld op True, wordt de #ERR teken reeks weer gegeven.

## <a name="see-also"></a>Zie ook

[Het element DefaultSettings (opmaak)](./defaultsettings-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
