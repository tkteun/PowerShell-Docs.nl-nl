---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="7dc04-102">On-demand PULL van DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="7dc04-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="7dc04-103">De nieuwe Update DscConfiguration cmdlet activeert een pull van de pull (s) in het meta-configuratie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="7dc04-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="7dc04-104">Het gedrag is vaak genoemd 'Nu Pull'.</span><span class="sxs-lookup"><span data-stu-id="7dc04-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="7dc04-105">Zodra geactiveerd, de pull gedraagt zich precies hetzelfde als wanneer geactiveerd tijdens de normale frequentie:</span><span class="sxs-lookup"><span data-stu-id="7dc04-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="7dc04-106">De controlesom voor de huidige configuratie wordt vergeleken met de controlesom voor de configuratie op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="7dc04-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="7dc04-107">Als ze hetzelfde zijn, deze is voltooid zonder de configuratie van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="7dc04-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="7dc04-108">Als deze verschillen, wordt de configuratie van de pull-server opgevraagd en toegepast.</span><span class="sxs-lookup"><span data-stu-id="7dc04-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="7dc04-109">**Opmerking:** als de Meta-configuratie RefreshMode = 'Push' een fout is geretourneerd door deze cmdlet, zodat deze cmdlet altijd niets doet als een doelknooppunt in de modus 'Push'.</span><span class="sxs-lookup"><span data-stu-id="7dc04-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
