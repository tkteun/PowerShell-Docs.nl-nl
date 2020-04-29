---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WaitForAll-resource
ms.openlocfilehash: 1bdaa63812766cfe5ec0778ef07689109683b994
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941290"
---
# <a name="dsc-waitforall-resource"></a>DSC WaitForAll-resource

> Van toepassing op: Windows Power shell 5. x

De resource van de desired state Configuration (DSC) **WaitForAll** kan worden gebruikt binnen een knooppunt blok in een [DSC-configuratie](../../../configurations/configurations.md) om afhankelijkheden op te geven voor de configuraties op andere knoop punten.

Deze resource slaagt als de resource die is opgegeven door de eigenschap **ResourceName** de gewenste status heeft voor alle doel knooppunten die zijn gedefinieerd in de eigenschap **nodenaam** .

> [!NOTE]
> **WaitForAll** -resource maakt gebruik van Windows Remote Management om de status van andere knoop punten te controleren. Zie [beveiligings overwegingen voor externe communicatie van Power shell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)voor meer informatie over de vereisten voor de poort en de beveiliging van WinRM.

## <a name="syntax"></a>Syntaxis

```Syntax
WaitForAll [string] #ResourceName
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
|ResourceName |De resource naam waarvan afhankelijk is. Als deze resource deel uitmaakt van een andere configuratie, moet u `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`de naam indelen als. |
|NodeName |De doel knooppunten van de resource waarvan afhankelijk is. |
|RetryIntervalSec |Het aantal seconden voordat een nieuwe poging wordt gedaan. De minimum waarde is 1. |
|RetryCount |Het maximum aantal keren dat opnieuw moet worden geprobeerd. |
|ThrottleLimit |Aantal machines om tegelijkertijd verbinding te maken. Standaard instelling `New-CimSession` is standaard. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

Zie [afhankelijkheden van meerdere knoop punten opgeven](../../../configurations/crossNodeDependencies.md) voor een voor beeld van het gebruik van deze bron.