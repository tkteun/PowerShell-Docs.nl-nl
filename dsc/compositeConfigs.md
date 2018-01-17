---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Geneste configuraties
ms.openlocfilehash: 89badda86707a129909b1c3cc3f79afa0b5f5df6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-dsc-configurations"></a>Het nesten van DSC-configuraties

Een geneste configuratie (ook wel samengestelde configuratie) is een configuratie die is aangeroepen in een andere configuratie alsof deze een resource.
Beide configuraties moeten worden gedefinieerd in hetzelfde bestand.

Bekijk een eenvoudig voorbeeld:

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

In dit voorbeeld `FileConfig` heeft twee verplichte parameters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de **bronpad** en  **Doelpad** eigenschappen in de `File` resource blok. De `NestedConfig` configuratie aanroepen `FileConfig` alsof deze een resource.
De eigenschappen in de `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) de parameters van de `FileConfig` configuratie.

## <a name="see-also"></a>Zie ook

- [Samengestelde bronnen--met een DSC-configuratie als een bron](authoringResourceComposite.md)

