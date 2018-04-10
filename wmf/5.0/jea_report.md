---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="reporting-on-jea"></a><span data-ttu-id="19b39-102">Rapportage over JEA</span><span class="sxs-lookup"><span data-stu-id="19b39-102">Reporting on JEA</span></span>
<span data-ttu-id="19b39-103">Om te rapporteren over de status van de configuratie van uw JEA, kunt u het volgende gebruiken:</span><span class="sxs-lookup"><span data-stu-id="19b39-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="19b39-104">**Get-PSSessionConfiguration** geregistreerd om te retourneren van een lijst met alle eindpunten op een bepaalde computer.</span><span class="sxs-lookup"><span data-stu-id="19b39-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="19b39-105">**Get-PSSessionCapability** om te rapporteren over de mogelijkheden voor een bepaalde gebruiker op een specifieke eindpunt heeft.</span><span class="sxs-lookup"><span data-stu-id="19b39-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="19b39-106">Hier volgt een voorbeeld van **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="19b39-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
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

<span data-ttu-id="19b39-107">Om te rapporteren over de _acties_ gebruikers tijdens een sessie JEA duurde, kunt u:</span><span class="sxs-lookup"><span data-stu-id="19b39-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="19b39-108">Schakel de transcripties 'failover-de-schouder' voor dat eindpunt JEA en raadpleegt u de map met de tekst voor een volledige logboek van acties van elke gebruiker</span><span class="sxs-lookup"><span data-stu-id="19b39-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="19b39-109">PowerShell-module logboekregistratie inschakelen en controleren van de PowerShell-gebeurtenislogboeken.</span><span class="sxs-lookup"><span data-stu-id="19b39-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>