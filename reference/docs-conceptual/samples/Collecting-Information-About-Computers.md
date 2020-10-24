---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Informatie over computers verzamelen
description: In dit artikel wordt beschreven hoe u informatie over de configuratie van de computer verzameling WMI en CIM-cmdlets gebruikt.
ms.openlocfilehash: 5088960ab7c049085a9d7c05ec4571b6fd7e3545
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500586"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="cdcf0-104">Informatie over computers verzamelen</span><span class="sxs-lookup"><span data-stu-id="cdcf0-104">Collecting Information About Computers</span></span>

<span data-ttu-id="cdcf0-105">Cmdlets van de **CimCmdlets** -module zijn de belangrijkste cmdlets voor algemene systeem beheer taken.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-105">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span> <span data-ttu-id="cdcf0-106">Alle essentiële subsysteem instellingen worden weer gegeven via WMI.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-106">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="cdcf0-107">Daarnaast behandelt WMI gegevens als objecten die zich in verzamelingen van een of meer items bevinden.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-107">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="cdcf0-108">Omdat Windows Power shell ook met objecten werkt en een pijp lijn heeft waarmee u één of meerdere objecten op dezelfde manier kunt behandelen, kunt u met algemene WMI-toegang enkele geavanceerde taken uitvoeren met zeer weinig werk.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-108">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="cdcf0-109">Bureau blad-instellingen weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-109">Listing Desktop Settings</span></span>

<span data-ttu-id="cdcf0-110">We beginnen met een opdracht voor het verzamelen van informatie over de Bureau bladen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-110">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

<span data-ttu-id="cdcf0-111">Hiermee wordt informatie over alle Bureau bladen geretourneerd, ongeacht of deze al dan niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-111">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="cdcf0-112">Gegevens die door bepaalde WMI-klassen worden geretourneerd, kunnen zeer gedetailleerd zijn en bevatten vaak meta gegevens over de WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-112">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>

