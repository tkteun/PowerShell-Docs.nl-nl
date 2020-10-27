---
ms.date: 01/17/2019
keywords: DSC, Power shell, configuratie, installatie
title: Een knooppunt opnieuw opstarten
description: Voor veel configuratie-instellingen kan het nodig zijn dat de computer opnieuw wordt opgestart om de configuratie wijziging te volt ooien. In dit artikel wordt uitgelegd hoe u opnieuw opstarten in een configuratie beheert.
ms.openlocfilehash: d2b0f77c34ebcb006821da1f4f8d7c4b046f7a95
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645118"
---
# <a name="reboot-a-node"></a>Een knooppunt opnieuw opstarten

> [!NOTE]
> In dit onderwerp vindt u informatie over het opnieuw opstarten van een knoop punt. Als u de computer opnieuw wilt opstarten, moeten de instellingen voor **ActionAfterReboot** en **RebootNodeIfNeeded** LCM correct worden geconfigureerd. Zie [de lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)of [de lokale Configuration Manager (v4) configureren](../managing-nodes/metaConfig4.md)voor meer informatie over de instellingen van lokale Configuration Manager.

Knoop punten kunnen opnieuw worden opgestart vanuit een resource met behulp van de `$global:DSCMachineStatus` vlag. Als u deze vlag instelt op `1` in de `Set-TargetResource` functie, dwingt de LCM het knoop punt rechtstreeks opnieuw op te starten na de **set** -methode van de huidige resource. Als u deze vlag gebruikt, detecteert de **PendingReboot** -resource in de DSC-resource module van [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) dat een herstart in behandeling is buiten DSC.

Uw [configuraties](configurations.md) kunnen stappen uitvoeren waarvoor het knoop punt opnieuw moet worden opgestart. Dit kan bijvoorbeeld de volgende oorzaken hebben:

- Windows-updates
- Software-installatie
- Hernoemingen van bestanden
- Computer naam wijzigen

De **PendingReboot** -resource controleert specifieke computer locaties om te bepalen of opnieuw opstarten in behandeling is. Als het knoop punt opnieuw moet worden opgestart buiten DSC, wordt met de **PendingReboot** -resource de `$global:DSCMachineStatus` vlag ingesteld voor het `1` afdwingen van een herstart en het oplossen van de voor waarde in behandeling.

> [!NOTE]
> Een DSC-resource kan de LCM de opdracht geven het knoop punt opnieuw op te starten door deze vlag in de functie in te stellen `Set-TargetResource` . Zie [een aangepaste DSC-resource schrijven met MOF](../resources/authoringResourceMOF.md)voor meer informatie.

## <a name="syntax"></a>Syntax

```
PendingReboot [String] #ResourceName
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

| Eigenschap | Beschrijving |
| --- | --- |
| Naam| De vereiste para meter die uniek moet zijn per exemplaar van de resource in een configuratie.|
| SkipComponentBasedServicing | Overs Laan keer opnieuw opstarten geactiveerd door het onderdeel Component-Based onderhoud. |
| SkipWindowsUpdate | Overs Laan keer opnieuw opstarten geactiveerd door Windows Update.|
| SkipPendingFileRename | Overs Laan herstart van bestand in behandeling. |
| SkipCcmClientSDK | Sla opnieuw opstarten dat door de Configuration Manager-client wordt geactiveerd. |
| SkipComputerRename | Overs Laan keer opnieuw opstarten geactiveerd door het wijzigen van de naam van de computer. |
| PSDSCRunAsCredential | Ondersteund in V5. Hiermee wordt de resource uitgevoerd als de opgegeven gebruiker. |
| DependsOn | Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt **uitvoeren, de** naam **ResourceName** is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . Zie [using DependsOn](resource-depends-on.md) voor meer informatie.|

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt micro soft Exchange geïnstalleerd met behulp van de [xExchange](https://github.com/PowerShell/xExchange) -resource. Tijdens de installatie wordt de **PendingReboot** -resource gebruikt om het knoop punt opnieuw op te starten.

> [!NOTE]
> In dit voor beeld is de referentie vereist van een account met rechten voor het toevoegen van een Exchange-server aan het forest. Zie [referenties afhandelen in DSC](../configurations/configDataCredentials.md) voor meer informatie over het gebruik van referenties in DSC

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
    Import-DscResource -Module ComputerManagementDsc

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
        PendingReboot BeforeExchangeInstall
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
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> In dit voor beeld wordt ervan uitgegaan dat u de lokale Configuration Manager zo hebt geconfigureerd dat deze opnieuw wordt opgestart en de configuratie kan worden voortgezet nadat de computer opnieuw is opgestart.

## <a name="where-to-download"></a>Waar downloaden?

U kunt de resources downloaden die in dit onderwerp worden gebruikt op de volgende locaties of met behulp van de Power shell-galerie.

- [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc)
- [xExchange](https://github.com/PowerShell/xExchange)
