---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Informatie over computers verzamelen
ms.openlocfilehash: 5dc8fcc5f12fdf9e3fc8151d3e50b8b660262c62
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030852"
---
# <a name="collecting-information-about-computers"></a>Informatie over computers verzamelen

Cmdlets van de **CimCmdlets** -module zijn de belangrijkste cmdlets voor algemene systeem beheer taken.
Alle essentiële subsysteem instellingen worden weer gegeven via WMI.
Daarnaast behandelt WMI gegevens als objecten die zich in verzamelingen van een of meer items bevinden.
Omdat Windows Power shell ook met objecten werkt en een pijp lijn heeft waarmee u één of meerdere objecten op dezelfde manier kunt behandelen, kunt u met algemene WMI-toegang enkele geavanceerde taken uitvoeren met zeer weinig werk.

De volgende voor beelden laten zien hoe u specifieke informatie kunt verzamelen met behulp van `Get-CimInstance` op een wille keurige computer.
De para meter **ComputerName** wordt opgegeven met de punt waarde ( **.** ), die de lokale computer vertegenwoordigt.
U kunt een naam of IP-adres opgeven dat is gekoppeld aan een computer die u via WMI kunt bereiken.
Als u informatie wilt ophalen over de lokale computer, kunt u de para meter **ComputerName** weglaten.

## <a name="listing-desktop-settings"></a>Bureau blad-instellingen weer geven

We beginnen met een opdracht voor het verzamelen van informatie over de Bureau bladen op de lokale computer.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Hiermee wordt informatie over alle Bureau bladen geretourneerd, ongeacht of deze al dan niet worden gebruikt.

> [!NOTE]
> Gegevens die door bepaalde WMI-klassen worden geretourneerd, kunnen zeer gedetailleerd zijn en bevatten vaak meta gegevens over de WMI-klasse.
Omdat de meeste van deze eigenschappen van meta gegevens namen hebben die beginnen met **CIM**, kunt u de eigenschappen filteren met behulp van `Select-Object`.
Geef de para meter **-ExcludeProperty** op als waarde.
Bijvoorbeeld:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Als u de meta gegevens wilt filteren, gebruikt u een pijplijn operator (|) om de resultaten van de `Get-CimInstance` opdracht naar `Select-Object -ExcludeProperty "CIM*"`te verzenden.

## <a name="listing-bios-information"></a>BIOS-gegevens weer geven

De WMI- **Win32_BIOS** klasse retourneert tamelijk compact en volledige informatie over het systeem-BIOS op de lokale computer:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a>Processor gegevens weer geven

U kunt algemene processor gegevens ophalen met behulp van de **Win32_Processor** klasse van WMI, hoewel u waarschijnlijk de informatie wilt filteren:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Voor een algemene beschrijvings teken reeks van de processor familie kunt u gewoon de eigenschap **System type** retour neren:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>De fabrikant en het model van de computer weer geven

Informatie over het computer model is ook beschikbaar via **Win32_ComputerSystem**.
De standaard weer gegeven uitvoer heeft geen filters nodig om OEM-gegevens op te geven:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

De uitvoer van opdrachten zoals deze, waarmee informatie rechtstreeks vanuit bepaalde hardware wordt geretourneerd, is alleen van belang voor de gegevens die u hebt.
Sommige informatie is niet juist geconfigureerd door hardwarefabrikanten en is daarom niet beschikbaar.

## <a name="listing-installed-hotfixes"></a>Geïnstalleerde hotfixes weer geven

U kunt alle geïnstalleerde hotfixes weer geven met behulp van **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Deze klasse retourneert een lijst met hotfixes die er als volgt uitzien:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Voor een meer beknopte uitvoer wilt u mogelijk sommige eigenschappen uitsluiten.
Hoewel u de **eigenschaps** parameter van de `Get-CimInstance`kunt gebruiken om alleen de **HotFixID**te kiezen, wordt in feite meer informatie geretourneerd, omdat alle meta gegevens standaard worden weer gegeven:

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

De extra gegevens worden geretourneerd, omdat de eigenschaps parameter in `Get-CimInstance` de eigenschappen die worden geretourneerd door WMI-klasse-instanties beperkt, niet het object dat naar Windows Power shell wordt geretourneerd.
Gebruik `Select-Object`om de uitvoer te verminderen:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Informatie over versie van besturings systeem weer geven

De eigenschappen van de **Win32_OperatingSystem** klasse bevatten informatie over de versie en het Service Pack.
U kunt alleen deze eigenschappen expliciet selecteren om een samen vatting van versie gegevens op te halen van **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

U kunt ook joker tekens gebruiken met de **eigenschaps** parameter van de `Select-Object`.
Omdat alle eigenschappen die beginnen met ofwel **Build** of **servicepack** belang rijk zijn om hier te gebruiken, kunnen we het volgende formulier inkorten:

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

## <a name="listing-local-users-and-owner"></a>Lokale gebruikers en eigenaar weer geven

Lokale algemene gebruikers informatie: het aantal gelicentieerde gebruikers, het huidige aantal gebruikers en de naam van de eigenaar — kan worden gevonden met een selectie van **Win32_OperatingSystem** klasse-eigenschappen.
U kunt expliciet de eigenschappen selecteren die als volgt worden weer gegeven:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Een beknoptere versie met behulp van joker tekens is:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Beschik bare schijf ruimte ophalen

Als u de schijf ruimte en de beschik bare ruimte voor lokale stations wilt zien, kunt u de WMI-klasse Win32_LogicalDisk gebruiken.
U moet alleen instanties met een DriveType van 3 zien: de waarde WMI gebruikt voor vaste harde schijven.

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

## <a name="getting-logon-session-information"></a>Informatie over de aanmeldings sessie ophalen

U kunt algemene informatie verkrijgen over aanmeldings sessies die zijn gekoppeld aan gebruikers via de WMI-klasse **Win32_LogonSession** :

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>De gebruiker die is aangemeld op een computer ophalen

U kunt de gebruiker die is aangemeld bij een bepaald computer systeem weer geven met behulp van Win32_ComputerSystem.
Met deze opdracht wordt alleen de gebruiker die is aangemeld op het bureau blad van het systeem geretourneerd:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a>Lokale tijd ophalen van een computer

U kunt de huidige lokale tijd op een specifieke computer ophalen met behulp van de WMI-klasse **Win32_LocalTime** .

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

## <a name="displaying-service-status"></a>Service status weer geven

Als u de status van alle services op een specifieke computer wilt weer geven, kunt u lokaal de `Get-Service`-cmdlet gebruiken.
Voor externe systemen kunt u de WMI-klasse **Win32_Service** gebruiken.
Als u ook `Select-Object` gebruikt om de resultaten te filteren op **status**, **naam**en **DisplayName**, is de uitvoer indeling bijna gelijk aan die van `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Als u de volledige weer gave van namen voor incidentele Services met extreem lange namen wilt toestaan, kunt u `Format-Table` met de para meters **AutoSize** en **wrap** gebruiken om de kolom breedte te optimaliseren en lange namen te laten teruglopen in plaats van afgekapt:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
