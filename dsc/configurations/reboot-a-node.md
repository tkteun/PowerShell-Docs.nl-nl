---
ms.date: 01/17/2019
keywords: DSC, powershell, configuratie en installatie
title: Een knooppunt opnieuw opstarten
ms.openlocfilehash: 106fa1e7b0e3aaf3070ec05548d51140fe9a7725
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470741"
---
# <a name="reboot-a-node"></a>Een knooppunt opnieuw opstarten

> [!NOTE]
> In dit onderwerp wordt besproken hoe u een knooppunt opnieuw opstarten. In de volgorde voor het opnieuw opstarten om succesvol te zijn de **ActionAfterReboot** en **RebootNodeIfNeeded** LCM instellingen moeten correct worden geconfigureerd.
> Zie voor meer informatie over de lokale Configuration Manager-instellingen, [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md), of [configureren de Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).

Knooppunten kunnen opnieuw worden opgestart vanaf binnen een resource, met behulp van de `$global:DSCMachineStatus` vlag. Als deze vlag instelt op `1` in de `Set-TargetResource` functie zorgt ervoor dat de LCM om het knooppunt rechtstreeks na opnieuw opstarten de **ingesteld** methode van de huidige resourcegroep. Met deze markering de **xPendingReboot** resource wordt gedetecteerd of een opnieuw opstarten in behandeling is buiten DSC.

Uw [configuraties](configurations.md) voeren stappen waarvoor het knooppunt opnieuw op te starten. Dit kan bijvoorbeeld dingen omvatten:

- Windows-updates
- Software-installatie
- De naam van bestand wijzigen
- Computer wijzigen

De **xPendingReboot** resource controleert locaties van de specifieke computer om te bepalen of een opnieuw opstarten in behandeling is. Als het knooppunt opnieuw worden opgestart buiten DSC moet, de **xPendingReboot** resource stelt de `$global:DSCMachineStatus` markering `1` forceren van opnieuw opstarten en het oplossen van de voorwaarde in behandeling.

> [!NOTE]
> Een DSC-resource kan de opdracht geven de LCM om het knooppunt opnieuw opstarten met deze markering instellen de `Set-TargetResource` functie. Zie voor meer informatie, [schrijven van een aangepaste DSC-resource met MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Syntaxis

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Eigenschappen

| Eigenschap | Description |
| --- | --- |
| Naam| De vereiste parameter moet uniek zijn per exemplaar van de resource in een configuratie.|
| SkipComponentBasedServicing | Overslaan opnieuw wordt opgestart door het onderdeel Component-Based Servicing geactiveerd. |
| SkipWindowsUpdate | Overslaan opnieuw wordt opgestart geactiveerd door Windows Update.|
| SkipPendingFileRename | Opnieuw opstarten in behandeling zijnde-naam overslaan. |
| SkipCcmClientSDK | Overslaan opnieuw wordt opgestart geactiveerd door de ConfigMgr-client. |
| SkipComputerRename | Overslaan opnieuw wordt opgestart door de naam van de Computer geactiveerd. |
| PSDSCRunAsCredential | Ondersteund in versie 5. De resource als de opgegeven gebruiker uitgevoerd. |
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`. Zie voor meer informatie, [DependsOn gebruiken](resource-depends-on.md)|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld installeert met behulp van Microsoft Exchange de [xExchange](https://github.com/PowerShell/xExchange) resource.
Tijdens de installatie de **xPendingReboot** bron wordt gebruikt om het knooppunt opnieuw opstarten.

> [!NOTE]
> In dit voorbeeld is de referentie van een account met machtigingen voor het toevoegen van een Exchange-server aan het forest vereist. Zie voor meer informatie over het gebruik van referenties in DSC [verwerken van de referenties in DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> In dit voorbeeld wordt ervan uitgegaan dat u de Local Configuration Manager als u wilt toestaan dat opnieuw wordt opgestart en doorgaan met de configuratie na het opnieuw opstarten hebt geconfigureerd.

## <a name="where-to-download"></a>Het downloaden

U kunt de resources die worden gebruikt in dit onderwerp op de volgende locaties of met behulp van de PowerShell gallery downloaden.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
