---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225688"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="fc650-102">Modules ondersteuning voor het declareren van versie bereiken (1.\*, enzovoort)</span><span class="sxs-lookup"><span data-stu-id="fc650-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="fc650-103">In combinatie met **- MinimumVersion**, **- MaximumVersion** nu kan de gebruiker get/import-module binnen een bepaald bereik.</span><span class="sxs-lookup"><span data-stu-id="fc650-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="fc650-104">De parameter bieden ook ondersteuning voor **.** \*.</span><span class="sxs-lookup"><span data-stu-id="fc650-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="fc650-105">Het volgende voorbeeld ziet u hoe het werkt:</span><span class="sxs-lookup"><span data-stu-id="fc650-105">The following example shows how it works:</span></span>

<span data-ttu-id="fc650-106">U kunt nu combineren **- MinimumVersion** en **- MaximumVersion** module binnen een specifiek bereik te importeren:</span><span class="sxs-lookup"><span data-stu-id="fc650-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
