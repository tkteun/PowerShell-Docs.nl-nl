---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: f2ddde78f436e6f03f521a9a8246dbda93e7a57a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="b53da-102">On-demand PULL van DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="b53da-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="b53da-103">De nieuwe Update DscConfiguration cmdlet activeert een pull van de pull (s) in het meta-configuratie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b53da-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="b53da-104">Het gedrag is vaak genoemd 'Nu Pull'.</span><span class="sxs-lookup"><span data-stu-id="b53da-104">The behavior is often referred to as 'Pull Now'.</span></span> 


<span data-ttu-id="b53da-105">Zodra geactiveerd, de pull gedraagt zich precies hetzelfde als wanneer geactiveerd tijdens de normale frequentie:</span><span class="sxs-lookup"><span data-stu-id="b53da-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="b53da-106">De controlesom voor de huidige configuratie wordt vergeleken met de controlesom voor de configuratie op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="b53da-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span> 
2. <span data-ttu-id="b53da-107">Als ze hetzelfde zijn, deze is voltooid zonder de configuratie van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="b53da-107">If they are the same, it completes successfully without applying the configuration.</span></span> 
3. <span data-ttu-id="b53da-108">Als deze verschillen, wordt de configuratie van de pull-server opgevraagd en toegepast.</span><span class="sxs-lookup"><span data-stu-id="b53da-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="b53da-109">**Opmerking:** als de Meta-configuratie RefreshMode = 'Push' een fout is geretourneerd door deze cmdlet, zodat deze cmdlet altijd niets doet als een doelknooppunt in de modus 'Push'.</span><span class="sxs-lookup"><span data-stu-id="b53da-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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

