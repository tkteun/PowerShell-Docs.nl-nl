---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 27f8fab6a72e7f3a3f510f5a9e503bbfb8a8f618
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
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