---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Afhankelijkheden van meerdere knooppunten opgeven
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080200"
---
# <a name="specifying-cross-node-dependencies"></a>Afhankelijkheden van meerdere knooppunten opgeven

> Van toepassing op: Windows PowerShell 5.0

DSC biedt speciale resources **WaitForAll**, **WaitForAny**, en **WaitForSome** die kunnen worden gebruikt in configuraties met afhankelijkheden opgeven voor configuraties op andere knooppunten. Het gedrag van deze resources is als volgt:

- **WaitForAll**: Is geslaagd als de opgegeven resource in de gewenste status van alle doelknooppunten gedefinieerd is in de **knooppuntnaam** eigenschap.
- **WaitForAny**: Is geslaagd als de opgegeven resource in de gewenste status op ten minste één van de doelknooppunten gedefinieerd is in de **knooppuntnaam** eigenschap.
- **WaitForSome**: Hiermee geeft u een **NodeCount** eigenschap naast een **knooppuntnaam** eigenschap. De resource is geslaagd als de resource in de gewenste status op een minimum aantal knooppunten is (opgegeven door **NodeCount**) gedefinieerd door de **knooppuntnaam** eigenschap.

## <a name="syntax"></a>Syntaxis

De **WaitForAll** en **WaitForAny** resources delen dezelfde syntaxis. Vervang \<ResourceType\> in het onderstaande voorbeeld met ofwel **WaitForAny** of **WaitForAll**.
Net als de **DependsOn** trefwoord, moet u de naam als 'ResourceName [ResourceType]'. Als de resource deel uitmaakt van een afzonderlijke [configuratie](configurations.md), bevatten de **ConfigurationName** in de opgemaakte tekenreeks "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName] '. De **knooppuntnaam** is de computer, of het knooppunt waarop de huidige bron moet wachten.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

De **WaitForSome** resource heeft een vergelijkbare syntaxis in het bovenstaande voorbeeld, maar voegt de **NodeCount** sleutel. De **NodeCount** geeft aan hoeveel knooppunten die de huidige bron moet worden gewacht op.

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

Alle **WaitForXXXX** delen van de volgende syntaxis van de sleutels.

|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying. Minimumwaarde is 1. | | RetryCount | Het maximum aantal nieuwe pogingen. | | ThrottleLimit | Het aantal machines tegelijk verbinding kunnen maken. De standaardwaarde is `New-CimSession` standaard. | | DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Zie voor meer informatie, [DependsOn](resource-depends-on.md)|| PsDscRunAsCredential | Zie [DSC gebruiken met de referenties van gebruiker](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Met behulp van WaitForXXXX bronnen

Elke **WaitForXXXX** resource wacht tot de opgegeven bronnen voor het opgegeven knooppunt. Andere resources in dezelfde configuratie kunnen vervolgens *afhankelijk zijn van* de **WaitForXXXX** resource met behulp van de **DependsOn** sleutel.

Bijvoorbeeld, in de volgende configuratie, het doelknooppunt wordt gewacht tot de **xADDomain** resource moet worden voltooid op de **Eigendc** knooppunt met een maximum van 30 nieuwe pogingen, met intervallen van 15 seconden, voordat de doelknooppunt kan deelnemen aan het domein.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Wanneer u de configuratie compileren, worden "twee MOF-bestanden gegenereerd. Beide ".mof" bestanden van toepassing op de doelknooppunten met behulp van de [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**Opmerking:** Standaard de WaitForXXX resources één keer proberen en voert vervolgens failover uit. Hoewel het niet vereist is, zult u doorgaans om op te geven een **RetryCount** en **RetryIntervalSec**.

## <a name="see-also"></a>Zie ook

- [DSC-configuraties](configurations.md)
- [Resource-afhankelijkheden](resource-depends-on.md)
- [DSC-Resources](../resources/resources.md)
- [De Local Configuration Manager configureren](../managing-nodes/metaConfig.md)
