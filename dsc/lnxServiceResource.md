---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxService Resource
ms.openlocfilehash: b02fb1153570f628682533cb57a7d429e5cc8762
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC voor Linux nxService Resource

De **nxService** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van services op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen
|  Eigenschap |  Beschrijving |
|---|---|
| Naam| De naam van de service /-daemon te configureren.|
| Controller| Het type servicecontroller moet worden gebruikt bij het configureren van de service.|
| Ingeschakeld| Hiermee wordt aangegeven of de service wordt gestart bij het opstarten.|
| Status| Hiermee wordt aangegeven of de service wordt uitgevoerd. Stel deze eigenschap op 'Gestopt' om ervoor te zorgen dat de service niet wordt uitgevoerd. Stel deze in op 'Uitvoeren' om ervoor te zorgen dat de service niet wordt uitgevoerd.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="additional-information"></a>Als u meer informatie

De **nxService** resource niet maakt een servicedefinitie of het script voor de service als deze niet bestaat. Kunt u PowerShell Desired State Configuration **nxFile** Resource resource voor het beheren van de aanwezigheid of de inhoud van het servicedefinitiebestand of script.

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u configuratie van de service 'httpd' (voor Apache HTTP-Server), geregistreerd bij de **SystemD** service-controller.

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```