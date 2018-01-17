---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC ServiceSet Resource
ms.openlocfilehash: 9556a1d513c3819a36c1161e3b35388ca1eb66f9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0


De **ServiceSet** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van services in het doelknooppunt. Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [Service resource](serviceResource.md) voor elke service die is opgegeven in de `Name` eigenschap.

Gebruik deze bron als u wilt configureren, een aantal services naar dezelfde toestand.

## <a name="syntax"></a>Syntaxis

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Naam| Hiermee geeft u de servicenamen van de. Houd er rekening mee dat soms dit van de weergavenamen verschilt. U krijgt een lijst van de services en de huidige staat met de [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet.|
| StartupType| Hiermee geeft het opstarttype voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **automatische**, **uitgeschakelde**, en **handmatig**|  
| BuiltInAccount| Hiermee geeft u het aanmeldingsaccount voor de services. De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.| 
| Status| Geeft de status die u wilt zorgen voor de services: **gestopt** of **met**.| 
| Zorg ervoor dat| Geeft aan of de services op het systeem zijn. Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de services niet bestaan. Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservices bestaat.|
| referentie| Hiermee geeft u referenties voor het account waaronder resource voor de service wordt uitgevoerd. Deze eigenschap en de **BuiltinAccount** eigenschap kan niet samen worden gebruikt.| 
| dependsOn| Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is *ResourceName* en het type *ResourceType*, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 



## <a name="example"></a>Voorbeeld

De volgende configuratie start de services 'Windows Audio' en 'Extern bureaublad-Services'.

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

