---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties nesten
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75417862"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="1c7cb-103">DSC-configuraties nesten</span><span class="sxs-lookup"><span data-stu-id="1c7cb-103">Nesting DSC configurations</span></span>

<span data-ttu-id="1c7cb-104">Een geneste configuratie (ook wel samengestelde configuratie genoemd) is een configuratie die wordt aangeroepen binnen een andere configuratie alsof het een resource is.</span><span class="sxs-lookup"><span data-stu-id="1c7cb-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="1c7cb-105">Beide configuraties moeten in hetzelfde bestand worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="1c7cb-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="1c7cb-106">Laten we eens kijken naar een eenvoudig voor beeld:</span><span class="sxs-lookup"><span data-stu-id="1c7cb-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="1c7cb-107">In dit voor beeld `FileConfig` heeft twee verplichte para meters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de eigenschappen **SourcePath** en **doelpad** in het `File` resource blok.</span><span class="sxs-lookup"><span data-stu-id="1c7cb-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="1c7cb-108">De `NestedConfig` configuratie aanroepen `FileConfig` alsof het een bron is.</span><span class="sxs-lookup"><span data-stu-id="1c7cb-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="1c7cb-109">De eigenschappen in het `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) zijn de para meters `FileConfig` van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="1c7cb-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="1c7cb-110">DSC biedt momenteel geen ondersteuning voor het nesten van configuraties binnen geneste configuraties.</span><span class="sxs-lookup"><span data-stu-id="1c7cb-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="1c7cb-111">U kunt alleen een configuratie met één laag diepte nesten.</span><span class="sxs-lookup"><span data-stu-id="1c7cb-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c7cb-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1c7cb-112">See Also</span></span>

- [<span data-ttu-id="1c7cb-113">Samengestelde resources: met behulp van een DSC-configuratie als resource</span><span class="sxs-lookup"><span data-stu-id="1c7cb-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)