---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688530"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="3971b-102">On-demand PULL van DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="3971b-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="3971b-103">De nieuwe Update-DscConfiguration cmdlet activeert een pull vanuit de pull server (s) gedefinieerd in het meta-configuratie.</span><span class="sxs-lookup"><span data-stu-id="3971b-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="3971b-104">Het gedrag wordt vaak aangeduid als 'Nu Pull'.</span><span class="sxs-lookup"><span data-stu-id="3971b-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="3971b-105">Zodra geactiveerd, de pull gedraagt zich precies hetzelfde als wanneer geactiveerd tijdens de normale frequentie:</span><span class="sxs-lookup"><span data-stu-id="3971b-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="3971b-106">De controlesom voor de huidige configuratie wordt vergeleken met de controlesom voor de configuratie op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="3971b-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="3971b-107">Als ze hetzelfde zijn, bewerking is voltooid zonder toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="3971b-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="3971b-108">Als deze verschillend zijn, wordt de configuratie van de pull-server opgevraagd en toegepast.</span><span class="sxs-lookup"><span data-stu-id="3971b-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="3971b-109">**Opmerking:** Als de configuratie van Meta-RefreshMode = 'Push' een fout is geretourneerd door deze cmdlet, zodat deze cmdlet altijd niets doen wordt als een doelknooppunt in de modus 'Push wordt'.</span><span class="sxs-lookup"><span data-stu-id="3971b-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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
