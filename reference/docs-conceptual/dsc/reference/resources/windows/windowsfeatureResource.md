---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-WindowsFeature-resource
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942417"
---
# <a name="dsc-windowsfeature-resource"></a>DSC-WindowsFeature-resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De resource **WindowsFeature** in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat rollen en functies worden toegevoegd aan of verwijderd uit een doel knooppunt.

## <a name="syntax"></a>Syntaxis

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Name |Hiermee wordt de naam aangegeven van de functie of het onderdeel dat u wilt garanderen, wordt toegevoegd of verwijderd. Dit is hetzelfde als de **naam** eigenschap van de cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) en niet de weergave naam van de functie of het onderdeel. |
|Referentie |Hiermee geeft u de referenties op die moeten worden gebruikt om de functie of het onderdeel toe te voegen of te verwijderen. |
|IncludeAllSubFeature |Stel deze eigenschap in `$true` op om de status van alle vereiste subonderdelen met de status van de functie die u opgeeft met de eigenschap **name** te controleren. |
|Logboekpad |Hiermee geeft u het pad naar een logboek bestand op waar de resource provider de bewerking moet registreren. |
|Source |Hiermee wordt de locatie aangegeven van het bron bestand dat moet worden gebruikt voor installatie, indien nodig. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt aangegeven of de functie of het onderdeel is toegevoegd. Stel deze eigenschap in op **aanwezig**om te controleren of de functie of het onderdeel is toegevoegd. Om ervoor te zorgen dat de functie of het onderdeel wordt verwijderd, stelt u de eigenschap in op **afwezig**. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```