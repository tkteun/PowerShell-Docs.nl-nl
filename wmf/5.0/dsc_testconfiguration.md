---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="1048a-102">De cmdlet test-DscConfiguration ondersteunt configuraties van verwijzing</span><span class="sxs-lookup"><span data-stu-id="1048a-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="1048a-103">De cmdlet Test-DscConfiguration is bijgewerkt zodat het testen van de status van de gewenste configuratie van een of meer doelknooppunten door te geven van een configuratie referentiedocument om te kunnen vergelijken.</span><span class="sxs-lookup"><span data-stu-id="1048a-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="1048a-104">De volgende nieuwe parametersets gebruik van DSC-configuraties in het opgegeven pad voor alleen test en elke configuratie nooit toepassen op de knooppunten van het opgegeven doel.</span><span class="sxs-lookup"><span data-stu-id="1048a-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="1048a-105">De naam van elke MOF wordt net als bij Start DscConfiguration en andere DSC-cmdlets gebruikt om te bepalen welke doelknooppunt voor het testen van de configuratie op.</span><span class="sxs-lookup"><span data-stu-id="1048a-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="1048a-106">De volgende nieuwe parametersets gebruiken een DSC-configuratie voor één alleen testen en de configuratie nooit toepassen op de knooppunten van het opgegeven doel.</span><span class="sxs-lookup"><span data-stu-id="1048a-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
