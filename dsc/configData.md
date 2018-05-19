---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Met behulp van configuratiegegevens
ms.openlocfilehash: d42c43fddb54050adcbac949e7f67f3b41b540f1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="using-configuration-data-in-dsc"></a>Met behulp van de configuratiegegevens in DSC

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Met behulp van de ingebouwde DSC **ConfigurationData** parameter, kunt u gegevens die kunnen worden gebruikt in een configuratie definiëren.
Hiermee kunt u voor het maken van een configuratie voor één die kan worden gebruikt voor meerdere knooppunten of voor verschillende omgevingen.
Bijvoorbeeld, als u een toepassing ontwikkelt, kunt u één configuratie gebruiken voor ontwikkel- en productie-omgevingen en configuratiegegevens gebruiken om op te geven gegevens voor elke omgeving.

Dit onderwerp beschrijft de structuur van de **ConfigurationData** hash-tabel.
Zie voor voorbeelden van het gebruik van configuratiegegevens [scheiden van gegevens en de omgeving](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>De algemene parameter ConfigurationData

Een DSC-configuratie heeft een algemene parameter **ConfigurationData**, dat u opgeeft wanneer u de configuratie compileren.
Zie voor meer informatie over het compileren van configuraties [DSC-configuraties](configurations.md).

De **ConfigurationData** -parameter is een hasthtable waarvoor ten minste één sleutel met de naam moet **AllNodes**.
Het kan ook een of meer sleutels hebben.

>**Opmerking:** de voorbeelden in dit onderwerp gebruiken één extra sleutel (anders dan de benoemde **AllNodes** key) met de naam `NonNodeData`, maar u kunt een willekeurig aantal aanvullende sleutels bevatten en naam elke gewenste.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

De waarde van de **AllNodes** sleutel is een matrix. Elk element van deze matrix is ook een hashtabel die ten minste één sleutel met de naam moet hebben **NodeName**:

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

U kunt andere sleutels toevoegen aan elk hash-tabel:

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

Als u wilt een eigenschap van toepassing op alle knooppunten, kunt u een lid van de **AllNodes** matrix heeft een **NodeName** van `*`.
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
Voor het definiëren van **ConfigurationData** in een `.psd1` bestand, maakt u een bestand met alleen de hash-tabel die de configuratiegegevens vertegenwoordigt.

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

## <a name="compiling-a-configuration-with-configuration-data"></a>Een configuratie met configuratiegegevens compileren

Samengesteld op basis van een configuratie waarvoor u configuratiegegevens hebt gedefinieerd, geeft u de configuratiegegevens als de waarde van de **ConfigurationData** parameter.

Hiermee maakt u een MOF-bestand voor elk item in de **AllNodes** matrix.
Elke MOF-bestand worden benoemd met de `NodeName` eigenschap van de bijbehorende matrixvermelding.

Bijvoorbeeld, als het definiëren van configuratiegegevens, zoals in de `MyData.psd1` bestand hierboven, een configuratie compileren maakt zowel `VM-1.mof` en `VM-2.mof` bestanden.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compileren van een configuratie met configuratiegegevens met behulp van een variabele

Gebruik van de configuratiegegevens die is gedefinieerd als een variabele in dezelfde `.ps1` bestand als de configuratie, geeft u de variabele naam als de waarde van de **ConfigurationData** parameter bij het compileren van de configuratie:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compileren van een configuratie met configuratiegegevens met een gegevensbestand

Voor het gebruik van de configuratiegegevens die is gedefinieerd in een bestand .psd1 u geeft het pad en bestandsnaam van het bestand als de waarde van de **ConfigurationData** parameter bij het compileren van de configuratie:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>ConfigurationData variabelen gebruiken in een configuratie

DSC biedt drie speciale variabelen die kunnen worden gebruikt in een configuratiescript: **$AllNodes**, **$Node**, en **$ConfigurationData**.

- **$AllNodes** verwijst naar de volledige verzameling van knooppunten die zijn gedefinieerd in **ConfigurationData**. U kunt filteren de **AllNodes** verzameling met behulp van **. WHERE()** en **. ForEach()**.
- **Knooppunt** verwijst naar een bepaald item in de **AllNodes** verzameling nadat deze is gefilterd met behulp van **. WHERE()** of **. ForEach()**.
- **ConfigurationData** verwijst naar de volledige hash-tabel die is doorgegeven als parameter bij het compileren van een configuratie.

## <a name="using-non-node-data"></a>Met behulp van de gegevens niet-knooppunt

Als er in de eerdere voorbeelden hebt gezien de **ConfigurationData** hashtabel kan een of meer sleutels naast de vereiste hebben **AllNodes** sleutel.
In de voorbeelden in dit onderwerp, hebben we slechts één extra knooppunt gebruikt en met de naam `NonNodeData`.
U kunt echter een aantal aanvullende sleutels opgeven en elke gewenste naam.

Zie voor een voorbeeld van het gebruik van niet-knooppuntgegevens [scheiden van gegevens en de omgeving](separatingEnvData.md).

## <a name="see-also"></a>Zie ook
- [Referentieopties in configuratiegegevens](configDataCredentials.md)
- [DSC-configuraties](configurations.md)