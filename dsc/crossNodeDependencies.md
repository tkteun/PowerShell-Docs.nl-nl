---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Cross-knooppunt afhankelijkheden opgeven
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a>Cross-knooppunt afhankelijkheden opgeven

> Van toepassing op: Windows PowerShell 5.0

DSC biedt speciale bronnen **WaitForAll**, **WaitForAny**, en **WaitForSome** die kunnen worden gebruikt in configuraties afhankelijkheden op configuraties op andere opgeven knooppunten. Het gedrag van deze resources is als volgt:

* **WaitForAll**: is geslaagd als de opgegeven bron in de gewenste status op alle doelknooppunten gedefinieerd is in de **NodeName** eigenschap.
* **WaitForAny**: is geslaagd als de opgegeven bron in de gewenste status op ten minste één van de doelknooppunten gedefinieerd is in de **NodeName** eigenschap.
* **WaitForSome**: Hiermee geeft u een **NodeCount** eigenschap naast een **NodeName** eigenschap. De resource is geslaagd als de bron in de gewenste status van een minimum aantal knooppunten is (opgegeven door **NodeCount**) gedefinieerd door de **NodeName** eigenschap. 

## <a name="using-waitforxxxx-resources"></a>WaitForXXXX-bronnen

Gebruik de **WaitForXXXX** resources, hebt u een resource-blok van dat resourcetype waarmee de DSC-resource en de knooppunten te wachten. Vervolgens gebruikt u de **DependsOn** eigenschap in een andere bron gegevensblokken die zich in de configuratie moet worden gewacht op de voorwaarden van de **WaitForXXXX** knooppunt om te slagen.

Bijvoorbeeld, in de volgende configuratie het doelknooppunt wacht tot de **xADDomain** resource moet worden voltooid op de **Eigendc** knooppunt met 30 maximumaantal nieuwe pogingen, met intervallen van 15 seconden, voordat de doelknooppunt kunt deelnemen aan het domein.

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

>**Opmerking:** standaard de WaitForXXX resources één keer te proberen en voert vervolgens failover uit. Hoewel dit niet vereist is, wilt u waarschijnlijk een interval voor opnieuw proberen en de telling opgeven.

## <a name="see-also"></a>Zie ook
* [DSC-configuraties](configurations.md)
* [DSC-Resources](resources.md)
* [De lokale Configuration Manager configureren](metaConfig.md)

