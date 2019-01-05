---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForSome Resource
ms.openlocfilehash: 906375a8fcf9b87d4b7487e63e6fae3f05b86d0d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048179"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome Resource

> Van toepassing op: Windows PowerShell 5.0 en hoger

De **WaitForAny** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.

Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op een minimum aantal knooppunten (opgegeven door **NodeCount**) gedefinieerd door de **knooppuntnaam**  eigenschap.


## <a name="syntax"></a>Syntaxis

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| NodeCount| Het minimum aantal knooppunten dat in de gewenste status voor deze resource worden moet te voltooien.|
| Knooppuntnaam| De doelknooppunten van de resource afhankelijk.|
| ResourceName| De naam van de resource afhankelijk. Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| RetryIntervalSec| Het aantal seconden alvorens het opnieuw te proberen. Minimumwaarde is 1.|
| retryCount| Het maximale aantal nieuwe pogingen.|
| ThrottleLimit| Het aantal machines tegelijk verbinding kunnen maken. Standaard is de nieuwe-cimsession standaard.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Zie [DSC gebruiken met de referenties van gebruiker](https://docs.microsoft.com/powershell/dsc/runasuser) |

## <a name="example"></a>Voorbeeld

Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)
