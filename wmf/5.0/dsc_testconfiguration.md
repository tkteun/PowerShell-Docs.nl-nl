---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058740"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>De cmdlet test-DscConfiguration ondersteunt Verwijzingsconfiguraties

De cmdlet Test-DscConfiguration is bijgewerkt om toe te staan van de status van de gewenste configuratie van een of meer doelknooppunten testen door een referentiedocument configuratie om te kunnen vergelijken op te geven.

De volgende nieuwe parametersets DSC-configuraties gebruiken in het opgegeven pad voor alleen test en nooit elke configuratie toepassen op de knooppunten van het opgegeven doel. De naam van elke MOF wordt net als bij de Start-DscConfiguration en andere DSC-cmdlets gebruikt om te bepalen welk doelknooppunt voor het testen van de configuratie op.

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

De volgende nieuwe parametersets gebruiken om een enkele DSC-configuratie te testen alleen nooit de configuratie van toepassing op de knooppunten van het opgegeven doel.

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
