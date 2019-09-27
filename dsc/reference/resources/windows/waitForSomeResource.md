---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WaitForSome-resource
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324017"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome-resource

> Van toepassing op: Windows Power shell 5. x

De resource van de desired state Configuration (DSC) **WaitForSome** kan worden gebruikt binnen een knooppunt blok in een [DSC-configuratie](../../../configurations/configurations.md) om afhankelijkheden op te geven voor de configuraties op andere knoop punten.

Deze resource slaagt als de resource die is opgegeven door de eigenschap **ResourceName** de gewenste status heeft voor een minimum aantal knoop punten (opgegeven door **NodeCount**) dat is gedefinieerd door de eigenschap **nodenaam** .

> [!NOTE]
> **WaitForSome** -resource maakt gebruik van Windows Remote Management om de status van andere knoop punten te controleren. Zie [beveiligings overwegingen voor externe communicatie van Power shell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)voor meer informatie over de vereisten voor de poort en de beveiliging van WinRM.

## <a name="syntax"></a>Syntaxis

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|NodeCount |Het minimum aantal knoop punten dat in de gewenste status voor deze resource moet worden uitgevoerd. |
|NodeName |De doel knooppunten van de resource waarvan afhankelijk is. |
|ResourceName |De resource naam waarvan afhankelijk is. Als deze resource deel uitmaakt van een andere configuratie, moet u `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`de naam indelen als. |
|RetryIntervalSec |Het aantal seconden voordat een nieuwe poging wordt gedaan. De minimum waarde is 1. |
|retryCount |Het maximum aantal keren dat opnieuw moet worden geprobeerd. |
|ThrottleLimit |Aantal machines om tegelijkertijd verbinding te maken. Standaard instelling `New-CimSession` is standaard. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

Zie [afhankelijkheden van meerdere knoop punten opgeven](../../../configurations/crossNodeDependencies.md) voor een voor beeld van het gebruik van deze bron.