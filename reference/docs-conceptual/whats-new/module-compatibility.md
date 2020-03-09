---
title: Compatibiliteit met Power shell 7-module
ms.date: 02/03/2020
ms.openlocfilehash: 1f7a2f4fa04e07b8f56635d0a39e580924ae0134
ms.sourcegitcommit: d34841a44742af1123da007fefbdc24a2f1762dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/07/2020
ms.locfileid: "78926197"
---
# <a name="powershell-7-module-compatibility"></a>Compatibiliteit met Power shell 7-module

Dit artikel bevat een lijst met Power shell-modules die door micro soft zijn gepubliceerd en die beheer en ondersteuning bieden voor diverse micro soft-producten en-services. Deze modules zijn bijgewerkt voor gebruik in combi natie met Power shell 7 of getest op compatibiliteit met Power shell 7.

Deze lijst wordt bijgewerkt met nieuwe informatie, omdat er meer modules worden geïdentificeerd en getest. Als u informatie hebt om te delen of problemen met specifieke modules op te lossen, kunt u een probleem melden in de [WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility) -opslag plaats.

## <a name="windows-management-modules"></a>Windows-beheer modules

De Windows-beheer modules worden op verschillende manieren geïnstalleerd, afhankelijk van het type Windows en de wijze waarop de module is verpakt. Deze modules moeten worden geïnstalleerd vanuit een Power shell-sessie met verhoogde bevoegdheid met de optie **als administrator uitvoeren** .

Gebruik op Windows Server de functie naam met de [install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) om de module te installeren. Bijvoorbeeld:

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

