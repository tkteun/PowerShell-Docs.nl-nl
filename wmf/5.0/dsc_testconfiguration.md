---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187558"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>De cmdlet test-DscConfiguration ondersteunt configuraties van verwijzing

De cmdlet Test-DscConfiguration is bijgewerkt zodat het testen van de status van de gewenste configuratie van een of meer doelknooppunten door te geven van een configuratie referentiedocument om te kunnen vergelijken.

De volgende nieuwe parametersets gebruik van DSC-configuraties in het opgegeven pad voor alleen test en elke configuratie nooit toepassen op de knooppunten van het opgegeven doel. De naam van elke MOF wordt net als bij Start DscConfiguration en andere DSC-cmdlets gebruikt om te bepalen welke doelknooppunt voor het testen van de configuratie op.

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

De volgende nieuwe parametersets gebruiken een DSC-configuratie voor één alleen testen en de configuratie nooit toepassen op de knooppunten van het opgegeven doel.

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
