---
title: Display error-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774283"
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
