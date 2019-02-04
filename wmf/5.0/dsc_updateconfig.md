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
# <a name="on-demand-pull-of-dsc-configurations"></a>On-demand PULL van DSC-configuraties

De nieuwe Update-DscConfiguration cmdlet activeert een pull vanuit de pull server (s) gedefinieerd in het meta-configuratie. Het gedrag wordt vaak aangeduid als 'Nu Pull'.


Zodra geactiveerd, de pull gedraagt zich precies hetzelfde als wanneer geactiveerd tijdens de normale frequentie:

1. De controlesom voor de huidige configuratie wordt vergeleken met de controlesom voor de configuratie op de pull-server.
2. Als ze hetzelfde zijn, bewerking is voltooid zonder toe te passen van de configuratie.
3. Als deze verschillend zijn, wordt de configuratie van de pull-server opgevraagd en toegepast.

**Opmerking:** Als de configuratie van Meta-RefreshMode = 'Push' een fout is geretourneerd door deze cmdlet, zodat deze cmdlet altijd niets doen wordt als een doelknooppunt in de modus 'Push wordt'.

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
