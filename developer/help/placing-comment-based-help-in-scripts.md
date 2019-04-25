---
title: Help op basis van een opmerking in Scripts plaatsen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083226"
---
# <a name="placing-comment-based-help-in-scripts"></a>Help op basis van opmerkingen in scripts plaatsen

Dit onderwerp wordt uitgelegd waar u de help voor een script op basis van een opmerking plaatsen zodat het `Get-Help` cmdlet het helponderwerp op basis van een opmerking koppelt met scripts en niet met alle functies die mogelijk in het script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Waar plaatst u de Help op basis van een opmerking voor een Script

- Aan het begin van het scriptbestand. Script Help kunt in het script worden voorafgegaan door opmerkingen en lege regels.

- Aan het einde van het scriptbestand.

  Als het eerste item in de hoofdtekst van het script (na de Help) een functiedeclaratie is, moet er ten minste twee lege regels tussen het einde van het Help-script en de functiedeclaratie. Anders wordt de Help geïnterpreteerd als hulp voor de functie niet Help voor het script.

## <a name="examples-of-help-placement-in-a-script"></a>Voorbeelden van de plaatsing van de Help-informatie in een Script

 De volgende voorbeelden ziet elk van de opties voor plaatsing voor meer informatie over op basis van een opmerking voor een script.

### <a name="help-at-the-beginning-of-a-script"></a>Help weer bij het begin van een Script

 Het volgende voorbeeld ziet u op basis van een opmerking aan het begin van een script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Help weer bij het einde van een Script

 Het volgende voorbeeld ziet Opmerking gebaseerde aan het einde van een script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```