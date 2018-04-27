---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Ophalen van WMI-objecten ophalen WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 279e656b4affd27450be71015a5d6bd21af9f7ad
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2018
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Ophalen van WMI-objecten (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Ophalen van WMI-objecten (Get-WmiObject)

Windows Management Instrumentation (WMI) is een belangrijke technologie voor Windows Systeembeheer omdat een breed scala aan gegevens op uniforme wijze worden getoond. Vanwege hoeveel WMI mogelijk uit de Windows PowerShell-cmdlet voor toegang tot WMI-objecten maakt **Get-WmiObject**, is een van de meest geschikt voor echte werk. We gaan bespreken Get-WmiObject gebruiken voor toegang tot WMI-objecten en vervolgens op het gebruik van WMI-objecten om specifieke dingen te doen.

### <a name="listing-wmi-classes"></a>Aanbieding WMI-klassen

Het eerste probleem optreden van de meeste gebruikers van de WMI-probeert om erachter te komen wat u met WMI doen kunt. WMI-klassen beschrijven de bronnen die kunnen worden beheerd. Er zijn honderden WMI-klassen, waarvan sommige tientallen eigenschappen bevatten.

**Get-WmiObject** lost dit probleem doordat WMI kunnen worden gedetecteerd. U kunt een lijst met de WMI-klassen beschikbaar op de lokale computer krijgen door te typen:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

U kunt dezelfde gegevens vanaf een externe computer met behulp van de parameter ComputerName ophalen opgeven van een computernaam of IP-adres:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

De aanbieding van de klasse die wordt geretourneerd door de externe computers kan vanwege het specifieke besturingssysteem dat wordt uitgevoerd op de computer en de bepaalde WMI-uitbreidingen toegevoegd door de geïnstalleerde toepassingen verschillen.

> [!NOTE]
> Wanneer u de Get-WmiObject verbinding maken met een externe computer, op de externe computer WMI moet worden uitgevoerd en onder de standaardconfiguratie moet het account dat u gebruikt in de lokale beheerdersgroep op de externe computer. Het externe systeem hoeft niet te hebben van Windows PowerShell is geïnstalleerd. Hiermee kunt u voor het beheren van besturingssystemen die niet worden uitgevoerd in Windows PowerShell, maar hoeven WMI beschikbaar.

U kunt zelfs de ComputerName opnemen wanneer u verbinding met het lokale systeem. U kunt de naam van de lokale computer, het IP-adres (of de loopback-adres 127.0.0.1), of de WMI-stijl '.' als de naam van de computer. Als u Windows PowerShell op een computer met de naam Admin01 met IP-adres 192.168.1.90 uitvoert, wordt de volgende opdrachten alle geretourneerd met de WMI-klasse aanbieding voor die computer:

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

### <a name="displaying-wmi-class-details"></a>Met de WMI-klasse Details

Als u de naam van een WMI-klasse al weet, kunt u deze informatie onmiddellijk ophalen. Bijvoorbeeld, een van de WMI-klassen die meestal wordt gebruikt voor het ophalen van informatie over een computer is **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Hoewel we alle parameters worden weergegeven, kan de opdracht kan worden uitgedrukt in een meer beknopte manier. De **ComputerName** parameter is niet nodig bij het verbinden met het lokale systeem. We blijkt dat het meest algemene geval demonstreren en herinneren van de parameter. De **Namespace** root/cimv2 standaard en kan ook worden weggelaten. Ten slotte kunt de meeste cmdlets u de naam van de algemene parameters weglaten. Met Get-WmiObject, als er geen naam is opgegeven voor de eerste parameter, Windows PowerShell wordt deze behandeld als de **klasse** parameter. Dit betekent dat de laatste opdracht kan worden uitgegeven door te typen:

```powershell
Get-WmiObject Win32_OperatingSystem
```

De **Win32_OperatingSystem** klasse heeft nog veel meer eigenschappen dan de hier weergegeven. De eigenschappen kunt u Get-lid. De eigenschappen van een WMI-klasse zijn automatisch beschikbaar, zoals andere eigenschappen van het object:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Eigenschappen van de niet-standaard met indeling Cmdlets weer te geven

Als u wilt dat de gegevens in de **Win32_OperatingSystem** klasse is niet standaard weergegeven, kunt u deze weergeven doen met behulp van de **indeling** cmdlets. Bijvoorbeeld, als u gegevens beschikbaar geheugen weergeven wilt, typt u:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Jokertekens werken met namen van eigenschappen in **Format-Table**, zodat de laatste pipeline-element kan worden teruggebracht naar `Format-Table -Property Total,Free`

De geheugengegevens is mogelijk beter leesbare indeling als een lijst door te typen:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
