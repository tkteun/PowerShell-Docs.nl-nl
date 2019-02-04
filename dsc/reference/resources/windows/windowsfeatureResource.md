---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-WindowsFeature-Resource
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685968"
---
# <a name="dsc-windowsfeature-resource"></a>DSC-WindowsFeature-Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat functies en onderdelen worden toegevoegd of verwijderd op een doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Geeft aan dat de naam van de functie of onderdeel dat u wilt ervoor zorgen is toegevoegd of verwijderd. Dit is hetzelfde als de __naam__ eigenschap uit de [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, en niet de weergavenaam van de rol of functie.|
| Referentie| Geeft aan dat de referenties voor het toevoegen of verwijderen van de rol of functie gebruiken.|
| Zorg ervoor dat| Hiermee wordt aangegeven als de functie of onderdeel is toegevoegd. Om ervoor te zorgen dat de rol of functie is toegevoegd, stel deze eigenschap in op 'Aanwezig' om ervoor te zorgen dat de rol of functie wordt verwijderd, de eigenschap instellen op 'Ontbreekt'.|
| IncludeAllSubFeature| Deze eigenschap instellen op __$true__ om te controleren of de status van alle vereiste subonderdelen met de status van de functie die u met opgeeft de __naam__ eigenschap.|
| Logboekpad| Geeft het pad naar een logboekbestand waar u de resourceprovider voor aanmelding van de bewerking.|
| DependsOn| Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Bron| Geeft de locatie van het bronbestand moet worden gebruikt voor installatie, indien nodig.|

## <a name="example"></a>Voorbeeld
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```