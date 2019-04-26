---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Met behulp van configuratiegegevens
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080217"
---
# <a name="using-configuration-data-in-dsc"></a>Met behulp van de configuratiegegevens in DSC

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Met behulp van de ingebouwde DSC **ConfigurationData** parameter, kunt u gegevens die kunnen worden gebruikt in een configuratie definiëren.
Hiermee kunt u een configuratie voor één die kan worden gebruikt voor meerdere knooppunten of voor verschillende omgevingen maken.
Bijvoorbeeld, als u een toepassing ontwikkelt, kunt u één configuratie gebruiken voor zowel ontwikkeling als productie-omgevingen, en configuratiegegevens om op te geven van de gegevens voor elke omgeving.

In dit onderwerp beschrijft de structuur van de **ConfigurationData** hash-tabel.
Zie voor meer voorbeelden van hoe u configuratiegegevens [configuratie- en omgevingsgegevens scheiden](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>De algemene parameter ConfigurationData

Een DSC-configuratie wordt een algemene parameter **ConfigurationData**, dat u opgeeft wanneer u de configuratie compileren.
Zie voor meer informatie over het compileren van configuraties [DSC-configuraties](configurations.md).

De **ConfigurationData** parameter is een hashtabel die ten minste één sleutel met de naam moet hebben **AllNodes**.
Het kan ook een of meer sleutels hebben.

> [!NOTE]
> De voorbeelden in dit onderwerp gebruiken één extra sleutel (dan de benoemde **AllNodes** sleutel) met de naam `NonNodeData`, maar u kunt een willekeurig aantal aanvullende sleutels bevatten, en ze elke gewenste naam.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

De waarde van de **AllNodes** sleutel is een matrix. Elk element van deze matrix is ook een hash-tabel dat er moet ten minste één sleutel met de naam **knooppuntnaam**:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

U kunt andere sleutels toevoegen aan elke hash-tabel:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

Als u wilt een eigenschap van toepassing op alle knooppunten, kunt u een lid van de **AllNodes** matrix waarvoor een **knooppuntnaam** van `*`.
Bijvoorbeeld, voor elk knooppunt een `LogPath` eigenschap, u kunt dit doen:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Dit is het equivalent van het toevoegen van een eigenschap met de naam `LogPath` met een waarde van `"C:\Logs"` aan elk van de andere blokken (`VM-1`, `VM-2`, en `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>De hashtabel ConfigurationData definiëren

U kunt definiëren **ConfigurationData** als een variabele binnen hetzelfde scriptbestand als een configuratie (zoals in het vorige voorbeeld) of in een afzonderlijke `.psd1` bestand.
Voor het definiëren van **ConfigurationData** in een `.psd1` bestand, maakt u een bestand met alleen de hashtabel die Hiermee geeft u de configuratiegegevens.

U kunt bijvoorbeeld een bestand met de naam maken `MyData.psd1` met de volgende inhoud:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Compileren van een configuratie met configuratiegegevens

Samengesteld op basis van een configuratie waarvoor u configuratiegegevens hebt gedefinieerd, geven u de configuratiegegevens als de waarde van de **ConfigurationData** parameter.

Hiermee maakt u een MOF-bestand voor elk item in de **AllNodes** matrix.
Elke MOF-bestand worden benoemd met de `NodeName` eigenschap van de bijbehorende matrixvermelding.

Bijvoorbeeld, als u de configuratiegegevens in definieert de `MyData.psd1` bestand hierboven, compileren van een configuratie maakt beide `VM-1.mof` en `VM-2.mof` bestanden.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compileren van een configuratie met de van configuratiegegevens met behulp van een variabele

Gebruik van configuratiegegevens die is gedefinieerd als een variabele in dezelfde `.ps1` bestand als de configuratie, geven u naam van de variabele als de waarde van de **ConfigurationData** parameter bij het compileren van de configuratie:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compileren van een configuratie met de van configuratiegegevens met behulp van een gegevensbestand

Voor het gebruik van configuratiegegevens die is gedefinieerd in een .psd1-bestand, u geeft het pad en de naam van het bestand als de waarde van de **ConfigurationData** parameter bij het compileren van de configuratie:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>ConfigurationData variabelen gebruiken in een configuratie

DSC biedt de volgende speciale variabelen die kunnen worden gebruikt in een configuratiescript:

- **$AllNodes** verwijst naar de volledige verzameling van knooppunten die zijn gedefinieerd in **ConfigurationData**. U kunt filteren, de **AllNodes** verzameling met behulp van **. WHERE()** en **. ForEach()**.
- **ConfigurationData** verwijst naar de volledige hash-tabel die wordt doorgegeven als parameter bij het compileren van een configuratie.
- **MyTypeName** bevat de [configuratie](configurations.md) de naam van de variabele wordt gebruikt in. Bijvoorbeeld, in de configuratie van de `MyDscConfiguration`, wordt de `$MyTypeName` heeft een waarde van `MyDscConfiguration`.
- **Knooppunt** verwijst naar een bepaalde vermelding in de **AllNodes** verzameling nadat deze is gefilterd met behulp van **. WHERE()** of **. ForEach()**.
  - U kunt meer lezen over deze methoden in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

## <a name="using-non-node-data"></a>Met behulp van niet-knooppuntgegevens

Zoals we hebben gezien in de vorige voorbeelden de **ConfigurationData** hashtabel kan hebben een of meer sleutels naast de vereiste **AllNodes** sleutel.
In de voorbeelden in dit onderwerp hebben we slechts één extra knooppunt gebruikt en met de naam `NonNodeData`.
U kunt echter een willekeurig aantal aanvullende sleutels definiëren, en elke gewenste naam.

Zie voor een voorbeeld van het gebruik van niet-knooppuntgegevens [configuratie- en omgevingsgegevens scheiden](separatingEnvData.md).

## <a name="see-also"></a>Zie ook

- [Referentieopties in de configuratiegegevens](configDataCredentials.md)
- [DSC-configuraties](configurations.md)