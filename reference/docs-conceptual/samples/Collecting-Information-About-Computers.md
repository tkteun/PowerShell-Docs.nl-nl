---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Informatie over computers verzamelen
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: d837684108656e17ebf26189bd4841c5de01051c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058332"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="7ba05-103">Informatie over computers verzamelen</span><span class="sxs-lookup"><span data-stu-id="7ba05-103">Collecting Information About Computers</span></span>

<span data-ttu-id="7ba05-104">Cmdlets van **CimCmdlets** module zijn de belangrijkste-cmdlets voor algemene systeem-beheertaken.</span><span class="sxs-lookup"><span data-stu-id="7ba05-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="7ba05-105">Alle kritiek subsysteeminstellingen worden weergegeven via WMI.</span><span class="sxs-lookup"><span data-stu-id="7ba05-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="7ba05-106">Bovendien worden WMI gegevens behandeld als objecten die in verzamelingen van een of meer items voorkomen.</span><span class="sxs-lookup"><span data-stu-id="7ba05-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="7ba05-107">Omdat Windows PowerShell ook met objecten werkt en een pijplijn waarmee u één of meerdere objecten op dezelfde manier behandelen heeft, wordt er algemene WMI-toegang kunt u sommige geavanceerde taken met weinig werk uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7ba05-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="7ba05-108">De volgende voorbeelden laten zien hoe u specifieke informatie verzamelen met behulp van `Get-CimInstance` op basis van een willekeurige computer.</span><span class="sxs-lookup"><span data-stu-id="7ba05-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="7ba05-109">We geven de **ComputerName** parameter met de waarde van de punt (**.**), die staat voor de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7ba05-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="7ba05-110">U kunt een naam of IP-adres dat is gekoppeld aan elke computer die u via WMI bereiken kan.</span><span class="sxs-lookup"><span data-stu-id="7ba05-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="7ba05-111">Als u wilt ophalen van informatie over de lokale computer, zou u de **ComputerName** parameter.</span><span class="sxs-lookup"><span data-stu-id="7ba05-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="7ba05-112">Bureaublad-instellingen weergeven</span><span class="sxs-lookup"><span data-stu-id="7ba05-112">Listing Desktop Settings</span></span>

<span data-ttu-id="7ba05-113">We beginnen met met een opdracht die u informatie over de bureaubladen op de lokale computer verzamelt.</span><span class="sxs-lookup"><span data-stu-id="7ba05-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="7ba05-114">Hiermee wordt informatie voor alle bureaubladen, ongeacht of deze in gebruik is of niet.</span><span class="sxs-lookup"><span data-stu-id="7ba05-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="7ba05-115">Informatie die wordt geretourneerd door een WMI-klassen kan worden zeer gedetailleerde en metagegevens over de WMI-klasse vaak bevatten.</span><span class="sxs-lookup"><span data-stu-id="7ba05-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="7ba05-116">Omdat de meeste van deze metagegevenseigenschappen namen die beginnen hebben met **Cim**, kunt u de eigenschappen die met behulp van filteren `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="7ba05-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="7ba05-117">Geef de **- ExcludeProperty** parameter met 'Cim \*' als de waarde.</span><span class="sxs-lookup"><span data-stu-id="7ba05-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="7ba05-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7ba05-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="7ba05-119">Als u wilt filteren de metagegevens, gebruikt u een pipeline-operator (|) voor het verzenden van de resultaten van de `Get-CimInstance` opdracht `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="7ba05-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="7ba05-120">BIOS-gegevens weergeven</span><span class="sxs-lookup"><span data-stu-id="7ba05-120">Listing BIOS Information</span></span>

<span data-ttu-id="7ba05-121">De WMI **Win32_BIOS** klasse retourneert vrij compact en volledige informatie over het systeem-BIOS op de lokale computer:</span><span class="sxs-lookup"><span data-stu-id="7ba05-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a><span data-ttu-id="7ba05-122">Processorgegevens van aanbieding</span><span class="sxs-lookup"><span data-stu-id="7ba05-122">Listing Processor Information</span></span>

<span data-ttu-id="7ba05-123">U kunt algemene processorgegevens ophalen met behulp van WMI **Win32_Processor** klasse, hoewel u wellicht wilt, de gegevens wilt filteren:</span><span class="sxs-lookup"><span data-stu-id="7ba05-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="7ba05-124">Voor een algemene beschrijving van de processor-familie, kunt u alleen retourneren de **SystemType** eigenschap:</span><span class="sxs-lookup"><span data-stu-id="7ba05-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="7ba05-125">Aanbieding computerfabrikant en Model</span><span class="sxs-lookup"><span data-stu-id="7ba05-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="7ba05-126">Computergegevens model is ook beschikbaar via **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="7ba05-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="7ba05-127">De standaarduitvoer weergegeven hoeft niet alle filters voor OEM-gegevens:</span><span class="sxs-lookup"><span data-stu-id="7ba05-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="7ba05-128">De uitvoer van opdrachten, zoals deze, die informatie rechtstreeks uit bepaalde hardware retourneert, is alleen nuttig als de gegevens die u hebt.</span><span class="sxs-lookup"><span data-stu-id="7ba05-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="7ba05-129">Sommige informatie niet juist is geconfigureerd door hardwarefabrikanten en kan daarom niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="7ba05-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="7ba05-130">Aanbieding Hotfixes geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="7ba05-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="7ba05-131">U kunt alle geïnstalleerde hotfixes weergeven met behulp van **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="7ba05-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="7ba05-132">Deze klasse wordt een lijst van hotfixes aan die er als uitzien volgt:</span><span class="sxs-lookup"><span data-stu-id="7ba05-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="7ba05-133">Voor meer beknopte uitvoer, kunt u bepaalde eigenschappen uitsluiten.</span><span class="sxs-lookup"><span data-stu-id="7ba05-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="7ba05-134">Hoewel u kunt de `Get-CimInstance`van **eigenschap** parameter kiest u alleen de **HotFixID**, als dit dus, retourneren meer informatie, omdat alle metagegevens wordt standaard weergegeven:</span><span class="sxs-lookup"><span data-stu-id="7ba05-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="7ba05-135">De aanvullende gegevens worden geretourneerd, omdat de eigenschap parameter in `Get-CimInstance` Hiermee beperkt u de eigenschappen die zijn geretourneerd door de WMI-klasse-instanties, niet op het object geretourneerd naar de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ba05-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="7ba05-136">Gebruik om te verminderen van de uitvoer, `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="7ba05-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="7ba05-137">Informatie over de versie van besturingssysteem vermelden</span><span class="sxs-lookup"><span data-stu-id="7ba05-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="7ba05-138">De **Win32_OperatingSystem** klasse-eigenschappen ook versie- en service pack.</span><span class="sxs-lookup"><span data-stu-id="7ba05-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="7ba05-139">U kunt alleen deze eigenschappen voor een versie-informatie van samenvatting expliciet selecteren **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="7ba05-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="7ba05-140">U kunt ook jokertekens met de `Select-Object`van **eigenschap** parameter.</span><span class="sxs-lookup"><span data-stu-id="7ba05-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="7ba05-141">Omdat alle eigenschappen die beginnen met een **bouwen** of **ServicePack** zijn belangrijk dat u hier, we dit kunnen korter naar de volgende notatie:</span><span class="sxs-lookup"><span data-stu-id="7ba05-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="7ba05-142">Lokale gebruikers en de eigenaar aanbieding</span><span class="sxs-lookup"><span data-stu-id="7ba05-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="7ba05-143">Lokale, algemene gebruikersgegevens: aantal gelicentieerde gebruikers, het huidige aantal gebruikers en de naam van de eigenaar, vindt u een selectie van **Win32_OperatingSystem** de klasse-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="7ba05-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="7ba05-144">U kunt de eigenschappen weer te geven, zoals dit expliciet selecteren:</span><span class="sxs-lookup"><span data-stu-id="7ba05-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="7ba05-145">Er is een meer beknopte versie met jokertekens:</span><span class="sxs-lookup"><span data-stu-id="7ba05-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="7ba05-146">Beschikbare ruimte op schijf ophalen</span><span class="sxs-lookup"><span data-stu-id="7ba05-146">Getting Available Disk Space</span></span>

