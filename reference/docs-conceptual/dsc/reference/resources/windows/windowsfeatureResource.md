---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-WindowsFeature-resource
ms.openlocfilehash: 7f9b200b4d10aef6c8a3f76c497f4d60e8062cb5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557394"
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

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Name |Hiermee wordt de naam aangegeven van de functie of het onderdeel dat u wilt garanderen, wordt toegevoegd of verwijderd. Dit is hetzelfde als de **naam** eigenschap van de cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) en niet de weergave naam van de functie of het onderdeel. |
|Referentie |Hiermee geeft u de referenties op die moeten worden gebruikt om de functie of het onderdeel toe te voegen of te verwijderen. |
|IncludeAllSubFeature |Stel deze eigenschap in op `$true` om de status van alle vereiste subonderdelen met de status van de functie die u opgeeft met de eigenschap **name** te controleren. |
|Logboekpad |Hiermee geeft u het pad naar een logboek bestand op waar de resource provider de bewerking moet registreren. |
|Bron |Hiermee wordt de locatie aangegeven van het bron bestand dat moet worden gebruikt voor installatie, indien nodig. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
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
