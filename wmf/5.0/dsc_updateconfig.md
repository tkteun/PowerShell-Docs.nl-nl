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
# <a name="on-demand-pull-of-dsc-configurations"></a>On-demand PULL van DSC-configuraties

De nieuwe Update DscConfiguration cmdlet activeert een pull van de pull (s) in het meta-configuratie is gedefinieerd. Het gedrag is vaak genoemd 'Nu Pull'. 


Zodra geactiveerd, de pull gedraagt zich precies hetzelfde als wanneer geactiveerd tijdens de normale frequentie:

1. De controlesom voor de huidige configuratie wordt vergeleken met de controlesom voor de configuratie op de pull-server. 
2. Als ze hetzelfde zijn, deze is voltooid zonder de configuratie van de toepassing. 
3. Als deze verschillen, wordt de configuratie van de pull-server opgevraagd en toegepast.

**Opmerking:** als de Meta-configuratie RefreshMode = 'Push' een fout is geretourneerd door deze cmdlet, zodat deze cmdlet altijd niets doet als een doelknooppunt in de modus 'Push'.

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

