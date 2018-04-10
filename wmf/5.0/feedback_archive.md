---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a>Archief-cmdlets

Twee nieuwe cmdlets, **comprimeren archief** en **uit te breiden archief**laat u uitvouwen ZIP-bestanden en comprimeren.

## <a name="compress-archive"></a>Compress-archief
De **comprimeren archief** cmdlet maakt een nieuw archiefbestand van opgegeven bestanden. Een archiefbestand kan meerdere bestanden die moeten worden verpakt en optioneel in een enkel bestand gemakkelijker verwerking en opslag zijn gecomprimeerd. Een archiefbestand worden gecomprimeerd met behulp van een compressiealgoritme die is opgegeven in de **- CompressionLevel** parameter.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Vouw archief
De **uit te breiden archief** cmdlet bestanden uit een bestand opgegeven archief worden uitgepakt. Een archiefbestand kan meerdere bestanden die moeten worden verpakt en optioneel in een enkel bestand gemakkelijker verwerking en opslag zijn gecomprimeerd.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```