In Windows 10 moet u een van deze cmdlets gebruiken, afhankelijk van het pakket type:
- [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)
- [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

Voor modules die worden geïnstalleerd als Windows-onderdelen:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName FooFeatureName
```

Voor modules die als Windows-mogelijkheden worden geïnstalleerd, moet u `~~~~0.0.1.0` toevoegen aan het einde van de pakket naam. Bijvoorbeeld:

```powershell
Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
```

### <a name="activedirectory"></a>ActiveDirectory

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met RSAT-AD-Power shell
- Windows 10-versie: 1809 + met RSAT. ActiveDirectory. DS-LDS. tools

### <a name="adfs"></a>ADFS

Status: niet getest met compatibiliteit slaag

### <a name="appbackgroundtask"></a>AppBackgroundTask

Status: systeem eigen compatibel

Compatibel met:

- Windows 10-versie: 1903 +

### <a name="applocker"></a>AppLocker

Status: niet getest met compatibiliteit slaag

### <a name="appvclient"></a>AppvClient

Status: niet getest met compatibiliteit slaag

### <a name="appx"></a>Appx

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="assignedaccess"></a>AssignedAccess

Status: systeem eigen compatibel

Compatibel met:

- Windows 10-versie: 1809 +

### <a name="bestpractices"></a>BestPractices

Status: niet getest met compatibiliteit slaag

### <a name="bitlocker"></a>BitLocker

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met BitLocker
- Windows 10-versie: 1809 +

### <a name="bitstransfer"></a>BitsTransfer

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 20H1
- Windows 10-versie: 20H1

### <a name="booteventcollector"></a>BootEventCollector

Status: niet getest met compatibiliteit slaag

### <a name="branchcache"></a>BranchCache

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="cimcmdlets"></a>CimCmdlets

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="clusterawareupdating"></a>ClusterAwareUpdating

Status: niet getest met compatibiliteit slaag

### <a name="configci"></a>ConfigCI

Status: niet getest met compatibiliteit slaag

### <a name="defender"></a>Beschermd

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="deliveryoptimization"></a>DeliveryOptimization

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 +
- Windows 10-versie: 1903 +

### <a name="dfsn"></a>DFSN

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met FS-DFS-naam ruimte
- Windows 10-versie: 1809 + met RSAT. FailoverCluster. Management. tools

### <a name="dfsr"></a>DFSR

Status: niet getest met compatibiliteit slaag

### <a name="dhcpserver"></a>DHCP

Status: niet getest met compatibiliteit slaag

### <a name="directaccessclientcomponents"></a>DirectAccessClientComponents

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="dism"></a>DISM

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 +
- Windows 10-versie: 1903 +

### <a name="dnsclient"></a>DnsClient

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="dnsserver"></a>DnsServer

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met DNS of RSAT-DNS-server
- Windows 10-versie: 1809 + met RSAT. DNS. tools

### <a name="eventtracingmanagement"></a>EventTracingManagement

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="failoverclusters"></a>FailoverClusters

Status: niet getest met compatibiliteit slaag

### <a name="failoverclusterset"></a>FailoverClusterSet

Status: niet getest met compatibiliteit slaag

### <a name="fileserverresourcemanager"></a>FileServerResourceManager

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met FS-Resource-Manager

### <a name="grouppolicy"></a>Architectuur

Status: niet getest met compatibiliteit slaag

### <a name="hgsclient"></a>HgsClient

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 + met Hyper-V of RSAT-afgeschermde-VM-Hulpprogram Ma's
- Windows 10-versie: 1903 + met RSAT. afgeschermde. VM. tools

### <a name="hgsdiagnostics"></a>HgsDiagnostics

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met Hyper-V of RSAT-afgeschermde-VM-Hulpprogram Ma's
- Windows 10-versie: 1809 + met RSAT. afgeschermde. VM. tools

### <a name="hyper-v"></a>Hyper-V

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met Hyper-V-Power shell
- Windows 10-versie: 1809 + met micro soft-Hyper-V-Management-Power shell

### <a name="iisadministration"></a>IISAdministration

Status: niet getest met compatibiliteit slaag

### <a name="international"></a>Nederland

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 +
- Windows 10-versie: 1903 +

### <a name="ipamserver"></a>IpamServer

Status: niet getest met compatibiliteit slaag

### <a name="iscsi"></a>iSCSI

Status: niet getest met compatibiliteit slaag

### <a name="iscsitarget"></a>IscsiTarget

Status: niet getest met compatibiliteit slaag

### <a name="ise"></a>ISE

Status: niet getest met compatibiliteit slaag

### <a name="kds"></a>KDS

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 20H1
- Windows 10-versie: 20H1

### <a name="microsoftpowershellarchive"></a>Micro soft. Power shell. Archive

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="microsoftpowershelllocalaccounts"></a>Micro soft. Power shell. LocalAccounts

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="microsoftpowershellodatautils"></a>Micro soft. Power shell. ODataUtils

Status: niet getest met compatibiliteit slaag

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="microsoftwsmanmanagement"></a>Microsoft.WSMan.Management

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="mmagent"></a>MMAgent

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="mpio"></a>MPIO

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met meerdere paden-IO

### <a name="msdtc"></a>MsDtc

Status: niet getest met compatibiliteit slaag

### <a name="netadapter"></a>NetAdapter

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="netconnection"></a>NetConnection

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="neteventpacketcapture"></a>NetEventPacketCapture

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="netlbfo"></a>NetLbfo

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="netlldpagent"></a>NetLldpAgent

Status: niet getest met compatibiliteit slaag

### <a name="netnat"></a>NetNat

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="netqos"></a>NetQos

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="netsecurity"></a>Netbeveiliging

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="netswitchteam"></a>NetSwitchTeam

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="nettcpip"></a>NetTCPIP

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="netwnv"></a>NetWNV

Status: niet getest met compatibiliteit slaag

### <a name="networkconnectivitystatus"></a>NetworkConnectivityStatus

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="networkcontroller"></a>Network controller

Status: niet getest met compatibiliteit slaag

### <a name="networkcontrollerdiagnostics"></a>NetworkControllerDiagnostics

Status: niet getest met compatibiliteit slaag

### <a name="networkloadbalancingclusters"></a>NetworkLoadBalancingClusters

Status: niet getest met compatibiliteit slaag

### <a name="networkswitchmanager"></a>NetworkSwitchManager

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="networktransition"></a>NetworkTransition

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="nfs"></a>NFS

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 + met RSAT. Server Manager. tools

### <a name="packagemanagement"></a>Package Management

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="pcsvdevice"></a>PcsvDevice

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="persistentmemory"></a>PersistentMemory

Status: niet getest met compatibiliteit slaag

### <a name="pki"></a>PKI

Status: niet getest met compatibiliteit slaag

### <a name="pnpdevice"></a>PnpDevice

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="powershellget"></a>PowerShellGet

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="printmanagement"></a>PrintManagement

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 + met Afdruk Services
- Windows 10-versie: 1903 +

### <a name="processmitigations"></a>ProcessMitigations

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 +
- Windows 10-versie: 1903 +

### <a name="provisioning"></a>Inrichten

Status: niet getest met compatibiliteit slaag

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

Status: gedeeltelijk

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="psdiagnostics"></a>PSDiagnostics

Status: systeem eigen compatibel

Compatibel met:

- Ingebouwd in Power shell 7

### <a name="psscheduledjob"></a>PSScheduledJob

Status: werkt niet met compatibiliteit slaag

Compatibel met:

- Ingebouwd in Power shell 5,1

### <a name="psworkflow"></a>PSWorkflow

Status: niet getest met compatibiliteit slaag

### <a name="psworkflowutility"></a>PSWorkflowUtility

Status: niet getest met compatibiliteit slaag

### <a name="remoteaccess"></a>Remote

Status: niet getest met compatibiliteit slaag

### <a name="remotedesktop"></a>RemoteDesktop

Status: niet getest met compatibiliteit slaag

### <a name="scheduledtasks"></a>ScheduledTasks

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="secureboot"></a>SecureBoot

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="servercore"></a>ServerCore

Status: niet getest met compatibiliteit slaag

### <a name="servermanager"></a>Manager

Status: niet getest met compatibiliteit slaag

### <a name="servermanagertasks"></a>ServerManagerTasks

Status: niet getest met compatibiliteit slaag

### <a name="shieldedvmdatafile"></a>ShieldedVMDataFile

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 + met RSAT-afgeschermde-VM-Hulpprogram Ma's
- Windows 10-versie: 1903 + met RSAT. afgeschermde. VM. tools

### <a name="shieldedvmprovisioning"></a>ShieldedVMProvisioning

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met HostGuardian
- Windows 10-versie: 1809 + met HostGuardian

### <a name="shieldedvmtemplate"></a>ShieldedVMTemplate

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met RSAT-afgeschermde-VM-Hulpprogram Ma's
- Windows 10-versie: 1809 + met RSAT. afgeschermde. VM. tools

### <a name="smbshare"></a>SmbShare

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="smbwitness"></a>SmbWitness

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="smisconfig"></a>SMISConfig

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 + met WindowsStorageManagementService

### <a name="sms"></a>Sms

Status: niet getest met compatibiliteit slaag

### <a name="softwareinventorylogging"></a>SoftwareInventoryLogging

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +

### <a name="startlayout"></a>StartLayout

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met bureaublad ervaring
- Windows 10-versie: 1809 +

### <a name="storage"></a>Opslag

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="storagebuscache"></a>StorageBusCache

Status: niet getest met compatibiliteit slaag

### <a name="storagemigrationservice"></a>StorageMigrationService

Status: niet getest met compatibiliteit slaag

### <a name="storageqos"></a>StorageQOS

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met RSAT-clustering-Power shell
- Windows 10-versie: 1809 + met RSAT. FailoverCluster. Management. tools

### <a name="storagereplica"></a>Storage replica

Status: niet getest met compatibiliteit slaag

### <a name="syncshare"></a>SyncShare

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met FS-SyncShareService

### <a name="systeminsights"></a>SystemInsights

Status: niet getest met compatibiliteit slaag

### <a name="tls"></a>TLS

Status: niet getest met compatibiliteit slaag

### <a name="troubleshootingpack"></a>TroubleshootingPack

Status: systeem eigen compatibel

Compatibel met:

- Windows 10-versie: 1903 +

### <a name="trustedplatformmodule"></a>TrustedPlatformModule

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="uev"></a>UEV

Status: systeem eigen compatibel

Compatibel met:

- Server versie:? Toekomstige versie van server met bureaublad ervaring?
- Windows 10-versie: 1903 +

### <a name="updateservices"></a>Installeer WindowsFeature

Status: werkt niet met compatibiliteit slaag

### <a name="vpnclient"></a>VpnClient

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="wdac"></a>Wdac

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="webadministration"></a>Webbeheer

Status: niet getest met compatibiliteit slaag

### <a name="whea"></a>WHEA

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1903 +
- Windows 10-versie: 1903 +

### <a name="windowsdeveloperlicense"></a>WindowsDeveloperLicense

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 + met bureaublad ervaring
- Windows 10-versie: 1809 +

### <a name="windowserrorreporting"></a>WindowsErrorReporting

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="windowssearch"></a>WindowsSearch

Status: systeem eigen compatibel

Compatibel met:

- Windows 10-versie: 1903 +

### <a name="windowsserverbackup"></a>WindowsServerBackup

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 19H2 met Windows-Server-Backup

### <a name="windowsupdate"></a>WindowsUpdate

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +

### <a name="windowsupdateprovider"></a>WindowsUpdateProvider

Status: systeem eigen compatibel

Compatibel met:

- Server versie: 1809 +
- Windows 10-versie: 1809 +
