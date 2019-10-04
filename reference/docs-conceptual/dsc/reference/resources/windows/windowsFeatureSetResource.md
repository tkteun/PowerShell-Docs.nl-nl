---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsFeatureSet-resource
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941248"
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet-resource

> Van toepassing op: Windows Power shell 5. x

De **WindowsFeatureSet** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat rollen en functies worden toegevoegd aan of verwijderd uit een doel knooppunt. Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [resource WindowsFeature](windowsfeatureResource.md) aanroept voor elk onderdeel dat is opgegeven in de eigenschap **name** .

Gebruik deze resource als u een aantal Windows-onderdelen wilt configureren met dezelfde status.

## <a name="syntax"></a>Syntaxis

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|  Eigenschap  |  Description   |
|---|---|
|Name |De namen van de functies of onderdelen die u wilt controleren, worden toegevoegd of verwijderd. Dit is hetzelfde als de **naam** eigenschap van de cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) en niet de weergave naam van de functies of onderdelen. |
|Source |Hiermee wordt de locatie aangegeven van het bron bestand dat moet worden gebruikt voor installatie, indien nodig. |
|IncludeAllSubFeature |Stel deze eigenschap in `$true` op om alle vereiste subonderdelen toe te voegen met de functies die u opgeeft met de eigenschap **naam** . |
|Referentie |De referenties die moeten worden gebruikt om de functies of onderdelen toe te voegen of te verwijderen. |
|Logboekpad |Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt aangegeven of de functies of onderdelen worden toegevoegd. Stel deze eigenschap in op **presen teren**om ervoor te zorgen dat de functies of onderdelen worden toegevoegd. Om ervoor te zorgen dat de functies of onderdelen worden verwijderd, stelt u de eigenschap in op **afwezig**. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

De volgende configuratie zorgt ervoor dat de functies van de **webserver** (IIS) en de **SMTP-server** , en alle subonderdelen van elke, worden geïnstalleerd.

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