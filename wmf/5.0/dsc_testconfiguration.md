---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="cfe92-102">De cmdlet test-DscConfiguration ondersteunt configuraties van verwijzing</span><span class="sxs-lookup"><span data-stu-id="cfe92-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="cfe92-103">De cmdlet Test-DscConfiguration is bijgewerkt zodat het testen van de status van de gewenste configuratie van een of meer doelknooppunten door te geven van een configuratie referentiedocument om te kunnen vergelijken.</span><span class="sxs-lookup"><span data-stu-id="cfe92-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="cfe92-104">De volgende nieuwe parametersets gebruik van DSC-configuraties in het opgegeven pad voor alleen test en elke configuratie nooit toepassen op de knooppunten van het opgegeven doel.</span><span class="sxs-lookup"><span data-stu-id="cfe92-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="cfe92-105">De naam van elke MOF wordt net als bij Start DscConfiguration en andere DSC-cmdlets gebruikt om te bepalen welke doelknooppunt voor het testen van de configuratie op.</span><span class="sxs-lookup"><span data-stu-id="cfe92-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

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

<span data-ttu-id="cfe92-106">De volgende nieuwe parametersets gebruiken een DSC-configuratie voor één alleen testen en de configuratie nooit toepassen op de knooppunten van het opgegeven doel.</span><span class="sxs-lookup"><span data-stu-id="cfe92-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

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

