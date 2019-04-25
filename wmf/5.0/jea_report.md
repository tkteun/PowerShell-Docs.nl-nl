---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085240"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="6d573-102">Rapportage over JEA</span><span class="sxs-lookup"><span data-stu-id="6d573-102">Reporting on JEA</span></span>

<span data-ttu-id="6d573-103">Als u wilt rapporteren over de status van de JEA-configuratie, kunt u het volgende gebruiken:</span><span class="sxs-lookup"><span data-stu-id="6d573-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="6d573-104">**Get-PSSessionConfiguration** geregistreerd om terug te keren een lijst van alle eindpunten op een bepaalde computer.</span><span class="sxs-lookup"><span data-stu-id="6d573-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="6d573-105">**Get-PSSessionCapability** om te rapporteren over de mogelijkheden voor een bepaalde gebruiker is op een bepaald eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6d573-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="6d573-106">Hier volgt een voorbeeld van **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="6d573-106">Here's an example of **Get-PSSessionCapability**:</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...
```

<span data-ttu-id="6d573-107">Om te rapporteren over de _acties_ gebruikers duurde tijdens een JEA-sessie, kunt u:</span><span class="sxs-lookup"><span data-stu-id="6d573-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="6d573-108">De "over-the-schouder" Transcripten voor dat JEA-eindpunt inschakelen en raadpleegt u de map transcript voor een volledige logboek van acties van elke gebruiker</span><span class="sxs-lookup"><span data-stu-id="6d573-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="6d573-109">PowerShell-module logboekregistratie inschakelen en controleren van de PowerShell-gebeurtenislogboeken.</span><span class="sxs-lookup"><span data-stu-id="6d573-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>