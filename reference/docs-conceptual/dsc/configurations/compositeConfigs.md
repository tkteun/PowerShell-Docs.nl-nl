---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties nesten
ms.openlocfilehash: e74c0fe1d7f7b198c2d6f796c0bf120eb0ec21d9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564023"
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

In dit voor beeld `FileConfig` heeft twee verplichte para meters, **CopyFrom** en **CopyTo**, die worden gebruikt als de waarden voor de eigenschappen **SourcePath** en **doelpad** in het `File` resource blok. De `NestedConfig` configuratie aanroepen `FileConfig` alsof het een bron is. De eigenschappen in het `NestedConfig` resource blok (**CopyFrom** en **CopyTo**) zijn de para meters van de `FileConfig` configuratie.

DSC biedt momenteel geen ondersteuning voor het nesten van configuraties binnen geneste configuraties. U kunt alleen een configuratie met één laag diepte nesten.

## <a name="see-also"></a>Zie ook

- [Samengestelde resources: met behulp van een DSC-configuratie als resource](../resources/authoringResourceComposite.md)
