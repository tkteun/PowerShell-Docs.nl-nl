---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Informatie over computers verzamelen
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 99125ef701705c20d4e955c79eaa3469ce4d58fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688943"
---
# <a name="collecting-information-about-computers"></a>Informatie over computers verzamelen

Cmdlets van **CimCmdlets** module zijn de belangrijkste-cmdlets voor algemene systeem-beheertaken.
Alle kritiek subsysteeminstellingen worden weergegeven via WMI.
Bovendien worden WMI gegevens behandeld als objecten die in verzamelingen van een of meer items voorkomen.
Omdat Windows PowerShell ook met objecten werkt en een pijplijn waarmee u één of meerdere objecten op dezelfde manier behandelen heeft, wordt er algemene WMI-toegang kunt u sommige geavanceerde taken met weinig werk uit te voeren.

De volgende voorbeelden laten zien hoe u specifieke informatie verzamelen met behulp van `Get-CimInstance` op basis van een willekeurige computer.
We geven de **ComputerName** parameter met de waarde van de punt (**.**), die staat voor de lokale computer.
U kunt een naam of IP-adres dat is gekoppeld aan elke computer die u via WMI bereiken kan.
Als u wilt ophalen van informatie over de lokale computer, zou u de **ComputerName** parameter.

### <a name="listing-desktop-settings"></a>Bureaublad-instellingen weergeven

We beginnen met met een opdracht die u informatie over de bureaubladen op de lokale computer verzamelt.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Hiermee wordt informatie voor alle bureaubladen, ongeacht of deze in gebruik is of niet.

> [!NOTE]
> Informatie die wordt geretourneerd door een WMI-klassen kan worden zeer gedetailleerde en metagegevens over de WMI-klasse vaak bevatten.
Omdat de meeste van deze metagegevenseigenschappen namen die beginnen hebben met **Cim**, kunt u de eigenschappen die met behulp van filteren `Select-Object`.
Geef de **- ExcludeProperty** parameter met 'Cim *' als de waarde.
Bijvoorbeeld:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Als u wilt filteren de metagegevens, gebruikt u een pipeline-operator (|) voor het verzenden van de resultaten van de `Get-CimInstance` opdracht `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>BIOS-gegevens weergeven

De WMI **Win32_BIOS** klasse retourneert vrij compact en volledige informatie over het systeem-BIOS op de lokale computer:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Processorgegevens van aanbieding

U kunt algemene processorgegevens ophalen met behulp van WMI **Win32_Processor** klasse, hoewel u wellicht wilt, de gegevens wilt filteren:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Voor een algemene beschrijving van de processor-familie, kunt u alleen retourneren de **SystemType** eigenschap:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Aanbieding computerfabrikant en Model

Computergegevens model is ook beschikbaar via **Win32_ComputerSystem**.
De standaarduitvoer weergegeven hoeft niet alle filters voor OEM-gegevens:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

De uitvoer van opdrachten, zoals deze, die informatie rechtstreeks uit bepaalde hardware retourneert, is alleen nuttig als de gegevens die u hebt.
Sommige informatie niet juist is geconfigureerd door hardwarefabrikanten en kan daarom niet beschikbaar.

### <a name="listing-installed-hotfixes"></a>Aanbieding Hotfixes geïnstalleerd

U kunt alle geïnstalleerde hotfixes weergeven met behulp van **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Deze klasse wordt een lijst van hotfixes aan die er als uitzien volgt:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Voor meer beknopte uitvoer, kunt u bepaalde eigenschappen uitsluiten.
Hoewel u kunt de `Get-CimInstance`van **eigenschap** parameter kiest u alleen de **HotFixID**, als dit dus, retourneren meer informatie, omdat alle metagegevens wordt standaard weergegeven:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

De aanvullende gegevens worden geretourneerd, omdat de eigenschap parameter in `Get-CimInstance` Hiermee beperkt u de eigenschappen die zijn geretourneerd door de WMI-klasse-instanties, niet op het object geretourneerd naar de Windows PowerShell.
Gebruik om te verminderen van de uitvoer, `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>Informatie over de versie van besturingssysteem vermelden

De **Win32_OperatingSystem** klasse-eigenschappen ook versie- en service pack.
U kunt alleen deze eigenschappen voor een versie-informatie van samenvatting expliciet selecteren **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

U kunt ook jokertekens met de `Select-Object`van **eigenschap** parameter.
Omdat alle eigenschappen die beginnen met een **bouwen** of **ServicePack** zijn belangrijk dat u hier, we dit kunnen korter naar de volgende notatie:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Lokale gebruikers en de eigenaar aanbieding

Lokale, algemene gebruikersgegevens: aantal gelicentieerde gebruikers, het huidige aantal gebruikers en de naam van de eigenaar, vindt u een selectie van **Win32_OperatingSystem** de klasse-eigenschappen.
U kunt de eigenschappen weer te geven, zoals dit expliciet selecteren:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Er is een meer beknopte versie met jokertekens:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Beschikbare ruimte op schijf ophalen

Als u wilt zien van de schijfruimte en de vrije ruimte voor lokale stations, kunt u de Win32_LogicalDisk WMI-klasse.
U wilt zien alleen exemplaren met een DriveType van 3: de waarde die WMI gebruikt voor vaste harde schijven.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Aanmeldingsgegevens voor de sessie ophalen

U kunt algemene informatie over aanmeldingssessies die zijn gekoppeld aan gebruikers via de **Win32_LogonSession** WMI-klasse:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Ophalen van de gebruiker is aangemeld op een Computer

U kunt de gebruiker is aangemeld bij een bepaalde computer met behulp van Win32_ComputerSystem weergeven.
Met deze opdracht retourneert alleen de gebruiker aangemeld op het bureaublad system:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Lokale tijd ophalen van een Computer

U kunt de huidige lokale tijd op een specifieke computer ophalen met behulp van de **Win32_LocalTime** WMI-klasse.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a>Servicestatus weergeven

Als u wilt weergeven van de status van alle services op een specifieke computer, u lokaal kunt gebruiken de `Get-Service` cmdlet.
Voor externe systemen, kunt u de **Win32_Service** WMI-klasse.
Als u ook `Select-Object` de resultaten te filteren **Status**, **naam**, en **DisplayName**, de indeling van de uitvoer is bijna identiek is aan die van `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Als u wilt toestaan dat de volledige weergave van namen voor de services die af en toe met zeer lange namen, wilt u mogelijk gebruiken `Format-Table` met de **AutoSize** en **verpakken** parameters, het optimaliseren van de kolombreedte en lange namen om in te verpakken in plaats van het afkappen van toestaan:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
