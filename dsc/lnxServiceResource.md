---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxService-Resource
ms.openlocfilehash: ab6544762862c9b2477e92f0d782b13afb96f2c9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093565"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC voor Linux nxService-Resource

De **nxService** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van services op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Eigenschappen
|  Eigenschap |  Beschrijving |
|---|---|
| Naam| De naam van de service/daemon te configureren.|
| Domeincontroller| Het type servicecontroller te gebruiken bij het configureren van de service.|
| Ingeschakeld| Geeft aan of de service wordt gestart bij het opstarten.|
| Status| Geeft aan of de service wordt uitgevoerd. Deze eigenschap instellen op 'Stopped' om ervoor te zorgen dat de service niet wordt uitgevoerd. Stel deze in op "Uitvoeren" om ervoor te zorgen dat de service niet wordt uitgevoerd.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Als u meer informatie

De **nxService** resource niet maakt u een servicedefinitie of het script voor de service als deze niet bestaat. U kunt de PowerShell Desired State Configuration **nxFile** Resource resource voor het beheren van de aanwezigheid of de inhoud van het servicedefinitiebestand of script.

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u configuratie van de service 'httpd' (voor Apache HTTP Server), geregistreerd bij de **SystemD** servicecontroller.

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```