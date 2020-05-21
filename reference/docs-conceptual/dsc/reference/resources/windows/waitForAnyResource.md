---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WaitForAny-resource
ms.openlocfilehash: 181760ba0a4f493c451dafb68e7881adda2d58c0
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560777"
---
# <a name="dsc-waitforany-resource"></a>DSC WaitForAny-resource

> Van toepassing op: Windows Power shell 5,1

De resource van de desired state Configuration (DSC) **WaitForAny** kan worden gebruikt binnen een knooppunt blok in een [DSC-configuratie](../../../configurations/configurations.md) om afhankelijkheden op te geven voor de configuraties op andere knoop punten.

Deze resource slaagt als de resource die is opgegeven door de eigenschap **ResourceName** de gewenste status heeft op een doel knooppunt dat is gedefinieerd in de eigenschap **nodenaam** .

> [!NOTE]
> **WaitForAny** -resource maakt gebruik van Windows Remote Management om de status van andere knoop punten te controleren. Zie [beveiligings overwegingen voor externe communicatie van Power shell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)voor meer informatie over de vereisten voor de poort en de beveiliging van WinRM.

## <a name="syntax"></a>Syntaxis

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|ResourceName |De resource naam waarvan afhankelijk is. Als deze resource deel uitmaakt van een andere configuratie, moet u de naam indelen als `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]` . |
|NodeName |De doel knooppunten van de resource waarvan afhankelijk is. |
|RetryIntervalSec |Het aantal seconden voordat een nieuwe poging wordt gedaan. De minimum waarde is 1. |
|RetryCount |Het maximum aantal keren dat opnieuw moet worden geprobeerd. |
|ThrottleLimit |Aantal machines om tegelijkertijd verbinding te maken. Standaard instelling is `New-CimSession` standaard. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

Zie [afhankelijkheden van meerdere knoop punten opgeven](../../../configurations/crossNodeDependencies.md) voor een voor beeld van het gebruik van deze bron.
