---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties nesten
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75417862"
---
# <a name="nesting-dsc-configurations"></a>DSC-configuraties nesten

Een geneste configuratie (ook wel samengestelde configuratie genoemd) is een configuratie die wordt aangeroepen binnen een andere configuratie alsof het een resource is. Beide configuraties moeten in hetzelfde bestand worden gedefinieerd.

Laten we eens kijken naar een eenvoudig voor beeld:

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

In dit voor beeld neemt `FileConfig` twee verplichte para meters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de eigenschappen **SourcePath** en **doelpad** in het resource blok `File`. De `NestedConfig` configuratie roept `FileConfig` alsof het een resource is. De eigenschappen in het `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) zijn de para meters van de `FileConfig` configuratie.

DSC biedt momenteel geen ondersteuning voor het nesten van configuraties binnen geneste configuraties. U kunt alleen een configuratie met één laag diepte nesten.

## <a name="see-also"></a>Zie ook

- [Samengestelde resources: met behulp van een DSC-configuratie als resource](../resources/authoringResourceComposite.md)