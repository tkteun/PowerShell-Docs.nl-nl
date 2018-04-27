---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Informatie over computers verzamelen
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 7f5a5f6accd57a84e2bcb3d20c14640a8e028791
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2018
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="1c0fc-103">Informatie over computers verzamelen</span><span class="sxs-lookup"><span data-stu-id="1c0fc-103">Collecting Information About Computers</span></span>

<span data-ttu-id="1c0fc-104">**Get-WmiObject** is de belangrijkste cmdlet voor het algemene system beheertaken.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="1c0fc-105">Alle kritieke subsysteeminstellingen beschikbaar worden gesteld via WMI.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="1c0fc-106">Bovendien worden WMI gegevens behandeld als objecten die zich in verzamelingen van een of meer items.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="1c0fc-107">Omdat Windows PowerShell ook met objecten werkt en een pijplijn waarmee u één of meerdere objecten op dezelfde manier behandelen heeft, wordt er algemene WMI-toegang kunt u sommige geavanceerde taken met weinig werk uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="1c0fc-108">De volgende voorbeelden laten zien hoe u specifieke informatie verzamelen met behulp van **Get-WmiObject** op een willekeurige computer.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="1c0fc-109">We geven de **ComputerName** parameter met de waarde van de punt (**.**), die staat voor de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="1c0fc-110">U kunt een naam of IP-adres die zijn gekoppeld aan elke computer die u via WMI bereiken kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="1c0fc-111">Voor het ophalen van informatie over de lokale computer, zou u de **- ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="1c0fc-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="1c0fc-112">Instellingen voor het bureaublad van aanbieding</span><span class="sxs-lookup"><span data-stu-id="1c0fc-112">Listing Desktop Settings</span></span>

<span data-ttu-id="1c0fc-113">Er moet beginnen met een opdracht die u informatie over de bureaubladen op de lokale computer verzamelt.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="1c0fc-114">Hiermee wordt informatie voor alle bureaubladen, ongeacht of deze in gebruik of niet.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="1c0fc-115">Informatie die wordt geretourneerd door een WMI-klassen worden zeer gedetailleerde, en bevatten vaak metagegevens over de WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="1c0fc-116">Omdat de meeste van deze metagegevenseigenschappen namen die met een dubbele onderstrepingsteken hebben beginnen, kunt u de Select-Object met eigenschappen te filteren.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="1c0fc-117">Alleen eigenschappen die beginnen met alfabetische tekens opgeven via **[a-z]**\* als de waarde van eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-117">Specify only properties that begin with alphabetic characters by using **[a-z]**\* as the Property value.</span></span> <span data-ttu-id="1c0fc-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-118">For example:</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="1c0fc-119">Gebruiken om te filteren om de metagegevens, een pipeline-operator (|) om de resultaten van de opdracht Get-WmiObject te verzenden naar `Select-Object -Property [a-z]*`.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to `Select-Object -Property [a-z]*`.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="1c0fc-120">Aanbieding BIOS-gegevens</span><span class="sxs-lookup"><span data-stu-id="1c0fc-120">Listing BIOS Information</span></span>

<span data-ttu-id="1c0fc-121">De klasse WMI Win32_BIOS retourneert redelijk compact en volledige informatie over het systeem-BIOS op de lokale computer:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="1c0fc-122">Processorinformatie van aanbieding</span><span class="sxs-lookup"><span data-stu-id="1c0fc-122">Listing Processor Information</span></span>

<span data-ttu-id="1c0fc-123">U kunt algemene processorgegevens ophalen met behulp van WMI **Win32_Processor** klasse, hoewel u waarschijnlijk wilt u de informatie filteren:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="1c0fc-124">Voor een algemene beschrijving van de processor-serie, kunt u alleen retourneren de **SystemType** eigenschap:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="1c0fc-125">Aanbieding computerfabrikant en Model</span><span class="sxs-lookup"><span data-stu-id="1c0fc-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="1c0fc-126">Modelgegevens van de computer is ook beschikbaar via **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="1c0fc-127">De standaarduitvoer weergegeven, hoeven niet filteren zodat OEM-gegevens:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="1c0fc-128">De uitvoer van opdrachten zoals deze, die informatie rechtstreeks uit andere hardware retourneert, is alleen nuttig als de gegevens die u hebt.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="1c0fc-129">Sommige informatie is niet correct geconfigureerd voor hardwarefabrikanten en kan daarom niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="1c0fc-130">In de lijst geïnstalleerde Hotfixes</span><span class="sxs-lookup"><span data-stu-id="1c0fc-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="1c0fc-131">U kunt alle geïnstalleerde hotfixes weergeven met behulp van **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="1c0fc-132">Deze klasse retourneert een lijst van hotfixes aan die er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

