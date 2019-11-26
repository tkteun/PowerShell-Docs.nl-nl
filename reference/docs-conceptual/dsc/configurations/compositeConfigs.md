---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties nesten
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942368"
---
# <a name="nesting-dsc-configurations"></a>DSC-configuraties nesten

Een geneste configuratie (ook wel samengestelde configuratie genoemd) is een configuratie die wordt aangeroepen binnen een andere configuratie alsof het een resource is.
Beide configuraties moeten in hetzelfde bestand worden gedefinieerd.

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

In dit voor beeld neemt `FileConfig` twee verplichte para meters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de eigenschappen **SourcePath** en **doelpad** in het `File`-Resource blok.
De `NestedConfig`-configuratie roept `FileConfig` alsof het een resource is.
De eigenschappen in het `NestedConfig`-Resource blok (**CopyFrom** en **CopyTo**) zijn de para meters van de configuratie van de `FileConfig`.

## <a name="see-also"></a>Zie ook

- [Samengestelde resources: met behulp van een DSC-configuratie als resource](../resources/authoringResourceComposite.md)