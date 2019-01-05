---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForAny Resource
ms.openlocfilehash: 39e90f0df3459b8891ed46e02ae82c45a285e7f5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048285"
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny Resource

> Van toepassing op: Windows PowerShell 5.1 of hoger

De **WaitForSome** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.

Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op een doelknooppunten dat is gedefinieerd in de **knooppuntnaam** eigenschap.


## <a name="syntax"></a>Syntaxis

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| ResourceName| De naam van de resource afhankelijk. Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| Knooppuntnaam| De doelknooppunten van de resource afhankelijk.|
| RetryIntervalSec| Het aantal seconden alvorens het opnieuw te proberen. Minimumwaarde is 1.|
| retryCount| Het maximale aantal nieuwe pogingen.|
| ThrottleLimit| Het aantal machines tegelijk verbinding kunnen maken. Standaard is de nieuwe-cimsession standaard.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)