<span data-ttu-id="1c0fc-133">Voor meer beknopte uitvoer kan u wilt uitsluiten van sommige eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="1c0fc-134">Hoewel u met de **Get-WmiObject eigenschap** parameter te kiezen alleen de **HotFixID**, doen dus, retourneren meer informatie, omdat de metagegevens wordt standaard weergegeven:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID

HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

<span data-ttu-id="1c0fc-135">De aanvullende gegevens wordt geretourneerd, omdat de parameter Property in **Get-WmiObject** Hiermee beperkt u de eigenschappen die zijn geretourneerd door de WMI-klasse-instanties niet het object teruggegeven aan Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="1c0fc-136">Als u de uitvoer, gebruik **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="1c0fc-137">Gegevens over de besturingssysteemversie aanbieding</span><span class="sxs-lookup"><span data-stu-id="1c0fc-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="1c0fc-138">De **Win32_OperatingSystem** klasseneigenschappen zijn onder meer informatie over het versie en service pack.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="1c0fc-139">U kunt alleen deze eigenschappen voor een versie-informatie van samenvatting expliciet selecteren **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="1c0fc-140">U kunt ook jokertekens met de **Select-Object eigenschap** parameter.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="1c0fc-141">Omdat alle eigenschappen die beginnen met een **bouwen** of **ServicePack** zijn belangrijk dat u hier we kunt moet u dit de volgende notatie:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="1c0fc-142">Lokale gebruikers en de eigenaar aanbieding</span><span class="sxs-lookup"><span data-stu-id="1c0fc-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="1c0fc-143">Algemene van gebruikersgegevens: aantal gelicentieerde gebruikers, het huidige aantal gebruikers en de naam van de eigenaar, vindt u een selectie van **Win32_OperatingSystem** eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="1c0fc-144">U kunt de eigenschappen weer te geven als volgt expliciet selecteren:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="1c0fc-145">Er is een meer beknopte versie gebruik van jokertekens:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="1c0fc-146">Ophalen van beschikbare schijfruimte</span><span class="sxs-lookup"><span data-stu-id="1c0fc-146">Getting Available Disk Space</span></span>

<span data-ttu-id="1c0fc-147">Overzicht van de schijfruimte en de vrije ruimte voor lokale stations, kunt u de Win32_LogicalDisk WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="1c0fc-148">U wilt zien alleen exemplaren met een DriveType van 3: de waarde die WMI gebruikt voor vaste harde schijven.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="1c0fc-149">Sessie-aanmeldingsgegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="1c0fc-149">Getting Logon Session Information</span></span>

<span data-ttu-id="1c0fc-150">U kunt algemene informatie over aanmeldingssessies die zijn gekoppeld aan gebruikers via de Win32_LogonSession WMI-klasse krijgen:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="1c0fc-151">Ophalen van de gebruiker is aangemeld op een Computer</span><span class="sxs-lookup"><span data-stu-id="1c0fc-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="1c0fc-152">U kunt de gebruiker is aangemeld bij een bepaalde computer met behulp van Win32_ComputerSystem weergeven.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="1c0fc-153">Met deze opdracht retourneert alleen de gebruiker aangemeld op het bureaublad systeem:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="1c0fc-154">Ophalen van de lokale tijd van een Computer</span><span class="sxs-lookup"><span data-stu-id="1c0fc-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="1c0fc-155">U kunt de huidige lokale tijd op een specifieke computer ophalen met behulp van de Win32_LocalTime WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="1c0fc-156">Omdat deze klasse standaard worden alle metagegevens weergegeven, u kunt filteren met behulp van **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a><span data-ttu-id="1c0fc-157">Servicestatus weergeven</span><span class="sxs-lookup"><span data-stu-id="1c0fc-157">Displaying Service Status</span></span>

<span data-ttu-id="1c0fc-158">Om weer te geven de status van alle services op een specifieke computer, u lokaal kunt gebruiken de **Get-Service** cmdlet zoals eerder vermeld.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="1c0fc-159">Voor externe systemen, kunt u de WMI-Win32_Service-klasse.</span><span class="sxs-lookup"><span data-stu-id="1c0fc-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="1c0fc-160">Als u ook **Select-Object** de resultaten te filteren **Status**, **naam**, en **DisplayName**, de indeling van de uitvoer is bijna identiek is aan die van **Get-Service**:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="1c0fc-161">Als u de volledige weergave van namen voor de incidentele services met zeer lange namen, kunt u gebruiken **Format-Table** met de **AutoSize** en **teruglopen** parameters , te optimaliseren kolombreedte en lange namen om te verpakken in plaats van worden afgekapt toestaan:</span><span class="sxs-lookup"><span data-stu-id="1c0fc-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
