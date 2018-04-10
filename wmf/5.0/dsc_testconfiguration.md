---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 18c1dab7412b8e9d31960507b612dd6cc56d31d5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
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