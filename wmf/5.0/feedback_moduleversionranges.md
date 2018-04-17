---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="fe667-102">Modules ondersteuning voor het declareren van versie bereiken (1.\*, enzovoort)</span><span class="sxs-lookup"><span data-stu-id="fe667-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="fe667-103">In combinatie met **- MinimumVersion**, **- MaximumVersion** nu kan de gebruiker get/import-module binnen een bepaald bereik.</span><span class="sxs-lookup"><span data-stu-id="fe667-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="fe667-104">De parameter bieden ook ondersteuning voor **.** \*.</span><span class="sxs-lookup"><span data-stu-id="fe667-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="fe667-105">Het volgende voorbeeld ziet u hoe het werkt:</span><span class="sxs-lookup"><span data-stu-id="fe667-105">The following example shows how it works:</span></span>

<span data-ttu-id="fe667-106">U kunt nu combineren **- MinimumVersion** en **- MaximumVersion** module binnen een specifiek bereik te importeren:</span><span class="sxs-lookup"><span data-stu-id="fe667-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
