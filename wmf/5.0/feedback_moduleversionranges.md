---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687984"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Module-ondersteuning voor declareren versiebereiken (1.*, enzovoort)
In combinatie met **- MinimumVersion**, **- MaximumVersion** kunnen nu get /-import-module binnen het bereik van specifieke gebruiker. De parameter bieden ook ondersteuning **.** \*. Het volgende voorbeeld laat zien hoe het werkt:

U kunt nu, combineren **- MinimumVersion** en **- MaximumVersion** module binnen een bepaald bereik te importeren:

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
