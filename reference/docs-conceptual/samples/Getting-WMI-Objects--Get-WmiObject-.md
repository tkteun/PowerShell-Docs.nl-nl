---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Ophalen van WMI-objecten WmiObject
ms.openlocfilehash: 23fd8cf596a8be7e36651ac3f9c79ca97240e647
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737216"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>WMI-objecten ophalen (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>WMI-objecten ophalen (Get-WmiObject)

Windows Management Instrumentation (WMI) is een kern technologie voor Windows-systeem beheer, omdat een breed scala aan gegevens op een uniforme manier wordt weer gegeven. Als gevolg van de mate waarin WMI mogelijk is, is de Power shell-cmdlet voor toegang tot WMI-objecten, `Get-CimInstance`, een van de handigste voor het uitvoeren van echte werk. We bespreken hoe u de CimCmdlets kunt gebruiken voor toegang tot WMI-objecten en hoe u WMI-objecten kunt gebruiken om specifieke dingen uit te voeren.

### <a name="listing-wmi-classes"></a>WMI-klassen weer geven

Het eerste probleem dat de meeste WMI-gebruikers ondervindt, probeert te ontdekken wat er met WMI kan worden gedaan. WMI-klassen beschrijven de resources die kunnen worden beheerd. Er zijn honderden WMI-klassen waarvan sommige van de eigenschappen tien tallen bevatten.

`Get-CimClass` lost dit probleem op door WMI detecteerbaar te maken. U kunt een lijst weer geven van de WMI-klassen die beschikbaar zijn op de lokale computer door het volgende te typen:

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

U kunt dezelfde gegevens ophalen van een externe computer met behulp van de para meter **ComputerName** , waarbij u een computer naam of IP-adres opgeeft:

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

De lijst met klassen die door externe computers wordt geretourneerd, kan variëren als gevolg van het specifieke besturings systeem dat op de computer wordt uitgevoerd en de specifieke WMI-uitbrei dingen die zijn toegevoegd door geïnstalleerde toepassingen.

> [!NOTE]
> Wanneer u CIM-cmdlets gebruikt om verbinding te maken met een externe computer, moet op de externe computer WMI worden uitgevoerd en moet het account dat u gebruikt zich in de lokale groep Administrators op de externe computer bevinden.
> Power shell hoeft niet te zijn geïnstalleerd op het externe systeem. Hierdoor kunt u besturings systemen beheren waarop Power shell niet wordt uitgevoerd, maar waarvoor WMI wel beschikbaar is.

### <a name="displaying-wmi-class-details"></a>Details van WMI-klasse weer geven

Als u de naam van een WMI-klasse al kent, kunt u deze gebruiken om informatie direct op te halen. Zo is een van de WMI-klassen die meestal worden gebruikt voor het ophalen van informatie over een computer is **Win32_OperatingSystem**.

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

Hoewel alle para meters worden weer gegeven, kan de opdracht op een meer beknopte manier worden aangegeven.
De para meter **ComputerName** is niet nodig bij het maken van verbinding met het lokale systeem. We laten u zien hoe u het meest algemene geval kunt demonstreren en u kunt u herinneren over de para meter. De **naam ruimte** wordt standaard ingesteld op `root/CIMV2`en kan ook worden wegge laten. Ten slotte kunt u met de meeste cmdlets de naam van algemene para meters weglaten. Als er bij `Get-CimInstance`geen naam is opgegeven voor de eerste para meter, wordt deze door Power shell beschouwd als de **klasse** -para meter. Dit betekent dat de laatste opdracht kan zijn uitgegeven door het volgende te typen:

```powershell
Get-WmiObject Win32_OperatingSystem
```

De klasse **Win32_OperatingSystem** heeft veel meer eigenschappen dan hier wordt weer gegeven. U kunt Get-member gebruiken om alle eigenschappen te bekijken. De eigenschappen van een WMI-klasse zijn automatisch beschikbaar, net als andere object eigenschappen:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Niet-standaard eigenschappen weer geven met Format-cmdlets

Als u informatie wilt weer geven in de klasse **Win32_OperatingSystem** die niet standaard wordt weer gegeven, kunt u de gegevens met behulp van de **Format** -cmdlets bekijken. Als u bijvoorbeeld beschik bare geheugen gegevens wilt weer geven, typt u:

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> Joker tekens werken met eigenschapnamen in `Format-Table`, zodat het laatste pijplijn element kan worden gereduceerd tot `Format-Table -Property Total*Memory*, Free*`

De geheugen gegevens kunnen beter leesbaar zijn als u deze als een lijst formatteert door het volgende te typen:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
