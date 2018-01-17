---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC Service Resource
ms.openlocfilehash: a549530edc19496a68c036fecbd18b0072cc6d74
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-service-resource"></a>DSC Service Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0


De **Service** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van services in het doelknooppunt.

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
| Naam| Geeft de servicenaam. Houd er rekening mee dat soms dit van de weergegeven naam verschilt. U kunt een lijst van de services en de huidige staat met de cmdlet Get-Service ophalen.| 
| BuiltInAccount| Hiermee geeft u het account aanmelden om te gebruiken voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.| 
| referentie| Hiermee geeft u referenties voor het account waaronder de service wordt uitgevoerd. Deze eigenschap en de __BuiltinAccount__ eigenschap kan niet samen worden gebruikt.| 
| dependsOn| Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 
| StartupType| Hiermee geeft het opstarttype voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **automatische**, **uitgeschakelde**, en **handmatig**| 
| Status| Geeft de status die u wilt zorgen voor de service.| 
| Beschrijving | Hiermee geeft u de beschrijving van de doelservice.| 
| DisplayName | Geeft de naam van de doelservice.| 
| Zorg ervoor dat | Hiermee wordt aangegeven of de doelservice op het systeem bestaat. Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de doelservice niet bestaat. Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservice bestaat.|
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

