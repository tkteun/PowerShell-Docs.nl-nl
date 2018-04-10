---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Configuraties nesten
ms.openlocfilehash: 9c6dbce462f7481e5714039a95ae85f85be0072e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="a8ab6-103">Het nesten van DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="a8ab6-103">Nesting DSC configurations</span></span>

<span data-ttu-id="a8ab6-104">Een geneste configuratie (ook wel samengestelde configuratie) is een configuratie die is aangeroepen in een andere configuratie alsof deze een resource.</span><span class="sxs-lookup"><span data-stu-id="a8ab6-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="a8ab6-105">Beide configuraties moeten worden gedefinieerd in hetzelfde bestand.</span><span class="sxs-lookup"><span data-stu-id="a8ab6-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="a8ab6-106">Bekijk een eenvoudig voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a8ab6-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="a8ab6-107">In dit voorbeeld `FileConfig` heeft twee verplichte parameters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de **bronpad** en  **Doelpad** eigenschappen in de `File` resource blok.</span><span class="sxs-lookup"><span data-stu-id="a8ab6-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="a8ab6-108">De `NestedConfig` configuratie aanroepen `FileConfig` alsof deze een resource.</span><span class="sxs-lookup"><span data-stu-id="a8ab6-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="a8ab6-109">De eigenschappen in de `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) de parameters van de `FileConfig` configuratie.</span><span class="sxs-lookup"><span data-stu-id="a8ab6-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8ab6-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a8ab6-110">See Also</span></span>

- [<span data-ttu-id="a8ab6-111">Samengestelde bronnen--met een DSC-configuratie als een bron</span><span class="sxs-lookup"><span data-stu-id="a8ab6-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)