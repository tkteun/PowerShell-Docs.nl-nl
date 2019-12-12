---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties nesten
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942368"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="9828d-103">DSC-configuraties nesten</span><span class="sxs-lookup"><span data-stu-id="9828d-103">Nesting DSC configurations</span></span>

<span data-ttu-id="9828d-104">Een geneste configuratie (ook wel samengestelde configuratie genoemd) is een configuratie die wordt aangeroepen binnen een andere configuratie alsof het een resource is.</span><span class="sxs-lookup"><span data-stu-id="9828d-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="9828d-105">Beide configuraties moeten in hetzelfde bestand worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9828d-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="9828d-106">Laten we eens kijken naar een eenvoudig voor beeld:</span><span class="sxs-lookup"><span data-stu-id="9828d-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="9828d-107">In dit voor beeld neemt `FileConfig` twee verplichte para meters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de eigenschappen **SourcePath** en **doelpad** in het resource blok `File`.</span><span class="sxs-lookup"><span data-stu-id="9828d-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="9828d-108">De `NestedConfig` configuratie roept `FileConfig` alsof het een resource is.</span><span class="sxs-lookup"><span data-stu-id="9828d-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="9828d-109">De eigenschappen in het `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) zijn de para meters van de `FileConfig` configuratie.</span><span class="sxs-lookup"><span data-stu-id="9828d-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="9828d-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9828d-110">See Also</span></span>

- [<span data-ttu-id="9828d-111">Samengestelde resources: met behulp van een DSC-configuratie als resource</span><span class="sxs-lookup"><span data-stu-id="9828d-111">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)