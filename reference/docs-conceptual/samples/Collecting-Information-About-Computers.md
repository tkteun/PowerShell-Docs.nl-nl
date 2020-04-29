---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Informatie over computers verzamelen
ms.openlocfilehash: 9407ff15b3c3ca6b3adab60d4d01d957c599e79e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737233"
---
# <a name="collecting-information-about-computers"></a>Informatie over computers verzamelen

Cmdlets van de **CimCmdlets** -module zijn de belangrijkste cmdlets voor algemene systeem beheer taken. Alle essentiële subsysteem instellingen worden weer gegeven via WMI. Daarnaast behandelt WMI gegevens als objecten die zich in verzamelingen van een of meer items bevinden. Omdat Windows Power shell ook met objecten werkt en een pijp lijn heeft waarmee u één of meerdere objecten op dezelfde manier kunt behandelen, kunt u met algemene WMI-toegang enkele geavanceerde taken uitvoeren met zeer weinig werk.

## <a name="listing-desktop-settings"></a>Bureau blad-instellingen weer geven

We beginnen met een opdracht voor het verzamelen van informatie over de Bureau bladen op de lokale computer.

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

Hiermee wordt informatie over alle Bureau bladen geretourneerd, ongeacht of deze al dan niet worden gebruikt.

> [!NOTE]
> Gegevens die door bepaalde WMI-klassen worden geretourneerd, kunnen zeer gedetailleerd zijn en bevatten vaak meta gegevens over de WMI-klasse.

Omdat de meeste van deze eigenschappen van meta gegevens namen hebben die beginnen met **CIM**, kunt u de `Select-Object`eigenschappen filteren met. Geef de para meter **-ExcludeProperty** op als waarde. Bijvoorbeeld:

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

Als u de meta gegevens wilt filteren, gebruikt u een pijplijn operator (|) om de resultaten van `Get-CimInstance` de opdracht `Select-Object -ExcludeProperty "CIM*"`naar te verzenden.

## <a name="listing-bios-information"></a>BIOS-gegevens weer geven

De WMI- **Win32_BIOS** klasse retourneert tamelijk compact en volledige informatie over het systeem-BIOS op de lokale computer:

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a>Processor gegevens weer geven

U kunt algemene processor gegevens ophalen met behulp van de **Win32_Processor** klasse van WMI, hoewel u waarschijnlijk de informatie wilt filteren:

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

Voor een algemene beschrijvings teken reeks van de processor familie kunt u gewoon de eigenschap **System type** retour neren:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>De fabrikant en het model van de computer weer geven

Informatie over het computer model is ook beschikbaar via **Win32_ComputerSystem**. De standaard weer gegeven uitvoer heeft geen filters nodig om OEM-gegevens op te geven:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

De uitvoer van opdrachten zoals deze, waarmee informatie rechtstreeks vanuit bepaalde hardware wordt geretourneerd, is alleen van belang voor de gegevens die u hebt. Sommige informatie is niet juist geconfigureerd door hardwarefabrikanten en is daarom niet beschikbaar.

## <a name="listing-installed-hotfixes"></a>Geïnstalleerde hotfixes weer geven

U kunt alle geïnstalleerde hotfixes weer geven met behulp van **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

Deze klasse retourneert een lijst met hotfixes die er als volgt uitzien:

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Voor een meer beknopte uitvoer wilt u mogelijk sommige eigenschappen uitsluiten. Hoewel u de `Get-CimInstance` **eigenschaps** parameter kunt gebruiken om alleen de **HotFixID**te kiezen, wordt er in werkelijkheid meer informatie geretourneerd, omdat alle meta gegevens standaard worden weer gegeven:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

De extra gegevens worden geretourneerd, omdat de **eigenschaps** parameter `Get-CimInstance` in de eigenschappen van WMI-klasse-instanties beperkt, niet het object dat naar Power shell wordt geretourneerd. Gebruik `Select-Object`het volgende om de uitvoer te verminderen:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Informatie over versie van besturings systeem weer geven

De eigenschappen van de **Win32_OperatingSystem** klasse bevatten informatie over de versie en het Service Pack. U kunt alleen deze eigenschappen expliciet selecteren om een samen vatting van versie gegevens op te halen van **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

U kunt ook joker tekens gebruiken met de `Select-Object`para meter van de **eigenschap** . Omdat alle eigenschappen die beginnen met ofwel **Build** of **servicepack** belang rijk zijn om hier te gebruiken, kunnen we het volgende formulier inkorten:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>Lokale gebruikers en eigenaar weer geven

Lokale algemene gebruikers informatie: het aantal gelicentieerde gebruikers, het huidige aantal gebruikers en de naam van de eigenaar — kan worden gevonden met een selectie van **Win32_OperatingSystem** klasse-eigenschappen. U kunt expliciet de eigenschappen selecteren die als volgt worden weer gegeven:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Een beknoptere versie met behulp van joker tekens is:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Beschik bare schijf ruimte ophalen

Als u de schijf ruimte en de beschik bare ruimte voor lokale stations wilt zien, kunt u de WMI-klasse Win32_LogicalDisk gebruiken.
U moet alleen instanties met een DriveType van 3 zien: de waarde WMI gebruikt voor vaste harde schijven.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>Informatie over de aanmeldings sessie ophalen

U kunt algemene informatie verkrijgen over aanmeldings sessies die zijn gekoppeld aan gebruikers via de WMI-klasse **Win32_LogonSession** :

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>De gebruiker die is aangemeld op een computer ophalen

U kunt de gebruiker die is aangemeld bij een bepaald computer systeem weer geven met behulp van Win32_ComputerSystem. Met deze opdracht wordt alleen de gebruiker die is aangemeld op het bureau blad van het systeem geretourneerd:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a>Lokale tijd ophalen van een computer

U kunt de huidige lokale tijd op een specifieke computer ophalen met behulp van de WMI-klasse **Win32_LocalTime** .

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a>Service status weer geven

Als u de status van alle services op een specifieke computer wilt weer geven, kunt u `Get-Service` de cmdlet lokaal gebruiken. Voor externe systemen kunt u de WMI-klasse **Win32_Service** gebruiken. Als u ook gebruikt `Select-Object` om de resultaten te filteren op **status**, **naam**en **DisplayName**, is de uitvoer indeling bijna identiek aan die van `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

Als u de volledige weer gave van namen voor incidentele Services met extreem lange namen wilt toestaan, kunt u met `Format-Table` de para meters **AutoSize** en **wrap** gebruiken om de kolom breedte te optimaliseren en lange namen te laten teruglopen in plaats van afgekapt:

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
