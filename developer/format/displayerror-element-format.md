---
title: DisplayError-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056478"
---
# <a name="displayerror-element-format"></a>Het element DisplayError (opmaak)

Hiermee geeft u op dat de tekenreeks #ERR wordt weergegeven wanneer er treedt een fout op bij het weergeven van een hoeveelheid gegevens.

Configuratie Element (indeling) DefaultSettings-Element (indeling) DisplayError-Element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `DisplayError` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[DefaultSettings-Element (indeling)](./defaultsettings-element-format.md)|Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert.|

## <a name="remarks"></a>Opmerkingen

Standaard als een fout optreedt tijdens een poging om weer te geven van een hoeveelheid gegevens, is de locatie van de gegevens leeg. Wanneer dit element is ingesteld op true, wordt de tekenreeks #ERR wordt weergegeven.

## <a name="see-also"></a>Zie ook

[DefaultSettings-Element (indeling)](./defaultsettings-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
