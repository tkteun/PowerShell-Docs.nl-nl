---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuratie gegevens gebruiken
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942109"
---
# <a name="using-configuration-data-in-dsc"></a>Configuratie gegevens gebruiken in DSC

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

Met de ingebouwde DSC **ConfigurationData** para meter kunt u gegevens definiëren die in een configuratie kunnen worden gebruikt.
Hierdoor kunt u één configuratie maken die kan worden gebruikt voor meerdere knoop punten of voor verschillende omgevingen.
Als u bijvoorbeeld een toepassing ontwikkelt, kunt u een configuratie gebruiken voor zowel ontwikkel-als productie omgevingen en configuratie gegevens gebruiken om gegevens op te geven voor elke omgeving.

In dit onderwerp wordt de structuur van de **ConfigurationData** hashtabel beschreven.
Zie [configuratie-en omgevings gegevens scheiden](separatingEnvData.md)voor voor beelden van het gebruik van configuratie gegevens.

## <a name="the-configurationdata-common-parameter"></a>De algemene para meter ConfigurationData

Een DSC-configuratie gebruikt een gemeen schappelijke para meter, **ConfigurationData**, die u opgeeft wanneer u de configuratie compileert.
Zie [DSC-configuraties](configurations.md)voor meer informatie over het compileren van configuraties.

De para meter **ConfigurationData** is een hashtabel die ten minste één sleutel met de naam **AllNodes**moet hebben.
Het kan ook een of meer andere sleutels hebben.

> [!NOTE]
> In de voor beelden in dit onderwerp wordt gebruikgemaakt van een enkele extra sleutel (met uitzonde ring van de benoemde **AllNodes** -sleutel) met de naam `NonNodeData`, maar u kunt een wille keurig aantal extra sleutels toevoegen en deze een naam geven wat u wilt.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

De waarde van de sleutel **AllNodes** is een matrix. Elk element van deze matrix is ook een hash-tabel die ten minste één sleutel met de naam **node**name moet hebben:

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

U kunt ook andere sleutels toevoegen aan elke hash-tabel:

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

Als u een eigenschap wilt Toep assen op alle knoop punten, kunt u een lid maken van de **AllNodes** -matrix met de **knooppunt** naam `*`.
U kunt bijvoorbeeld het volgende doen om elk knoop punt een `LogPath`-eigenschap te geven:

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

Dit is het equivalent van het toevoegen van een eigenschap met de naam `LogPath` met de waarde `"C:\Logs"` voor elk van de andere blokken (`VM-1`, `VM-2` en `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>De ConfigurationData hashtabel definiëren

U kunt **ConfigurationData** definiëren als een variabele binnen hetzelfde script bestand als een configuratie (zoals in de voor gaande voor beelden) of in een afzonderlijk `.psd1`-bestand.
Als u **ConfigurationData** wilt definiëren in een `.psd1`-bestand, maakt u een bestand dat alleen de hashtabel bevat die de configuratie gegevens vertegenwoordigt.

U kunt bijvoorbeeld een bestand met de naam `MyData.psd1` maken met de volgende inhoud:

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

## <a name="compiling-a-configuration-with-configuration-data"></a>Een configuratie met configuratie gegevens compileren

Als u een configuratie wilt compileren waarvoor u configuratie gegevens hebt gedefinieerd, geeft u de configuratie gegevens op als de waarde van de para meter **ConfigurationData** .

Hiermee maakt u een MOF-bestand voor elke vermelding in de **AllNodes** -matrix.
Elk MOF-bestand krijgt de naam van de eigenschap `NodeName` van de bijbehorende matrix vermelding.

Als u bijvoorbeeld configuratie gegevens definieert als in het bestand `MyData.psd1` hierboven, worden door het compileren van een configuratie zowel `VM-1.mof`-als `VM-2.mof`-bestanden gemaakt.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Een configuratie met configuratie gegevens compileren met behulp van een variabele

Als u configuratie gegevens wilt gebruiken die als een variabele zijn gedefinieerd in hetzelfde `.ps1`-bestand als de configuratie, geeft u de naam van de variabele door als de waarde van de **ConfigurationData** -para meter bij het compileren van de configuratie:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Een configuratie met configuratie gegevens compileren met behulp van een gegevens bestand

Als u configuratie gegevens wilt gebruiken die zijn gedefinieerd in een. psd1-bestand, geeft u het pad en de naam van het bestand door als de waarde van de para meter **ConfigurationData** bij het compileren van de configuratie:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>ConfigurationData-variabelen gebruiken in een configuratie

DSC biedt de volgende speciale variabelen die kunnen worden gebruikt in een configuratie script:

- **$AllNodes** verwijst naar de volledige verzameling knoop punten die in **ConfigurationData**zijn gedefinieerd. U kunt de **AllNodes** -verzameling filteren met behulp van **. WHERE ()** en **. ForEach ()** .
- **ConfigurationData** verwijst naar de volledige hash-tabel die wordt door gegeven als de para meter bij het compileren van een configuratie.
- **MyTypeName** bevat de [configuratie](configurations.md) naam waarin de variabele wordt gebruikt. In de configuratie `MyDscConfiguration` is de `$MyTypeName` bijvoorbeeld de waarde `MyDscConfiguration`.
- Het **knoop punt** verwijst naar een bepaalde vermelding in de **AllNodes** -verzameling nadat deze is gefilterd met behulp van **. WHERE ()** of **. ForEach ()** .
  - Meer informatie over deze methoden vindt u in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)

## <a name="using-non-node-data"></a>Niet-knooppunt gegevens gebruiken

Zoals we in eerdere voor beelden hebben gezien, kan de **ConfigurationData** hashtabel een of meer sleutels hebben naast de vereiste **AllNodes** -sleutel.
In de voor beelden in dit onderwerp hebben we slechts één extra knoop punt gebruikt, met de naam `NonNodeData`.
U kunt echter een wille keurig aantal extra sleutels definiëren en ze elke gewenste naam geven.

Zie [configuratie-en omgevings gegevens scheiden](separatingEnvData.md)voor een voor beeld van het gebruik van niet-knooppunt gegevens.

## <a name="see-also"></a>Zie ook

- [Referenties opties in configuratie gegevens](configDataCredentials.md)
- [DSC-configuraties](configurations.md)