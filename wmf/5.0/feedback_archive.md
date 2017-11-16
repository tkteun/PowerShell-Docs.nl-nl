---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="029d9-102">Archief-cmdlets</span><span class="sxs-lookup"><span data-stu-id="029d9-102">Archive cmdlets</span></span>

<span data-ttu-id="029d9-103">Twee nieuwe cmdlets, **comprimeren archief** en **uit te breiden archief**laat u uitvouwen ZIP-bestanden en comprimeren.</span><span class="sxs-lookup"><span data-stu-id="029d9-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="029d9-104">Compress-archief</span><span class="sxs-lookup"><span data-stu-id="029d9-104">Compress-Archive</span></span>
<span data-ttu-id="029d9-105">De **comprimeren archief** cmdlet maakt een nieuw archiefbestand van opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="029d9-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="029d9-106">Een archiefbestand kan meerdere bestanden die moeten worden verpakt en optioneel in een enkel bestand gemakkelijker verwerking en opslag zijn gecomprimeerd.</span><span class="sxs-lookup"><span data-stu-id="029d9-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="029d9-107">Een archiefbestand worden gecomprimeerd met behulp van een compressiealgoritme die is opgegeven in de **- CompressionLevel** parameter.</span><span class="sxs-lookup"><span data-stu-id="029d9-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="029d9-108">Vouw archief</span><span class="sxs-lookup"><span data-stu-id="029d9-108">Expand-Archive</span></span>
<span data-ttu-id="029d9-109">De **uit te breiden archief** cmdlet bestanden uit een bestand opgegeven archief worden uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="029d9-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="029d9-110">Een archiefbestand kan meerdere bestanden die moeten worden verpakt en optioneel in een enkel bestand gemakkelijker verwerking en opslag zijn gecomprimeerd.</span><span class="sxs-lookup"><span data-stu-id="029d9-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

