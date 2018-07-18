---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Logboekresource
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093473"
---
# <a name="dsc-log-resource"></a>DSC-Logboekresource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De __Log__ resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het schrijven van berichten naar het gebeurtenislogboek van de Microsoft-Windows-Desired State Configuration / analysen.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Alleen de operationele logboeken voor DSC zijn standaard ingeschakeld. Voordat de analytische logboek beschikbaar of zichtbaar is, moet zijn ingeschakeld. Zie voor meer informatie, [waar zich de gebeurtenislogboeken DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Bericht| Geeft aan dat het bericht dat u wilt schrijven naar het gebeurtenislogboek Microsoft-Windows-Desired staat configuratie/analysen.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze logboekbericht wordt geschreven. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet hoe u een bericht opnemen in het gebeurtenislogboek Microsoft-Windows-Desired staat configuratie/analysen.

> [!NOTE]
> Als u [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) met deze resource geconfigureerd, wordt altijd geretourneerd **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```