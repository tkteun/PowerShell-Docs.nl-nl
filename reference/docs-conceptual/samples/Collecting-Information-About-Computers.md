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
# <a name="collecting-information-about-computers"></a><span data-ttu-id="00904-103">Informatie over computers verzamelen</span><span class="sxs-lookup"><span data-stu-id="00904-103">Collecting Information About Computers</span></span>

<span data-ttu-id="00904-104">Cmdlets van de **CimCmdlets** -module zijn de belangrijkste cmdlets voor algemene systeem beheer taken.</span><span class="sxs-lookup"><span data-stu-id="00904-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="00904-105">Alle essentiële subsysteem instellingen worden weer gegeven via WMI.</span><span class="sxs-lookup"><span data-stu-id="00904-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="00904-106">Daarnaast behandelt WMI gegevens als objecten die zich in verzamelingen van een of meer items bevinden.</span><span class="sxs-lookup"><span data-stu-id="00904-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="00904-107">Omdat Windows Power shell ook met objecten werkt en een pijp lijn heeft waarmee u één of meerdere objecten op dezelfde manier kunt behandelen, kunt u met algemene WMI-toegang enkele geavanceerde taken uitvoeren met zeer weinig werk.</span><span class="sxs-lookup"><span data-stu-id="00904-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="00904-108">De volgende voor beelden laten zien hoe u specifieke informatie kunt verzamelen met behulp van `Get-CimInstance` op een wille keurige computer.</span><span class="sxs-lookup"><span data-stu-id="00904-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="00904-109">De para meter **ComputerName** wordt opgegeven met de punt waarde ( **.** ), die de lokale computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="00904-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="00904-110">U kunt een naam of IP-adres opgeven dat is gekoppeld aan een computer die u via WMI kunt bereiken.</span><span class="sxs-lookup"><span data-stu-id="00904-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="00904-111">Als u informatie wilt ophalen over de lokale computer, kunt u de para meter **ComputerName** weglaten.</span><span class="sxs-lookup"><span data-stu-id="00904-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="00904-112">Bureau blad-instellingen weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-112">Listing Desktop Settings</span></span>

<span data-ttu-id="00904-113">We beginnen met een opdracht voor het verzamelen van informatie over de Bureau bladen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="00904-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="00904-114">Hiermee wordt informatie over alle Bureau bladen geretourneerd, ongeacht of deze al dan niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00904-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="00904-115">Gegevens die door bepaalde WMI-klassen worden geretourneerd, kunnen zeer gedetailleerd zijn en bevatten vaak meta gegevens over de WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="00904-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="00904-116">Omdat de meeste van deze eigenschappen van meta gegevens namen hebben die beginnen met **CIM**, kunt u de eigenschappen filteren met behulp van `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="00904-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="00904-117">Geef de para meter **-ExcludeProperty** op als waarde.</span><span class="sxs-lookup"><span data-stu-id="00904-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="00904-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="00904-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="00904-119">Als u de meta gegevens wilt filteren, gebruikt u een pijplijn operator (|) om de resultaten van de `Get-CimInstance` opdracht naar `Select-Object -ExcludeProperty "CIM*"`te verzenden.</span><span class="sxs-lookup"><span data-stu-id="00904-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="00904-120">BIOS-gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-120">Listing BIOS Information</span></span>

<span data-ttu-id="00904-121">De WMI- **Win32_BIOS** klasse retourneert tamelijk compact en volledige informatie over het systeem-BIOS op de lokale computer:</span><span class="sxs-lookup"><span data-stu-id="00904-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a><span data-ttu-id="00904-122">Processor gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-122">Listing Processor Information</span></span>

<span data-ttu-id="00904-123">U kunt algemene processor gegevens ophalen met behulp van de **Win32_Processor** klasse van WMI, hoewel u waarschijnlijk de informatie wilt filteren:</span><span class="sxs-lookup"><span data-stu-id="00904-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="00904-124">Voor een algemene beschrijvings teken reeks van de processor familie kunt u gewoon de eigenschap **System type** retour neren:</span><span class="sxs-lookup"><span data-stu-id="00904-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="00904-125">De fabrikant en het model van de computer weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="00904-126">Informatie over het computer model is ook beschikbaar via **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="00904-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="00904-127">De standaard weer gegeven uitvoer heeft geen filters nodig om OEM-gegevens op te geven:</span><span class="sxs-lookup"><span data-stu-id="00904-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="00904-128">De uitvoer van opdrachten zoals deze, waarmee informatie rechtstreeks vanuit bepaalde hardware wordt geretourneerd, is alleen van belang voor de gegevens die u hebt.</span><span class="sxs-lookup"><span data-stu-id="00904-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="00904-129">Sommige informatie is niet juist geconfigureerd door hardwarefabrikanten en is daarom niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="00904-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="00904-130">Geïnstalleerde hotfixes weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="00904-131">U kunt alle geïnstalleerde hotfixes weer geven met behulp van **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="00904-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="00904-132">Deze klasse retourneert een lijst met hotfixes die er als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="00904-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="00904-133">Voor een meer beknopte uitvoer wilt u mogelijk sommige eigenschappen uitsluiten.</span><span class="sxs-lookup"><span data-stu-id="00904-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="00904-134">Hoewel u de **eigenschaps** parameter van de `Get-CimInstance`kunt gebruiken om alleen de **HotFixID**te kiezen, wordt in feite meer informatie geretourneerd, omdat alle meta gegevens standaard worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="00904-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="00904-135">De extra gegevens worden geretourneerd, omdat de eigenschaps parameter in `Get-CimInstance` de eigenschappen die worden geretourneerd door WMI-klasse-instanties beperkt, niet het object dat naar Windows Power shell wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="00904-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="00904-136">Gebruik `Select-Object`om de uitvoer te verminderen:</span><span class="sxs-lookup"><span data-stu-id="00904-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="00904-137">Informatie over versie van besturings systeem weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="00904-138">De eigenschappen van de **Win32_OperatingSystem** klasse bevatten informatie over de versie en het Service Pack.</span><span class="sxs-lookup"><span data-stu-id="00904-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="00904-139">U kunt alleen deze eigenschappen expliciet selecteren om een samen vatting van versie gegevens op te halen van **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="00904-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="00904-140">U kunt ook joker tekens gebruiken met de **eigenschaps** parameter van de `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="00904-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="00904-141">Omdat alle eigenschappen die beginnen met ofwel **Build** of **servicepack** belang rijk zijn om hier te gebruiken, kunnen we het volgende formulier inkorten:</span><span class="sxs-lookup"><span data-stu-id="00904-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="00904-142">Lokale gebruikers en eigenaar weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="00904-143">Lokale algemene gebruikers informatie: het aantal gelicentieerde gebruikers, het huidige aantal gebruikers en de naam van de eigenaar — kan worden gevonden met een selectie van **Win32_OperatingSystem** klasse-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="00904-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="00904-144">U kunt expliciet de eigenschappen selecteren die als volgt worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="00904-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="00904-145">Een beknoptere versie met behulp van joker tekens is:</span><span class="sxs-lookup"><span data-stu-id="00904-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="00904-146">Beschik bare schijf ruimte ophalen</span><span class="sxs-lookup"><span data-stu-id="00904-146">Getting Available Disk Space</span></span>

