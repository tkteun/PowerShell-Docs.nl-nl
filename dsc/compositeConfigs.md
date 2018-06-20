---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Configuraties nesten
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218991"
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

In dit voorbeeld `FileConfig` heeft twee verplichte parameters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de **bronpad** en  **Doelpad** eigenschappen in de `File` resource blok.
De `NestedConfig` configuratie aanroepen `FileConfig` alsof deze een resource.
De eigenschappen in de `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) de parameters van de `FileConfig` configuratie.

## <a name="see-also"></a>Zie ook

- [Samengestelde bronnen--met een DSC-configuratie als een bron](authoringResourceComposite.md)