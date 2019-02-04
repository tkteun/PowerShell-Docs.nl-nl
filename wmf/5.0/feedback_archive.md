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
# <a name="archive-cmdlets"></a><span data-ttu-id="deef6-102">Archief-cmdlets</span><span class="sxs-lookup"><span data-stu-id="deef6-102">Archive cmdlets</span></span>

<span data-ttu-id="deef6-103">Twee nieuwe cmdlets **Compress-archief** en **uit te breiden-archief**laat u comprimeren en vouw ZIP-bestanden.</span><span class="sxs-lookup"><span data-stu-id="deef6-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="deef6-104">Compress-archief</span><span class="sxs-lookup"><span data-stu-id="deef6-104">Compress-Archive</span></span>
<span data-ttu-id="deef6-105">De **Compress-archief** cmdlet maakt een nieuwe archiefbestand van opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="deef6-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="deef6-106">Een archiefbestand kan meerdere bestanden worden verpakt en (optioneel) gecomprimeerd in een enkel bestand gemakkelijker verwerking en opslag.</span><span class="sxs-lookup"><span data-stu-id="deef6-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="deef6-107">Een archiefbestand worden gecomprimeerd met behulp van een compressiealgoritme die is opgegeven in de **- CompressionLevel** parameter.</span><span class="sxs-lookup"><span data-stu-id="deef6-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="deef6-108">Vouw archiveren</span><span class="sxs-lookup"><span data-stu-id="deef6-108">Expand-Archive</span></span>
<span data-ttu-id="deef6-109">De **uit te breiden-archief** cmdlet bestanden van een opgegeven archiefbestand uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="deef6-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="deef6-110">Een archiefbestand kan meerdere bestanden worden verpakt en (optioneel) gecomprimeerd in een enkel bestand gemakkelijker verwerking en opslag.</span><span class="sxs-lookup"><span data-stu-id="deef6-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
