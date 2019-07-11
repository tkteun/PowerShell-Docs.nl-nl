---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WaitForAll Resource
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726876"
---
# <a name="dsc-waitforall-resource"></a>DSC WaitForAll Resource

> Van toepassing op: Windows PowerShell 5.0 en hoger

De **WaitForAll** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](../../../configurations/configurations.md) afhankelijkheden opgeven voor configuraties op andere knooppunten.

Deze resource is geslaagd als de resource die is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status van alle doelknooppunten gedefinieerd in de **knooppuntnaam** eigenschap.

> [!NOTE]
> **WaitForAll** resource maakt gebruik van Windows Remote Management om te controleren of de status van andere knooppunten.
> Zie voor meer informatie over de poort en beveiligingsvereisten voor WinRM [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="syntax"></a>Syntaxis

```
WaitForAll [string] #ResourceName
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

|  Eigenschap  |  Description   |
|---|---|
| ResourceName| De naam van de resource afhankelijk. Als deze resource tot een andere configuratie behoort, maakt u de naam op als ' [__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "|
| NodeName| De doelknooppunten van de resource afhankelijk.|
| RetryIntervalSec| Het aantal seconden alvorens het opnieuw te proberen. Minimumwaarde is 1.|
| RetryCount| Het maximale aantal nieuwe pogingen.|
| ThrottleLimit| Het aantal machines tegelijk verbinding kunnen maken. Standaard is de nieuwe-cimsession standaard.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Zie voor een voorbeeld van het gebruik van deze resource [afhankelijkheden van meerdere knooppunten opgeven](../../../configurations/crossNodeDependencies.md)
