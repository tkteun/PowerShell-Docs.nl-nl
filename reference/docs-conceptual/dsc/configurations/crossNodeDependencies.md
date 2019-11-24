---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Afhankelijkheden van meerdere knooppunten opgeven
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942053"
---
# <a name="specifying-cross-node-dependencies"></a>Afhankelijkheden van meerdere knooppunten opgeven

> Van toepassing op: Windows Power shell 5,0

DSC biedt speciale resources, **WaitForAll**, **WaitForAny**en **WaitForSome** die in configuraties kunnen worden gebruikt om afhankelijkheden op te geven voor configuraties op andere knoop punten. Het gedrag van deze resources is als volgt:

- **WaitForAll**: slaagt als de opgegeven resource de gewenste status heeft op alle doel knooppunten die zijn gedefinieerd in de eigenschap **nodenaam** .
- **WaitForAny**: slaagt als de opgegeven resource de gewenste status heeft op ten minste één van de doel knooppunten die zijn gedefinieerd in de eigenschap **nodenaam** .
- **WaitForSome**: Hiermee geeft u een eigenschap **NodeCount** op in aanvulling op de eigenschap **nodenaam** . De resource slaagt als de resource de gewenste status heeft voor een minimum aantal knoop punten (opgegeven door **NodeCount**) dat is gedefinieerd door de eigenschap **nodenaam** .

## <a name="syntax"></a>Syntaxis

De **WaitForAll** -en **WaitForAny** -resources delen dezelfde syntaxis. Vervang \<resource type\> in het onderstaande voor beeld met een **WaitForAny** of **WaitForAll**.
Net als het sleutel woord **DependsOn** moet u de naam als ' [resource type] ResourceName ' Format teren. Als de resource deel uitmaakt van een afzonderlijke [configuratie](configurations.md), neemt u de **configuratiepad** op in de opgemaakte teken reeks ' [resource type] ResourceName:: [configuratiepad]:: [configuratiepad] '. De **knooppunt** naam is de computer of het knoop punt waarop de huidige resource moet wachten.

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

De **WaitForSome** -resource heeft een vergelijk bare syntaxis voor het bovenstaande voor beeld, maar voegt de **NodeCount** -sleutel toe. De **NodeCount** geeft aan hoeveel knoop punten de huidige resource moet wachten.

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

Alle **WaitForXXXX** delen de volgende syntaxis sleutels.

|Eigenschap|  Beschrijving   |
|---------|---------------------|
| RetryIntervalSec| Het aantal seconden voordat een nieuwe poging wordt gedaan. De minimum waarde is 1.|
| RetryCount| Het maximum aantal keren dat opnieuw moet worden geprobeerd.|
| ThrottleLimit| Aantal machines om tegelijkertijd verbinding te maken. De standaard instelling is `New-CimSession` standaard waarde.|
| DependsOn | Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Zie [DependsOn](resource-depends-on.md) voor meer informatie.|
| PsDscRunAsCredential | Zie [DSC gebruiken met gebruikers referenties](./runAsUser.md) |

## <a name="using-waitforxxxx-resources"></a>WaitForXXXX-resources gebruiken

Elke **WaitForXXXX** -resource wacht totdat de opgegeven resources zijn voltooid op het opgegeven knoop punt.
Andere resources in dezelfde configuratie kunnen vervolgens *afhankelijk zijn* van de **WaitForXXXX** -bron met behulp van de **DependsOn** -sleutel.

In de volgende configuratie kan het doel knooppunt bijvoorbeeld wachten tot de **xADDomain** -resource op het **eigendc** -knoop punt is voltooid met een maximum aantal van 30 nieuwe pogingen, met een interval van 15 seconden voordat het doel knooppunt kan worden toegevoegd aan het domein.

De **WaitForXXX** -resources proberen standaard één keer en vervolgens mislukt. Hoewel dit niet vereist is, wilt u meestal een **RetryCount** en **RetryIntervalSec**opgeven.

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

Wanneer u de configuratie compileert, worden er twee. MOF-bestanden gegenereerd. Beide '. mof '-bestanden Toep assen op de doel knooppunten met behulp van de cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)

> [!NOTE]
> **WaitForXXX** -bronnen gebruiken Windows Remote Management om de status van andere knoop punten te controleren.
> Zie [beveiligings overwegingen voor externe communicatie van Power shell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)voor meer informatie over de vereisten voor de poort en de beveiliging van WinRM.

## <a name="see-also"></a>Zie ook

- [DSC-configuraties](configurations.md)
- [Resource afhankelijkheden gebruiken](resource-depends-on.md)
- [DSC-resources](../resources/resources.md)
- [De lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)