<span data-ttu-id="cdcf0-113">Omdat de meeste van deze eigenschappen van meta gegevens namen hebben die beginnen met **CIM**, kunt u de eigenschappen filteren met `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="cdcf0-113">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span> <span data-ttu-id="cdcf0-114">Geef de para meter **-ExcludeProperty** op als waarde.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-114">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span> <span data-ttu-id="cdcf0-115">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-115">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="cdcf0-116">Als u de meta gegevens wilt filteren, gebruikt u een pijplijn operator (|) om de resultaten van de `Get-CimInstance` opdracht naar te verzenden `Select-Object -ExcludeProperty "CIM*"` .</span><span class="sxs-lookup"><span data-stu-id="cdcf0-116">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="cdcf0-117">BIOS-gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-117">Listing BIOS Information</span></span>

<span data-ttu-id="cdcf0-118">De WMI- **Win32_BIOS** klasse retourneert tamelijk compact en volledige informatie over het systeem-BIOS op de lokale computer:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-118">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a><span data-ttu-id="cdcf0-119">Processor gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-119">Listing Processor Information</span></span>

<span data-ttu-id="cdcf0-120">U kunt algemene processor gegevens ophalen met behulp van de **Win32_Processor** klasse van WMI, hoewel u waarschijnlijk de informatie wilt filteren:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-120">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="cdcf0-121">Voor een algemene beschrijvings teken reeks van de processor familie kunt u gewoon de eigenschap **System type** retour neren:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-121">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="cdcf0-122">De fabrikant en het model van de computer weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-122">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="cdcf0-123">Informatie over het computer model is ook beschikbaar via **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-123">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="cdcf0-124">De standaard weer gegeven uitvoer heeft geen filters nodig om OEM-gegevens op te geven:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-124">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="cdcf0-125">De uitvoer van opdrachten zoals deze, waarmee informatie rechtstreeks vanuit bepaalde hardware wordt geretourneerd, is alleen van belang voor de gegevens die u hebt.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-125">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="cdcf0-126">Sommige informatie is niet juist geconfigureerd door hardwarefabrikanten en is daarom niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-126">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="cdcf0-127">Geïnstalleerde hotfixes weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-127">Listing Installed Hotfixes</span></span>

<span data-ttu-id="cdcf0-128">U kunt alle geïnstalleerde hotfixes weer geven met behulp van **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-128">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

<span data-ttu-id="cdcf0-129">Deze klasse retourneert een lijst met hotfixes die er als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-129">This class returns a list of hotfixes that looks like this:</span></span>

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="cdcf0-130">Voor een meer beknopte uitvoer wilt u mogelijk sommige eigenschappen uitsluiten.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-130">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="cdcf0-131">Hoewel u de `Get-CimInstance` **eigenschaps** parameter kunt gebruiken om alleen de **HotFixID**te kiezen, wordt er in werkelijkheid meer informatie geretourneerd, omdat alle meta gegevens standaard worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-131">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="cdcf0-132">De extra gegevens worden geretourneerd, omdat de **eigenschaps** parameter in `Get-CimInstance` de eigenschappen van WMI-klasse-instanties beperkt, niet het object dat naar Power shell wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-132">The additional data is returned, because the **Property** parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to PowerShell.</span></span> <span data-ttu-id="cdcf0-133">Gebruik het volgende om de uitvoer te verminderen `Select-Object` :</span><span class="sxs-lookup"><span data-stu-id="cdcf0-133">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="cdcf0-134">Informatie over versie van besturings systeem weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-134">Listing Operating System Version Information</span></span>

<span data-ttu-id="cdcf0-135">De eigenschappen van de **Win32_OperatingSystem** klasse bevatten informatie over de versie en het Service Pack.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-135">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="cdcf0-136">U kunt alleen deze eigenschappen expliciet selecteren om een samen vatting van versie gegevens op te halen van **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-136">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="cdcf0-137">U kunt ook joker tekens gebruiken met de `Select-Object` para meter van de **eigenschap** .</span><span class="sxs-lookup"><span data-stu-id="cdcf0-137">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span> <span data-ttu-id="cdcf0-138">Omdat alle eigenschappen die beginnen met ofwel **Build** of **servicepack** belang rijk zijn om hier te gebruiken, kunnen we het volgende formulier inkorten:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-138">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="cdcf0-139">Lokale gebruikers en eigenaar weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-139">Listing Local Users and Owner</span></span>

<span data-ttu-id="cdcf0-140">Lokale algemene gebruikers informatie: het aantal gelicentieerde gebruikers, het huidige aantal gebruikers en de naam van de eigenaar — kan worden gevonden met een selectie van **Win32_OperatingSystem** klasse-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-140">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class properties.</span></span> <span data-ttu-id="cdcf0-141">U kunt expliciet de eigenschappen selecteren die als volgt worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-141">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="cdcf0-142">Een beknoptere versie met behulp van joker tekens is:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-142">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="cdcf0-143">Beschik bare schijf ruimte ophalen</span><span class="sxs-lookup"><span data-stu-id="cdcf0-143">Getting Available Disk Space</span></span>

<span data-ttu-id="cdcf0-144">Als u de schijf ruimte en de beschik bare ruimte voor lokale stations wilt zien, kunt u de WMI-klasse Win32_LogicalDisk gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-144">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="cdcf0-145">U moet alleen instanties met een DriveType van 3 zien: de waarde WMI gebruikt voor vaste harde schijven.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-145">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="cdcf0-146">Informatie over de aanmeldings sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="cdcf0-146">Getting Logon Session Information</span></span>

<span data-ttu-id="cdcf0-147">U kunt algemene informatie verkrijgen over aanmeldings sessies die zijn gekoppeld aan gebruikers via de WMI-klasse **Win32_LogonSession** :</span><span class="sxs-lookup"><span data-stu-id="cdcf0-147">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="cdcf0-148">De gebruiker die is aangemeld op een computer ophalen</span><span class="sxs-lookup"><span data-stu-id="cdcf0-148">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="cdcf0-149">U kunt de gebruiker die is aangemeld bij een bepaald computer systeem weer geven met behulp van Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-149">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="cdcf0-150">Met deze opdracht wordt alleen de gebruiker die is aangemeld op het bureau blad van het systeem geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-150">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="cdcf0-151">Lokale tijd ophalen van een computer</span><span class="sxs-lookup"><span data-stu-id="cdcf0-151">Getting Local Time from a Computer</span></span>

<span data-ttu-id="cdcf0-152">U kunt de huidige lokale tijd op een specifieke computer ophalen met behulp van de WMI-klasse **Win32_LocalTime** .</span><span class="sxs-lookup"><span data-stu-id="cdcf0-152">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="cdcf0-153">Service status weer geven</span><span class="sxs-lookup"><span data-stu-id="cdcf0-153">Displaying Service Status</span></span>

<span data-ttu-id="cdcf0-154">Als u de status van alle services op een specifieke computer wilt weer geven, kunt u de cmdlet lokaal gebruiken `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="cdcf0-154">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span> <span data-ttu-id="cdcf0-155">Voor externe systemen kunt u de WMI-klasse **Win32_Service** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cdcf0-155">For remote systems, you can use the **Win32_Service** WMI class.</span></span> <span data-ttu-id="cdcf0-156">Als u ook gebruikt `Select-Object` om de resultaten te filteren op **status**, **naam**en **DisplayName**, is de uitvoer indeling bijna identiek aan die van `Get-Service` :</span><span class="sxs-lookup"><span data-stu-id="cdcf0-156">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="cdcf0-157">Als u de volledige weer gave van namen voor incidentele Services met extreem lange namen wilt toestaan, kunt u `Format-Table` met de para meters **AutoSize** en **wrap** gebruiken om de kolom breedte te optimaliseren en lange namen te laten teruglopen in plaats van afgekapt:</span><span class="sxs-lookup"><span data-stu-id="cdcf0-157">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
