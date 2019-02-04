---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WindowsFeatureSet-Resource
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684792"
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet-Resource

> Van toepassing op: Windows PowerShell 5.0

De **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat functies en onderdelen worden toegevoegd of verwijderd op een doelknooppunt.
Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [WindowsFeature-resource](windowsfeatureResource.md) voor elke functie die is opgegeven in de `Name` eigenschap.

Gebruik deze resource als u wilt configureren van een aantal functies van Windows naar dezelfde toestand.

## <a name="syntax"></a>Syntaxis

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| De namen van de functies of onderdelen die u wilt ervoor zorgen worden toegevoegd of verwijderd. Dit is hetzelfde als de **naam** eigenschap van de [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, en niet de weergavenaam van de functies of onderdelen.|
| Referentie| De referenties voor het toevoegen of verwijderen van de functies of onderdelen.|
| Zorg ervoor dat| Geeft aan of de functies of onderdelen worden toegevoegd. Om ervoor te zorgen dat de functies of onderdelen zijn toegevoegd, stel deze eigenschap in op 'Aanwezig' om ervoor te zorgen dat de functies of onderdelen zijn verwijderd, de eigenschap instellen op 'Ontbreekt'.|
| IncludeAllSubFeature| Deze eigenschap instellen op **$true** om op te nemen van alle vereiste subonderdelen met van de functies die u met opgeeft de **naam** eigenschap.|
| Logboekpad| Het pad naar een logboekbestand waar u de resourceprovider voor aanmelding van de bewerking.|
| DependsOn| Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Bron| Geeft de locatie van het bronbestand moet worden gebruikt voor installatie, indien nodig.|

## <a name="example"></a>Voorbeeld

De volgende configuratie zorgt ervoor dat de **-webserver** (IIS) en **SMTP-Server** functies en alle subfuncties van elk, worden geïnstalleerd.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
