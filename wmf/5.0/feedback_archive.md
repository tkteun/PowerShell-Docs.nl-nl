---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218090"
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
