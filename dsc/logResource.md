---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Logboek van de DSC-Resource
ms.openlocfilehash: 3bc4bf38b376cc62e42107eee1024eaabc93485a
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-log-resource"></a>Logboek van de DSC-Resource 

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De __logboek__ in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor berichten schrijven naar het gebeurtenislogboek van de Microsoft-Windows-gewenst status Configuration/analysen.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

Opmerking: Standaard alleen de operationele logboeken voor DSC zijn ingeschakeld.
Voordat het analytische logboek beschikbaar of zichtbaar is, moet zijn ingeschakeld.
Zie het volgende artikel.

[Waar zijn de gebeurtenislogboeken DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Eigenschappen
|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Bericht| Hiermee geeft u het bericht dat u wilt schrijven naar het gebeurtenislogboek Microsoft-Windows-Desired status Configuration/analysen.| 
| dependsOn | Geeft aan dat de configuratie van een andere resource moet worden uitgevoerd voordat dit logboekbericht wordt geschreven. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld laat zien hoe een bericht in het gebeurtenislogboek Microsoft-Windows-Desired status Configuration/analysen opnemen.

> **Opmerking**: als u [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aan deze resource is geconfigureerd, wordt altijd geretourneerd **$false**.

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

