---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Ophalen van WMI-objecten WmiObject
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030212"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>WMI-objecten ophalen (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>WMI-objecten ophalen (Get-WmiObject)

Windows Management Instrumentation (WMI) is een kern technologie voor Windows-systeem beheer, omdat een breed scala aan gegevens op een uniforme manier wordt weer gegeven. Als gevolg van de mate waarin WMI mogelijk is, is de Windows Power shell-cmdlet voor toegang tot WMI-objecten, **Get-WmiObject**, een van de handigste voor het uitvoeren van echte werk. We bespreken hoe u Get-WmiObject kunt gebruiken voor toegang tot WMI-objecten en hoe u WMI-objecten kunt gebruiken om specifieke dingen uit te voeren.

### <a name="listing-wmi-classes"></a>WMI-klassen weer geven

Het eerste probleem dat de meeste WMI-gebruikers ondervindt, probeert te ontdekken wat er met WMI kan worden gedaan. WMI-klassen beschrijven de resources die kunnen worden beheerd. Er zijn honderden WMI-klassen waarvan sommige van de eigenschappen tien tallen bevatten.

**Get-WmiObject** lost dit probleem op door WMI detecteerbaar te maken. U kunt een lijst weer geven van de WMI-klassen die beschikbaar zijn op de lokale computer door het volgende te typen:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

U kunt dezelfde gegevens ophalen van een externe computer met behulp van de para meter ComputerName, waarbij u een computer naam of IP-adres opgeeft:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

De lijst met klassen die door externe computers wordt geretourneerd, kan variëren als gevolg van het specifieke besturings systeem dat op de computer wordt uitgevoerd en de specifieke WMI-uitbrei dingen die zijn toegevoegd door geïnstalleerde toepassingen.

> [!NOTE]
> Wanneer u Get-WmiObject gebruikt om verbinding te maken met een externe computer, moet op de externe computer WMI worden uitgevoerd en moet het account dat u gebruikt, zich in de lokale groep Administrators op de externe computer bevinden, onder de standaard configuratie. Windows Power shell hoeft niet te zijn geïnstalleerd op het externe systeem. Hierdoor kunt u besturings systemen beheren waarop geen Windows Power shell wordt uitgevoerd, maar die WMI wel beschikbaar heeft.

U kunt zelfs de computer naam toevoegen wanneer u verbinding maakt met het lokale systeem. U kunt de naam van de lokale computer, het bijbehorende IP-adres (of het loop back-adres 127.0.0.1) of de WMI-stijl '. ' gebruiken als computer naam. Als u Windows Power shell uitvoert op een computer met de naam Admin01 met IP-adres 192.168.1.90, worden met de volgende opdrachten alle vermeldingen van de WMI-klasse voor die computer geretourneerd:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject maakt standaard gebruik van de naam ruimte root/cimv2. Als u een andere WMI-naam ruimte wilt opgeven, gebruikt u de para meter **naam ruimte** en geeft u het bijbehorende pad naar de naam ruimte op:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Details van WMI-klasse weer geven

Als u de naam van een WMI-klasse al kent, kunt u deze gebruiken om informatie direct op te halen. Zo is een van de WMI-klassen die meestal worden gebruikt voor het ophalen van informatie over een computer is **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Hoewel alle para meters worden weer gegeven, kan de opdracht op een meer beknopte manier worden aangegeven. De para meter **ComputerName** is niet nodig bij het maken van verbinding met het lokale systeem. We laten u zien hoe u het meest algemene geval kunt demonstreren en u kunt u herinneren over de para meter. De **naam ruimte** wordt standaard ingesteld op root-cimv2 en kan ook worden wegge laten. Ten slotte kunt u met de meeste cmdlets de naam van algemene para meters weglaten. Als er bij Get-WmiObject geen naam is opgegeven voor de eerste para meter, wordt deze door Windows Power shell beschouwd als de **klasse** para meter. Dit betekent dat de laatste opdracht kan zijn uitgegeven door het volgende te typen:

```powershell
Get-WmiObject Win32_OperatingSystem
```

De klasse **Win32_OperatingSystem** heeft veel meer eigenschappen dan hier wordt weer gegeven. U kunt Get-member gebruiken om alle eigenschappen te bekijken. De eigenschappen van een WMI-klasse zijn automatisch beschikbaar, net als andere object eigenschappen:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Niet-standaard eigenschappen weer geven met Format-cmdlets

Als u informatie wilt weer geven in de klasse **Win32_OperatingSystem** die niet standaard wordt weer gegeven, kunt u de gegevens met behulp van de **Format** -cmdlets bekijken. Als u bijvoorbeeld beschik bare geheugen gegevens wilt weer geven, typt u:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Joker tekens werken met eigenschapnamen in **indelings tabel**, zodat het laatste pijplijn element kan worden beperkt tot `Format-Table -Property Total,Free`

De geheugen gegevens kunnen beter leesbaar zijn als u deze als een lijst formatteert door het volgende te typen:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
