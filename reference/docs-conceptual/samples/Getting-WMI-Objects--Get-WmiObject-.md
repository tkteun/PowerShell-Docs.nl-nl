---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: WMI-objecten ophalen ophalen WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058247"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>WMI-objecten ophalen (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>WMI-objecten ophalen (Get-WmiObject)

Windows Management Instrumentation (WMI) is een belangrijke technologie voor Windows Systeembeheer omdat een breed scala aan gegevens op een uniforme wijze worden getoond. Vanwege WMI hoeveel mogelijk, de Windows PowerShell-cmdlet is voor toegang tot WMI-objecten, **Get-WmiObject**, een van de handigste is om echte werk te doen. We gaan bespreken Get-WmiObject gebruiken voor toegang tot WMI-objecten en klik vervolgens op WMI-objecten gebruiken om bepaalde dingen te doen.

### <a name="listing-wmi-classes"></a>WMI-klassen weergeven

Het eerste probleem tegenkomen voor de meeste gebruikers van de WMI-probeert om erachter te komen wat kan worden gedaan met WMI. WMI-klassen beschrijven de resources die kunnen worden beheerd. Er zijn honderden WMI-klassen, waarvan sommige tientallen eigenschappen bevatten.

**Get-WmiObject** lost dit probleem door WMI kunnen worden gedetecteerd. U kunt een lijst van de WMI-klassen beschikbaar op de lokale computer opvragen door te typen:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

U kunt dezelfde gegevens vanaf een externe computer met behulp van de parameter ComputerName ophalen een computernaam of IP-adres op te geven:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

De aanbieding van de klasse die wordt geretourneerd door de externe computers mogelijk afhankelijk van het specifieke besturingssysteem die de computer wordt uitgevoerd en de bepaalde WMI-extensies toegevoegd door de geïnstalleerde toepassingen.

> [!NOTE]
> Wanneer u Get-WmiObject verbinding maken met een externe computer, op de externe computer WMI moet worden uitgevoerd en onder de standaardconfiguratie, moet het account dat u gebruikt in de lokale beheerdersgroep op de externe computer. Het externe systeem hoeft niet te hebben van Windows PowerShell is geïnstalleerd. Hiermee kunt u voor het beheren van besturingssystemen die niet worden uitgevoerd in Windows PowerShell, maar wel WMI beschikbaar.

U kunt ook de computernaam opnemen bij het verbinden met het lokale systeem. U kunt de naam van de lokale computer, het IP-adres (of het loopback-adres 127.0.0.1), of de WMI-stijl '.' als naam van de computer. Als u Windows PowerShell op een computer met de naam Admin01 met IP-adres 192.168.1.90 uitvoert, worden de volgende opdrachten alle geretourneerd met de WMI-klasse aanbieding voor die computer:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject maakt standaard gebruik van de naamruimte root/cimv2. Als u een andere WMI-naamruimte opgeven wilt, gebruikt u de **Namespace** parameter en het bijbehorende naamruimtepad opgeven:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>WMI-klasse Details weergeven

Als u de naam van een WMI-klasse al kent, kunt u deze informatie om direct te ontvangen. Bijvoorbeeld, een van de WMI-klassen die vaak worden gebruikt voor het ophalen van informatie over een computer is **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Hoewel we alle parameters worden weergegeven, kan de opdracht kan worden uitgedrukt in een meer beknopte manier. De **ComputerName** parameter is niet nodig bij het verbinden met het lokale systeem. We laten zien voor het demonstreren van de meest algemene geval en herinneren dat u de parameter. De **Namespace** standaard ingesteld op de root/cimv2, en kunnen ook worden weggelaten. Ten slotte kunt de meeste cmdlets u de naam van de algemene parameters weglaten. Met Get-WmiObject, als er geen naam is opgegeven voor de eerste parameter, Windows PowerShell wordt deze behandeld als de **klasse** parameter. Dit betekent dat de laatste opdracht kan worden uitgegeven door te typen:

```powershell
Get-WmiObject Win32_OperatingSystem
```

De **Win32_OperatingSystem** klasse heeft nog veel meer eigenschappen dan die hier worden weergegeven. U kunt Get-Member gebruiken om te zien van alle eigenschappen. De eigenschappen van een WMI-klasse zijn automatisch beschikbaar, zoals andere eigenschappen van het object:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Niet-standaard-eigenschappen met de indeling Cmdlets weergeven

Als u wilt dat de informatie in de **Win32_OperatingSystem** klasse dat wil zeggen niet standaard weergegeven, kunt u deze weergeven doen met behulp van de **indeling** cmdlets. Bijvoorbeeld, als u wilt om beschikbare memory-gegevens weer te geven, typt u:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Jokertekens werken met namen van eigenschappen in **Format-Table**, zodat het uiteindelijke pijplijnelement kan worden teruggebracht naar `Format-Table -Property Total,Free`

De memory-gegevens is mogelijk beter leesbare indeling als een lijst met door te typen:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
