---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Logboekresource
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077225"
---
# <a name="dsc-log-resource"></a>DSC-Logboekresource

> _Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0_

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
> Alleen de operationele logboeken voor DSC zijn standaard ingeschakeld. Voordat de analytische logboek beschikbaar of zichtbaar is, moet zijn ingeschakeld. Zie voor meer informatie, [waar zich de gebeurtenislogboeken DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Eigenschappen

| Eigenschap | Description |
| --- | --- |
| Bericht| Geeft aan dat het bericht dat u wilt schrijven naar het gebeurtenislogboek Microsoft-Windows-Desired staat configuratie/analysen.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze logboekbericht wordt geschreven. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = '[ResourceType]ResourceName'`.|

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
