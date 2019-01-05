---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC ServiceSet-Resource
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048182"
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet-Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van services op het doelknooppunt. Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [Service resource](serviceResource.md) voor elke service die is opgegeven in de `Name` eigenschap.

Gebruik deze resource als u wilt configureren van een aantal services naar dezelfde toestand.

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
| Naam| Geeft aan dat de servicenamen van de. Houd er rekening mee dat soms dit af van de weergavenamen wijkt. U krijgt een overzicht van de services en de huidige status hiervan met de [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.|
| Opstarttype van| Geeft aan dat het opstarttype voor de service. De waarden die zijn toegestaan voor deze eigenschap zijn: **Automatische**, **uitgeschakelde**, en **handmatig**|
| BuiltInAccount| Geeft aan dat de aanmeldingsaccount gebruiken voor de services. De waarden die zijn toegestaan voor deze eigenschap zijn: **LocalService**, **LocalSystem**, en **NetworkService**.|
| Status| Hiermee geeft u de status die u wilt om ervoor te zorgen voor de services: **Gestopt** of **met**.|
| Zorg ervoor dat| Geeft aan of de services op het systeem zijn. Deze eigenschap instellen op **afwezig** om ervoor te zorgen dat de services niet bestaan. Instellen op **aanwezig** (de standaardwaarde) zorgt ervoor dat de doelservices bestaan.|
| Referentie| Geeft aan dat de referenties voor het account dat de bron van de service wordt uitgevoerd onder. Deze eigenschap en de **BuiltinAccount** eigenschap samen kan worden gebruikt.|
| DependsOn| Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is *ResourceName* en het type *ResourceType*, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|



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
