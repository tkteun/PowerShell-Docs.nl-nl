---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxService-Resource
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077686"
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

| Eigenschap | Description |
|---|---|
| Naam| De naam van de service/daemon te configureren.|
| Controller| Het type servicecontroller te gebruiken bij het configureren van de service.|
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