<span data-ttu-id="7ba05-147">Als u wilt zien van de schijfruimte en de vrije ruimte voor lokale stations, kunt u de Win32_LogicalDisk WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="7ba05-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="7ba05-148">U wilt zien alleen exemplaren met een DriveType van 3: de waarde die WMI gebruikt voor vaste harde schijven.</span><span class="sxs-lookup"><span data-stu-id="7ba05-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="7ba05-149">Aanmeldingsgegevens voor de sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="7ba05-149">Getting Logon Session Information</span></span>

<span data-ttu-id="7ba05-150">U kunt algemene informatie over aanmeldingssessies die zijn gekoppeld aan gebruikers via de **Win32_LogonSession** WMI-klasse:</span><span class="sxs-lookup"><span data-stu-id="7ba05-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="7ba05-151">Ophalen van de gebruiker is aangemeld op een Computer</span><span class="sxs-lookup"><span data-stu-id="7ba05-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="7ba05-152">U kunt de gebruiker is aangemeld bij een bepaalde computer met behulp van Win32_ComputerSystem weergeven.</span><span class="sxs-lookup"><span data-stu-id="7ba05-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="7ba05-153">Met deze opdracht retourneert alleen de gebruiker aangemeld op het bureaublad system:</span><span class="sxs-lookup"><span data-stu-id="7ba05-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="7ba05-154">Lokale tijd ophalen van een Computer</span><span class="sxs-lookup"><span data-stu-id="7ba05-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="7ba05-155">U kunt de huidige lokale tijd op een specifieke computer ophalen met behulp van de **Win32_LocalTime** WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="7ba05-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="7ba05-156">Servicestatus weergeven</span><span class="sxs-lookup"><span data-stu-id="7ba05-156">Displaying Service Status</span></span>

<span data-ttu-id="7ba05-157">Als u wilt weergeven van de status van alle services op een specifieke computer, u lokaal kunt gebruiken de `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ba05-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="7ba05-158">Voor externe systemen, kunt u de **Win32_Service** WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="7ba05-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="7ba05-159">Als u ook `Select-Object` de resultaten te filteren **Status**, **naam**, en **DisplayName**, de indeling van de uitvoer is bijna identiek is aan die van `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="7ba05-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="7ba05-160">Als u wilt toestaan dat de volledige weergave van namen voor de services die af en toe met zeer lange namen, wilt u mogelijk gebruiken `Format-Table` met de **AutoSize** en **verpakken** parameters, het optimaliseren van de kolombreedte en lange namen om in te verpakken in plaats van het afkappen van toestaan:</span><span class="sxs-lookup"><span data-stu-id="7ba05-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
