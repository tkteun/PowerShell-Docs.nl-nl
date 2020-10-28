---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxService-resource
description: DSC voor Linux nxService-resource
ms.openlocfilehash: 4eefe491c491c9245732def1cc85260f368ef9e1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648791"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC voor Linux nxService-resource

De **nxService** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van services op een Linux-knoop punt.

## <a name="syntax"></a>Syntax

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

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |De naam van de service/daemon die moet worden geconfigureerd. |
|Regelaar |Het type service controller dat moet worden gebruikt bij het configureren van de service. |
|Ingeschakeld |Hiermee wordt aangegeven of de service wordt gestart bij het opstarten. |
|Staat |Hiermee wordt aangegeven of de service wordt uitgevoerd. Stel deze eigenschap in op **gestopt** om er zeker van te zijn dat de service niet wordt uitgevoerd. Stel deze in op **wordt uitgevoerd** om ervoor te zorgen dat de service wordt uitgevoerd. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |

## <a name="additional-information"></a>Aanvullende informatie

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
