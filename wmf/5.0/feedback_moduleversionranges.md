---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057500"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="a03b4-102">Module-ondersteuning voor declareren versiebereiken (1.\*, enzovoort)</span><span class="sxs-lookup"><span data-stu-id="a03b4-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="a03b4-103">In combinatie met **- MinimumVersion**, **- MaximumVersion** kunnen nu get /-import-module binnen het bereik van specifieke gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a03b4-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="a03b4-104">De parameter bieden ook ondersteuning **.** \*.</span><span class="sxs-lookup"><span data-stu-id="a03b4-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="a03b4-105">Het volgende voorbeeld laat zien hoe het werkt:</span><span class="sxs-lookup"><span data-stu-id="a03b4-105">The following example shows how it works:</span></span>

<span data-ttu-id="a03b4-106">U kunt nu, combineren **- MinimumVersion** en **- MaximumVersion** module binnen een bepaald bereik te importeren:</span><span class="sxs-lookup"><span data-stu-id="a03b4-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