<span data-ttu-id="00904-147">Als u de schijf ruimte en de beschik bare ruimte voor lokale stations wilt zien, kunt u de WMI-klasse Win32_LogicalDisk gebruiken.</span><span class="sxs-lookup"><span data-stu-id="00904-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="00904-148">U moet alleen instanties met een DriveType van 3 zien: de waarde WMI gebruikt voor vaste harde schijven.</span><span class="sxs-lookup"><span data-stu-id="00904-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="00904-149">Informatie over de aanmeldings sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="00904-149">Getting Logon Session Information</span></span>

<span data-ttu-id="00904-150">U kunt algemene informatie verkrijgen over aanmeldings sessies die zijn gekoppeld aan gebruikers via de WMI-klasse **Win32_LogonSession** :</span><span class="sxs-lookup"><span data-stu-id="00904-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="00904-151">De gebruiker die is aangemeld op een computer ophalen</span><span class="sxs-lookup"><span data-stu-id="00904-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="00904-152">U kunt de gebruiker die is aangemeld bij een bepaald computer systeem weer geven met behulp van Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="00904-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="00904-153">Met deze opdracht wordt alleen de gebruiker die is aangemeld op het bureau blad van het systeem geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="00904-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="00904-154">Lokale tijd ophalen van een computer</span><span class="sxs-lookup"><span data-stu-id="00904-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="00904-155">U kunt de huidige lokale tijd op een specifieke computer ophalen met behulp van de WMI-klasse **Win32_LocalTime** .</span><span class="sxs-lookup"><span data-stu-id="00904-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="00904-156">Service status weer geven</span><span class="sxs-lookup"><span data-stu-id="00904-156">Displaying Service Status</span></span>

<span data-ttu-id="00904-157">Als u de status van alle services op een specifieke computer wilt weer geven, kunt u lokaal de `Get-Service`-cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="00904-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="00904-158">Voor externe systemen kunt u de WMI-klasse **Win32_Service** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="00904-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="00904-159">Als u ook `Select-Object` gebruikt om de resultaten te filteren op **status**, **naam**en **DisplayName**, is de uitvoer indeling bijna gelijk aan die van `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="00904-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="00904-160">Als u de volledige weer gave van namen voor incidentele Services met extreem lange namen wilt toestaan, kunt u `Format-Table` met de para meters **AutoSize** en **wrap** gebruiken om de kolom breedte te optimaliseren en lange namen te laten teruglopen in plaats van afgekapt:</span><span class="sxs-lookup"><span data-stu-id="00904-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
