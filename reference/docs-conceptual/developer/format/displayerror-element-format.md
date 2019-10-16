---
title: Display error-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355214"
---
# <a name="displayerror-element-format"></a>Het element DisplayError (opmaak)

Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven wanneer een fout optreedt bij het weer geven van een stukje gegevens.

Configuratie-element (indeling) DefaultSettings element (indeling) Display error element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `DisplayError` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[DefaultSettings-element (indeling)](./defaultsettings-element-format.md)|Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

Wanneer er een fout optreedt tijdens het weer geven van een stukje gegevens, blijft de locatie van de gegevens standaard leeg. Als dit element is ingesteld op True, wordt de #ERR teken reeks weer gegeven.

## <a name="see-also"></a>Zie ook

[DefaultSettings-element (indeling)](./defaultsettings-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
