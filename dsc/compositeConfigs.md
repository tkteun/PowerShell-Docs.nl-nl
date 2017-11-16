---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Geneste configuraties
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="a7a14-103">Het nesten van DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="a7a14-103">Nesting DSC configurations</span></span>

<span data-ttu-id="a7a14-104">Een geneste configuratie (ook wel samengestelde configuratie) is een configuratie die is aangeroepen in een andere configuratie alsof deze een resource.</span><span class="sxs-lookup"><span data-stu-id="a7a14-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="a7a14-105">Beide configuraties moeten worden gedefinieerd in hetzelfde bestand.</span><span class="sxs-lookup"><span data-stu-id="a7a14-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="a7a14-106">Bekijk een eenvoudig voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a7a14-106">Let's look at a simple example:</span></span>

```powershell
Configuration FileConfig 
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }
    
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

<span data-ttu-id="a7a14-107">In dit voorbeeld `FileConfig` heeft twee verplichte parameters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de **bronpad** en  **Doelpad** eigenschappen in de `File` resource blok.</span><span class="sxs-lookup"><span data-stu-id="a7a14-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="a7a14-108">De `NestedConfig` configuratie aanroepen `FileConfig` alsof deze een resource.</span><span class="sxs-lookup"><span data-stu-id="a7a14-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="a7a14-109">De eigenschappen in de `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) de parameters van de `FileConfig` configuratie.</span><span class="sxs-lookup"><span data-stu-id="a7a14-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7a14-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a7a14-110">See Also</span></span>

- [<span data-ttu-id="a7a14-111">Samengestelde bronnen--met een DSC-configuratie als een bron</span><span class="sxs-lookup"><span data-stu-id="a7a14-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)

