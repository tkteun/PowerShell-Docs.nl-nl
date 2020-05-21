---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsFeatureSet-resource
ms.openlocfilehash: 4707616b23a125e49e17031e0b75fd3cde4b9a3d
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565414"
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

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
|Name |De namen van de functies of onderdelen die u wilt controleren, worden toegevoegd of verwijderd. Dit is hetzelfde als de **naam** eigenschap van de cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) en niet de weergave naam van de functies of onderdelen. |
|Bron |Hiermee wordt de locatie aangegeven van het bron bestand dat moet worden gebruikt voor installatie, indien nodig. |
|IncludeAllSubFeature |Stel deze eigenschap in op `$true` om alle vereiste subonderdelen toe te voegen met de functies die u opgeeft met de eigenschap **naam** . |
|Referentie |De referenties die moeten worden gebruikt om de functies of onderdelen toe te voegen of te verwijderen. |
|Logboekpad |Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
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
