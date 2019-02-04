---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688558"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="75370-102">De cmdlet test-DscConfiguration ondersteunt Verwijzingsconfiguraties</span><span class="sxs-lookup"><span data-stu-id="75370-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="75370-103">De cmdlet Test-DscConfiguration is bijgewerkt om toe te staan van de status van de gewenste configuratie van een of meer doelknooppunten testen door een referentiedocument configuratie om te kunnen vergelijken op te geven.</span><span class="sxs-lookup"><span data-stu-id="75370-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="75370-104">De volgende nieuwe parametersets DSC-configuraties gebruiken in het opgegeven pad voor alleen test en nooit elke configuratie toepassen op de knooppunten van het opgegeven doel.</span><span class="sxs-lookup"><span data-stu-id="75370-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="75370-105">De naam van elke MOF wordt net als bij de Start-DscConfiguration en andere DSC-cmdlets gebruikt om te bepalen welk doelknooppunt voor het testen van de configuratie op.</span><span class="sxs-lookup"><span data-stu-id="75370-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="75370-106">De volgende nieuwe parametersets gebruiken om een enkele DSC-configuratie te testen alleen nooit de configuratie van toepassing op de knooppunten van het opgegeven doel.</span><span class="sxs-lookup"><span data-stu-id="75370-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
