---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForSome Resource
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726767"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome Resource

> Van toepassing op: Windows PowerShell 5.0 en hoger

De **WaitForSome** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.

Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status op een minimum aantal knooppunten (opgegeven door **NodeCount**) gedefinieerd door de **knooppuntnaam**  eigenschap.

> [!NOTE]
> **WaitForSome** resource maakt gebruik van Windows Remote Management om te controleren of de status van andere knooppunten.
> Zie voor meer informatie over de poort en beveiligingsvereisten voor WinRM [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

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

|  Eigenschap  |  Description   |
|---|---|
| NodeCount| Het minimum aantal knooppunten dat in de gewenste status voor deze resource worden moet te voltooien.|
| NodeName| De doelknooppunten van de resource afhankelijk.|
| ResourceName| De naam van de resource afhankelijk. Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| RetryIntervalSec| Het aantal seconden alvorens het opnieuw te proberen. Minimumwaarde is 1.|
| RetryCount| Het maximale aantal nieuwe pogingen.|
| ThrottleLimit| Het aantal machines tegelijk verbinding kunnen maken. Standaard is de nieuwe-cimsession standaard.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Zie [DSC gebruiken met de referenties van gebruiker](https://docs.microsoft.com/powershell/dsc/runasuser) |

## <a name="example"></a>Voorbeeld

Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)
