---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxService-resource
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324644"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC voor Linux nxService-resource

De **nxService** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op een Linux-knoop punt.

## <a name="syntax"></a>Syntaxis

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Name |De naam van de service/daemon die moet worden geconfigureerd. |
|Regelaar |Het type service controller dat moet worden gebruikt bij het configureren van de service. |
|Enabled |Hiermee wordt aangegeven of de service wordt gestart bij het opstarten. |
|State |Hiermee wordt aangegeven of de service wordt uitgevoerd. Stel deze eigenschap in op **gestopt** om er zeker van te zijn dat de service niet wordt uitgevoerd. Stel deze in op **wordt uitgevoerd** om ervoor te zorgen dat de service wordt uitgevoerd. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |

## <a name="additional-information"></a>Als u meer informatie

Met de **nxService** -resource wordt geen service definitie of script voor de service gemaakt als deze niet bestaat. U kunt de Power shell desired state Configuration **nxFile** resource Resource gebruiken om het bestaan of de inhoud van het service definitie bestand of-script te beheren.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u de configuratie van de ' httpd-service (voor Apache HTTP-server) die is geregistreerd bij de **Gesystemde** service controller.

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```