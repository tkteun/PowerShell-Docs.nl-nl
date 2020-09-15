---
title: Compatibiliteit met Power shell 7-module
ms.date: 02/03/2020
ms.openlocfilehash: d618f9e55f5997bfd724a4e58bb94c348bd681ce
ms.sourcegitcommit: 56463fb628a7d83dec4364e89417d83316c3e53b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2020
ms.locfileid: "84722810"
---
# <a name="powershell-7-module-compatibility"></a>Compatibiliteit met Power shell 7-module

Dit artikel bevat een lijst met Power shell-modules die zijn gepubliceerd door micro soft. Deze modules bieden beheer en ondersteuning voor diverse micro soft-producten en-services. Deze modules zijn bijgewerkt voor gebruik met Power shell 7 of getest op compatibiliteit met Power shell 7. Deze lijst wordt bijgewerkt met nieuwe informatie, omdat er meer modules worden geïdentificeerd en getest.

Als u informatie hebt om te delen of problemen met specifieke modules op te lossen, kunt u een probleem in de [WindowsCompatibility-opslag plaats](https://github.com/PowerShell/WindowsCompatibility)oplossen.

## <a name="windows-management-modules"></a>Windows-beheer modules

De Windows-beheer module wordt op verschillende manieren geïnstalleerd, afhankelijk van de versie van Windows en de wijze waarop de module voor die editie is verpakt.

Gebruik op Windows Server de functie naam met de cmdlet [install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) als beheerder. Bijvoorbeeld:

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

In Windows 10 worden de Windows-beheer modules beschikbaar gesteld als **optionele Windows-functies** of **Windows-mogelijkheden**. De volgende opdrachten moeten worden uitgevoerd vanuit een verhoogde sessie met de **uitvoeren als-beheerder**.

- Voor optionele Windows-functies

  Voer de volgende opdracht uit om een lijst met optionele functies weer te geven:

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  De functie installeren:

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  Zie voor meer informatie:

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- Voor Windows-mogelijkheden

  Voer de volgende opdracht uit om een lijst met Windows-mogelijkheden te verkrijgen:

  ```powershell
  Get-WindowsCapability -online
  ```

  U ziet dat de naam van het capaciteits pakket eindigt op `~~~~0.0.1.0` . U moet de volledige naam gebruiken om de mogelijkheid te installeren:

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  Zie voor meer informatie:

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>Module lijst

| Module naam                        | Status                               | Ondersteund besturings systeem                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| Active Directory                    | Systeem eigen compatibel                  | Windows Server 1809 + met RSAT-AD-Power shell<br>Windows 10 1809 + met RSAT. ActiveDirectory. DS-LDS. tools |
| ADDSDeployment                     | Werkt met compatibiliteit slaag       |  Windows Server 2019 1809 +         |
| ADFS                               | Niet getest met compatibiliteit slaag    |                                    |
| AppBackgroundTask                  | Systeem eigen compatibel                  | Windows 10 1903 +                   |
| AppLocker                          | Niet getest met compatibiliteit slaag    |                                    |
| AppvClient                         | Niet getest met compatibiliteit slaag    |                                    |
| Appx                               | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 + |
| AssignedAccess                     | Systeem eigen compatibel                  | Windows 10 1809 +                   |
| BestPractices                      | Niet ondersteund door compatibiliteit slaag |                                    |
| BitLocker                          | Systeem eigen compatibel                  | Windows Server 1809 + met BitLocker<br>Windows 10 1809 + |
| BitsTransfer                       | Systeem eigen compatibel                  | Windows Server-20H1<br>Windows 10-20H1 |
| BootEventCollector                 | Niet getest met compatibiliteit slaag    |                                        |
| BranchCache                        | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 + |
| CimCmdlets                         | Systeem eigen compatibel                  | Ingebouwd in Power shell 7 |
| ClusterAwareUpdating               | Niet getest met compatibiliteit slaag    |                         |
| ConfigCI                           | Niet getest met compatibiliteit slaag    |                         |
| Defender                           | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +  |
| DeliveryOptimization               | Systeem eigen compatibel                  | Windows Server 1903 +<br>Windows 10 1903 +  |
| DFSN                               | Systeem eigen compatibel                  | Windows Server 1809 + met FS-DFS-naam ruimte<br>Windows 10 1809 + met RSAT. FailoverCluster. Management. tools |
| DFSR                               | Niet getest met compatibiliteit slaag    |                                   |
| DHCP                         | Niet getest met compatibiliteit slaag    |                                   |
| DirectAccessClientComponents       | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +  |
| DISM                               | Systeem eigen compatibel                  | Windows Server 1903 +<br>Windows 10 1903 +  |
| DnsClient                          | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +  |
| DnsServer                          | Systeem eigen compatibel                  | Windows Server 1809 + met DNS of RSAT-DNS-server<br>Windows 10 1809 + met RSAT. DNS. tools |
| EventTracingManagement             | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +  |
| FailoverClusters                   | Niet getest met compatibiliteit slaag    |                                  |
| FailoverClusterSet                 | Niet getest met compatibiliteit slaag    |                                  |
| FileServerResourceManager          | Systeem eigen compatibel                  | Windows Server 1809 + met FS-Resource-Manager |
| Architectuur                        | Niet getest met compatibiliteit slaag    |                                               |
| HgsClient                          | Systeem eigen compatibel                  | Windows Server 1903 + met Hyper-V of RSAT-afgeschermde-VM-Hulpprogram Ma's<br>Windows 10 1903 + met RSAT. afgeschermde. VM. tools |
| HgsDiagnostics                     | Systeem eigen compatibel                  | Windows Server 1809 + met Hyper-V of RSAT-afgeschermde-VM-Hulpprogram Ma's<br>Windows 10 1809 + met RSAT. afgeschermde. VM. tools |
| Hyper-V                            | Systeem eigen compatibel                  | Windows Server 1809 + met Hyper-V-Power shell<br>Windows 10 1809 + met micro soft-Hyper-V-Management-Power shell |
| IISAdministration                  | Niet getest met compatibiliteit slaag    |                                               |
| Nederland                      | Systeem eigen compatibel                  | Windows Server 1903 +<br>Windows 10 1903 +      |
| IpamServer                         | Niet getest met compatibiliteit slaag    |                                               |
| iSCSI                              | Niet getest met compatibiliteit slaag    |                                               |
| IscsiTarget                        | Niet getest met compatibiliteit slaag    |                                               |
| ISE                                | Niet getest met compatibiliteit slaag    |                                               |
| KDS                                | Systeem eigen compatibel                  | Windows Server-20H1<br>Windows 10-20H1        |
| Micro soft. Power shell. Archive       | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| Micro soft. Power shell. Diagnostics   | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| Micro soft. Power shell. host          | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| Micro soft. Power shell. LocalAccounts | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| Micro soft. Power shell. Management    | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| Micro soft. Power shell. ODataUtils    | Niet getest met compatibiliteit slaag    |                                               |
| Micro soft. Power shell. Security      | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| Microsoft.PowerShell.Utility       | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| Micro soft. WSMan. Management         | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| MMAgent                            | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| MPIO                               | Systeem eigen compatibel                  | Windows Server 1809 + met meerdere paden-IO        |
| MsDtc                              | Niet getest met compatibiliteit slaag    |                                               |
| NetAdapter                         | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetConnection                      | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetEventPacketCapture              | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetLbfo                            | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetLldpAgent                       | Niet getest met compatibiliteit slaag    |                                               |
| NetNat                             | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetQos                             | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| Netbeveiliging                        | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetSwitchTeam                      | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetTCPIP                           | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetWNV                             | Niet getest met compatibiliteit slaag    |                                               |
| NetworkConnectivityStatus          | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| Network controller                  | Niet getest met compatibiliteit slaag    |                                               |
| NetworkControllerDiagnostics       | Niet getest met compatibiliteit slaag    |                                               |
| NetworkLoadBalancingClusters       | Niet getest met compatibiliteit slaag    |                                               |
| NetworkSwitchManager               | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NetworkTransition                  | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| NFS                                | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 + met RSAT. Server Manager. tools |
| PackageManagement                  | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| PcsvDevice                         | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| PersistentMemory                   | Niet getest met compatibiliteit slaag    |                                               |
| PKI                                | Niet getest met compatibiliteit slaag    |                                               |
| PnpDevice                          | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| PowerShellGet                      | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| PrintManagement                    | Systeem eigen compatibel                  | Windows Server 1903 + met Afdruk Services<br>Windows 10 1903 +  |
| ProcessMitigations                 | Systeem eigen compatibel                  | Windows Server 1903 +<br>Windows 10 1903 +      |
| Inrichten                       | Niet getest met compatibiliteit slaag    |                                               |
| PSDesiredStateConfiguration        | Gedeeltelijk                            | Ingebouwd in Power shell 7                       |
| PSDiagnostics                      | Systeem eigen compatibel                  | Ingebouwd in Power shell 7                       |
| PSScheduledJob                     | Niet ondersteund door compatibiliteit slaag | Ingebouwd in Power shell 5,1                     |
| PSWorkflow                         | Niet getest met compatibiliteit slaag    |                                               |
| PSWorkflowUtility                  | Niet getest met compatibiliteit slaag    |                                               |
| Remote                       | Niet getest met compatibiliteit slaag    |                                               |
| RemoteDesktop                      | Niet getest met compatibiliteit slaag    |                                               |
| ScheduledTasks                     | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| SecureBoot                         | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| ServerCore                         | Niet getest met compatibiliteit slaag    |                                               |
| Manager                      | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 + met RSAT. Server Manager. tools<br>_Zie de opmerkingen hieronder_ |
| ServerManagerTasks                 | Niet getest met compatibiliteit slaag    |                                               |
| ShieldedVMDataFile                 | Systeem eigen compatibel                  | Windows Server 1903 + met RSAT-afgeschermde-VM-Hulpprogram Ma's<br>Windows 10 1903 + met RSAT. afgeschermde. VM. tools |
| ShieldedVMProvisioning             | Systeem eigen compatibel                  | Windows Server 1809 + met HostGuardian<br>Windows 10 1809 + met HostGuardian  |
| ShieldedVMTemplate                 | Systeem eigen compatibel                  | Windows Server 1809 + met RSAT-afgeschermde-VM-Hulpprogram Ma's<br>Windows 10 1809 + met RSAT. afgeschermde. VM. tools |
| SmbShare                           | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| SmbWitness                         | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| SMISConfig                         | Systeem eigen compatibel                  | Windows Server 1903 + met WindowsStorageManagementService |
| Sms                                | Niet getest met compatibiliteit slaag    |                                               |
| SoftwareInventoryLogging           | Systeem eigen compatibel                  | Windows Server 1809 +                          |
| StartLayout                        | Systeem eigen compatibel                  | Windows Server 1809 + met bureaublad ervaring<br>Windows 10 1809 + |
| Storage                            | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| StorageBusCache                    | Niet getest met compatibiliteit slaag    |                                               |
| StorageMigrationService            | Niet getest met compatibiliteit slaag    |                                               |
| StorageQOS                         | Systeem eigen compatibel                  | Windows Server 1809 + met RSAT-clustering-Power shell<br>Windows 10 1809 + met RSAT. FailoverCluster. Management. tools |
| Storage replica                     | Niet getest met compatibiliteit slaag    |                                               |
| SyncShare                          | Systeem eigen compatibel                  | Windows Server 1809 + met FS-SyncShareService |
| SystemInsights                     | Niet getest met compatibiliteit slaag    |                                               |
| TLS                                | Niet getest met compatibiliteit slaag    |                                               |
| TroubleshootingPack                | Systeem eigen compatibel                  | Windows 10 1903 +                              |
| TrustedPlatformModule              | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| UEV                                | Systeem eigen compatibel                  | Windows Server? Toekomstige versie van server met bureaublad ervaring?<br>Windows 10 1903 + |
| Installeer WindowsFeature                     | Niet ondersteund door compatibiliteit slaag |                                               |
| VpnClient                          | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| Wdac                               | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| Webbeheer                  | Niet getest met compatibiliteit slaag    |                                               |
| WHEA                               | Systeem eigen compatibel                  | Windows Server 1903 +<br>Windows 10 1903 +      |
| WindowsDeveloperLicense            | Systeem eigen compatibel                  | Windows Server 1809 + met bureaublad ervaring<br>Windows 10 1809 + |
| WindowsErrorReporting              | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +      |
| WindowsSearch                      | Systeem eigen compatibel                  | Windows 10 1903 +                              |
| WindowsServerBackup                | Systeem eigen compatibel                  | Windows Server-19H2 met Windows-Server-Backup |
| WindowsUpdate                      | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +       |
| WindowsUpdateProvider              | Systeem eigen compatibel                  | Windows Server 1809 +<br>Windows 10 1809 +       |

## <a name="notes"></a>Opmerkingen

### <a name="servermanager-module"></a>Server Manager-module

De module heeft een aantal kleine compatibiliteits problemen met de opgemaakte uitvoer in Power shell 7. De `Get-WindowsFeature` cmdlet retourneert bijvoorbeeld het juiste object met alle eigenschappen, maar de standaard notatie voor weer gave is dat sommige eigenschappen leeg zijn. De werkelijke waarden zijn beschikbaar in de object eigenschappen met `Select-Object` of door rechtstreekse leden toegang.

