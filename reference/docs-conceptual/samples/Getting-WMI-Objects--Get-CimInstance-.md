---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Ophalen van WMI-objecten CimInstance
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "77004692"
---
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="76f32-103">WMI-objecten ophalen (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="76f32-103">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="76f32-104">WMI-objecten ophalen (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="76f32-104">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="76f32-105">Windows Management Instrumentation (WMI) is een kern technologie voor Windows-systeem beheer, omdat een breed scala aan gegevens op een uniforme manier wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="76f32-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="76f32-106">Als gevolg van de mate waarin WMI mogelijk is, is de Power shell-cmdlet voor toegang tot WMI-objecten, `Get-CimInstance`, een van de handigste voor het uitvoeren van echte werk.</span><span class="sxs-lookup"><span data-stu-id="76f32-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="76f32-107">We bespreken hoe u de CimCmdlets kunt gebruiken voor toegang tot WMI-objecten en hoe u WMI-objecten kunt gebruiken om specifieke dingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="76f32-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="76f32-108">WMI-klassen weer geven</span><span class="sxs-lookup"><span data-stu-id="76f32-108">Listing WMI Classes</span></span>

<span data-ttu-id="76f32-109">Het eerste probleem dat de meeste WMI-gebruikers ondervindt, probeert te ontdekken wat er met WMI kan worden gedaan.</span><span class="sxs-lookup"><span data-stu-id="76f32-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="76f32-110">WMI-klassen beschrijven de resources die kunnen worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="76f32-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="76f32-111">Er zijn honderden WMI-klassen waarvan sommige van de eigenschappen tien tallen bevatten.</span><span class="sxs-lookup"><span data-stu-id="76f32-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="76f32-112">`Get-CimClass` lost dit probleem op door WMI detecteerbaar te maken.</span><span class="sxs-lookup"><span data-stu-id="76f32-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="76f32-113">U kunt een lijst weer geven van de WMI-klassen die beschikbaar zijn op de lokale computer door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="76f32-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

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

<span data-ttu-id="76f32-114">U kunt dezelfde gegevens ophalen van een externe computer met behulp van de para meter **ComputerName** , waarbij u een computer naam of IP-adres opgeeft:</span><span class="sxs-lookup"><span data-stu-id="76f32-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="76f32-115">De lijst met klassen die door externe computers wordt geretourneerd, kan variëren als gevolg van het specifieke besturings systeem dat op de computer wordt uitgevoerd en de specifieke WMI-uitbrei dingen die zijn toegevoegd door geïnstalleerde toepassingen.</span><span class="sxs-lookup"><span data-stu-id="76f32-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="76f32-116">Wanneer u CIM-cmdlets gebruikt om verbinding te maken met een externe computer, moet op de externe computer WMI worden uitgevoerd en moet het account dat u gebruikt zich in de lokale groep Administrators op de externe computer bevinden.</span><span class="sxs-lookup"><span data-stu-id="76f32-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="76f32-117">Power shell hoeft niet te zijn geïnstalleerd op het externe systeem.</span><span class="sxs-lookup"><span data-stu-id="76f32-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="76f32-118">Hierdoor kunt u besturings systemen beheren waarop Power shell niet wordt uitgevoerd, maar waarvoor WMI wel beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="76f32-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="76f32-119">Details van WMI-klasse weer geven</span><span class="sxs-lookup"><span data-stu-id="76f32-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="76f32-120">Als u de naam van een WMI-klasse al kent, kunt u deze gebruiken om informatie direct op te halen.</span><span class="sxs-lookup"><span data-stu-id="76f32-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="76f32-121">Zo is een van de WMI-klassen die meestal worden gebruikt voor het ophalen van informatie over een computer is **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="76f32-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="76f32-122">Hoewel alle para meters worden weer gegeven, kan de opdracht op een meer beknopte manier worden aangegeven.</span><span class="sxs-lookup"><span data-stu-id="76f32-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="76f32-123">De para meter **ComputerName** is niet nodig bij het maken van verbinding met het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="76f32-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="76f32-124">We laten u zien hoe u het meest algemene geval kunt demonstreren en u kunt u herinneren over de para meter.</span><span class="sxs-lookup"><span data-stu-id="76f32-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="76f32-125">De **naam ruimte** wordt standaard ingesteld op `root/CIMV2`en kan ook worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="76f32-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="76f32-126">Ten slotte kunt u met de meeste cmdlets de naam van algemene para meters weglaten.</span><span class="sxs-lookup"><span data-stu-id="76f32-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="76f32-127">Als er bij `Get-CimInstance`geen naam is opgegeven voor de eerste para meter, wordt deze door Power shell beschouwd als de **klasse** -para meter.</span><span class="sxs-lookup"><span data-stu-id="76f32-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="76f32-128">Dit betekent dat de laatste opdracht kan zijn uitgegeven door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="76f32-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="76f32-129">De klasse **Win32_OperatingSystem** heeft veel meer eigenschappen dan hier wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="76f32-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="76f32-130">U kunt Get-member gebruiken om alle eigenschappen te bekijken.</span><span class="sxs-lookup"><span data-stu-id="76f32-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="76f32-131">De eigenschappen van een WMI-klasse zijn automatisch beschikbaar, net als andere object eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="76f32-131">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="76f32-132">Niet-standaard eigenschappen weer geven met Format-cmdlets</span><span class="sxs-lookup"><span data-stu-id="76f32-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="76f32-133">Als u informatie wilt weer geven in de klasse **Win32_OperatingSystem** die niet standaard wordt weer gegeven, kunt u de gegevens met behulp van de **Format** -cmdlets bekijken.</span><span class="sxs-lookup"><span data-stu-id="76f32-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="76f32-134">Als u bijvoorbeeld beschik bare geheugen gegevens wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="76f32-134">For example, if you want to display available memory data, type:</span></span>

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
> <span data-ttu-id="76f32-135">Joker tekens werken met eigenschapnamen in `Format-Table`, zodat het laatste pijplijn element kan worden gereduceerd tot `Format-Table -Property Total*Memory*, Free*`</span><span class="sxs-lookup"><span data-stu-id="76f32-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="76f32-136">De geheugen gegevens kunnen beter leesbaar zijn als u deze als een lijst formatteert door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="76f32-136">The memory data might be more readable if you format it as a list by typing:</span></span>

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
