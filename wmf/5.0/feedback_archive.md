---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: db9c630bcb8e9e0da423c779976739f1ae76f13e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687970"
---
# <a name="archive-cmdlets"></a>Archief-cmdlets

Twee nieuwe cmdlets **Compress-archief** en **uit te breiden-archief**laat u comprimeren en vouw ZIP-bestanden.

## <a name="compress-archive"></a>Compress-archief
De **Compress-archief** cmdlet maakt een nieuwe archiefbestand van opgegeven bestanden. Een archiefbestand kan meerdere bestanden worden verpakt en (optioneel) gecomprimeerd in een enkel bestand gemakkelijker verwerking en opslag. Een archiefbestand worden gecomprimeerd met behulp van een compressiealgoritme die is opgegeven in de **- CompressionLevel** parameter.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Vouw archiveren
De **uit te breiden-archief** cmdlet bestanden van een opgegeven archiefbestand uitgepakt. Een archiefbestand kan meerdere bestanden worden verpakt en (optioneel) gecomprimeerd in een enkel bestand gemakkelijker verwerking en opslag.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
