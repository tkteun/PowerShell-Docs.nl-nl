---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Configuraties nesten
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403910"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="7257b-103">DSC-configuraties nesten</span><span class="sxs-lookup"><span data-stu-id="7257b-103">Nesting DSC configurations</span></span>

<span data-ttu-id="7257b-104">Een geneste configuratie (ook wel samengestelde configuratie genoemd) is een configuratie die wordt aangeroepen binnen een andere configuratie alsof het een resource.</span><span class="sxs-lookup"><span data-stu-id="7257b-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="7257b-105">Beide configuraties moeten worden gedefinieerd in hetzelfde bestand.</span><span class="sxs-lookup"><span data-stu-id="7257b-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="7257b-106">We gaan een eenvoudige voorbeeld kijken:</span><span class="sxs-lookup"><span data-stu-id="7257b-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="7257b-107">In dit voorbeeld `FileConfig` heeft twee verplichte parameters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de **bronpad** en  **Doelpad** eigenschappen in de `File` resource blokkeren.</span><span class="sxs-lookup"><span data-stu-id="7257b-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="7257b-108">De `NestedConfig` configuratie aanroepen `FileConfig` alsof het een resource.</span><span class="sxs-lookup"><span data-stu-id="7257b-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="7257b-109">De eigenschappen in de `NestedConfig` resource blokkeren (**CopyFrom** en **CopyTo**) de parameters van de `FileConfig` configuratie.</span><span class="sxs-lookup"><span data-stu-id="7257b-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="7257b-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7257b-110">See Also</span></span>

- [<span data-ttu-id="7257b-111">Samengestelde resources--met behulp van een DSC-configuratie als een resource</span><span class="sxs-lookup"><span data-stu-id="7257b-111">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)