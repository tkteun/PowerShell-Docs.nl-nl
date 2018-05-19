---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsFeature-Resource
ms.openlocfilehash: ece77043d3a4131150b934a19ee8b92dd75c48f0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsfeature-resource"></a>DSC-WindowsFeature-Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat functies en onderdelen worden toegevoegd of verwijderd in een doelknooppunt.

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
| Naam| Hiermee geeft u de naam van de rol of functie die u wilt zorgen toegevoegd of verwijderd. Dit is hetzelfde als de __naam__ eigenschap uit de [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, en niet de weergavenaam van de rol of functie.|
| referentie| Hiermee geeft u de referenties toevoegen of verwijderen van de rol of functie.|
| Zorg ervoor dat| Hiermee wordt aangegeven of de rol of functie is toegevoegd. Om ervoor te zorgen dat de rol of functie is toegevoegd, stel deze eigenschap in op 'Aanwezig' om ervoor te zorgen dat de rol of functie wordt verwijderd, de eigenschap instellen op 'Afwezig'.|
| IncludeAllSubFeature| Deze eigenschap instellen op __$true__ om te controleren of de status van alle vereiste subonderdelen met de status van de functie die u met opgeeft de __naam__ eigenschap.|
| Logboekpad| Geeft het pad naar een logboekbestand waar u de resourceprovider aan te melden van de bewerking.|
| dependsOn| Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Bron| Geeft de locatie van het bronbestand moet worden gebruikt voor de installatie, indien nodig.|

## <a name="example"></a>Voorbeeld
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```