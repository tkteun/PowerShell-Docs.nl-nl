---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Bron van het DSC-Service
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048177"
---
# <a name="dsc-service-resource"></a>Bron van het DSC-Service

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0


De **Service** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van services op het doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Geeft de servicenaam. Houd er rekening mee dat soms dit af van de weergavenaam wijkt. U krijgt een overzicht van de services en de huidige status hiervan met de cmdlet Get-Service.|
| BuiltInAccount| Geeft aan dat de aanmeldingsaccount gebruiken voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.|
| Referentie| Geeft aan dat referenties voor het account waaronder de service wordt uitgevoerd. Deze eigenschap en de __BuiltinAccount__ eigenschap samen kan worden gebruikt.|
| DependsOn| Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Opstarttype van| Geeft aan dat het opstarttype voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **Automatische**, **uitgeschakelde**, en **handmatig**|
| Status| Geeft de status die u wilt om ervoor te zorgen voor de service.|
| Beschrijving | Geeft aan dat de beschrijving van de doelservice.|
| DisplayName | Geeft de naam van de doelservice.|
| Zorg ervoor dat | Geeft aan of de doelservice op het systeem bestaat. Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de doelservice niet bestaat. Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservice bestaat.|
| Pad | Geeft het pad naar het binaire bestand voor een nieuwe service.|

## <a name="example"></a>Voorbeeld

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```