---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Configuraties nesten
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684554"
---
# <a name="nesting-dsc-configurations"></a>DSC-configuraties nesten

Een geneste configuratie (ook wel samengestelde configuratie genoemd) is een configuratie die wordt aangeroepen binnen een andere configuratie alsof het een resource.
Beide configuraties moeten worden gedefinieerd in hetzelfde bestand.

We gaan een eenvoudige voorbeeld kijken:

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

In dit voorbeeld `FileConfig` heeft twee verplichte parameters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de **bronpad** en  **Doelpad** eigenschappen in de `File` resource blokkeren.
De `NestedConfig` configuratie aanroepen `FileConfig` alsof het een resource.
De eigenschappen in de `NestedConfig` resource blokkeren (**CopyFrom** en **CopyTo**) de parameters van de `FileConfig` configuratie.

## <a name="see-also"></a>Zie ook

- [Samengestelde resources--met behulp van een DSC-configuratie als een resource](../resources/authoringResourceComposite.md)