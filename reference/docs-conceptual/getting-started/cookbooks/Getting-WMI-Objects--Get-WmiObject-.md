---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Ophalen van WMI-objecten ophalen WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 279e656b4affd27450be71015a5d6bd21af9f7ad
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2018
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="eb962-103">Ophalen van WMI-objecten (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="eb962-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="eb962-104">Ophalen van WMI-objecten (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="eb962-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="eb962-105">Windows Management Instrumentation (WMI) is een belangrijke technologie voor Windows Systeembeheer omdat een breed scala aan gegevens op uniforme wijze worden getoond.</span><span class="sxs-lookup"><span data-stu-id="eb962-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="eb962-106">Vanwege hoeveel WMI mogelijk uit de Windows PowerShell-cmdlet voor toegang tot WMI-objecten maakt **Get-WmiObject**, is een van de meest geschikt voor echte werk.</span><span class="sxs-lookup"><span data-stu-id="eb962-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="eb962-107">We gaan bespreken Get-WmiObject gebruiken voor toegang tot WMI-objecten en vervolgens op het gebruik van WMI-objecten om specifieke dingen te doen.</span><span class="sxs-lookup"><span data-stu-id="eb962-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="eb962-108">Aanbieding WMI-klassen</span><span class="sxs-lookup"><span data-stu-id="eb962-108">Listing WMI Classes</span></span>

<span data-ttu-id="eb962-109">Het eerste probleem optreden van de meeste gebruikers van de WMI-probeert om erachter te komen wat u met WMI doen kunt.</span><span class="sxs-lookup"><span data-stu-id="eb962-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="eb962-110">WMI-klassen beschrijven de bronnen die kunnen worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="eb962-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="eb962-111">Er zijn honderden WMI-klassen, waarvan sommige tientallen eigenschappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="eb962-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="eb962-112">**Get-WmiObject** lost dit probleem doordat WMI kunnen worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="eb962-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="eb962-113">U kunt een lijst met de WMI-klassen beschikbaar op de lokale computer krijgen door te typen:</span><span class="sxs-lookup"><span data-stu-id="eb962-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="eb962-114">U kunt dezelfde gegevens vanaf een externe computer met behulp van de parameter ComputerName ophalen opgeven van een computernaam of IP-adres:</span><span class="sxs-lookup"><span data-stu-id="eb962-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="eb962-115">De aanbieding van de klasse die wordt geretourneerd door de externe computers kan vanwege het specifieke besturingssysteem dat wordt uitgevoerd op de computer en de bepaalde WMI-uitbreidingen toegevoegd door de geïnstalleerde toepassingen verschillen.</span><span class="sxs-lookup"><span data-stu-id="eb962-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="eb962-116">Wanneer u de Get-WmiObject verbinding maken met een externe computer, op de externe computer WMI moet worden uitgevoerd en onder de standaardconfiguratie moet het account dat u gebruikt in de lokale beheerdersgroep op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="eb962-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="eb962-117">Het externe systeem hoeft niet te hebben van Windows PowerShell is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="eb962-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="eb962-118">Hiermee kunt u voor het beheren van besturingssystemen die niet worden uitgevoerd in Windows PowerShell, maar hoeven WMI beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="eb962-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="eb962-119">U kunt zelfs de ComputerName opnemen wanneer u verbinding met het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="eb962-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="eb962-120">U kunt de naam van de lokale computer, het IP-adres (of de loopback-adres 127.0.0.1), of de WMI-stijl '.' als de naam van de computer.</span><span class="sxs-lookup"><span data-stu-id="eb962-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="eb962-121">Als u Windows PowerShell op een computer met de naam Admin01 met IP-adres 192.168.1.90 uitvoert, wordt de volgende opdrachten alle geretourneerd met de WMI-klasse aanbieding voor die computer:</span><span class="sxs-lookup"><span data-stu-id="eb962-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="eb962-122">Get-WmiObject maakt standaard gebruik van de naamruimte root/cimv2.</span><span class="sxs-lookup"><span data-stu-id="eb962-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="eb962-123">Als u een andere WMI-naamruimte opgeven wilt, gebruikt u de **Namespace** parameter en het bijbehorende naamruimtepad opgeven:</span><span class="sxs-lookup"><span data-stu-id="eb962-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="eb962-124">Met de WMI-klasse Details</span><span class="sxs-lookup"><span data-stu-id="eb962-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="eb962-125">Als u de naam van een WMI-klasse al weet, kunt u deze informatie onmiddellijk ophalen.</span><span class="sxs-lookup"><span data-stu-id="eb962-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="eb962-126">Bijvoorbeeld, een van de WMI-klassen die meestal wordt gebruikt voor het ophalen van informatie over een computer is **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="eb962-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="eb962-127">Hoewel we alle parameters worden weergegeven, kan de opdracht kan worden uitgedrukt in een meer beknopte manier.</span><span class="sxs-lookup"><span data-stu-id="eb962-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="eb962-128">De **ComputerName** parameter is niet nodig bij het verbinden met het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="eb962-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="eb962-129">We blijkt dat het meest algemene geval demonstreren en herinneren van de parameter.</span><span class="sxs-lookup"><span data-stu-id="eb962-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="eb962-130">De **Namespace** root/cimv2 standaard en kan ook worden weggelaten.</span><span class="sxs-lookup"><span data-stu-id="eb962-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="eb962-131">Ten slotte kunt de meeste cmdlets u de naam van de algemene parameters weglaten.</span><span class="sxs-lookup"><span data-stu-id="eb962-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="eb962-132">Met Get-WmiObject, als er geen naam is opgegeven voor de eerste parameter, Windows PowerShell wordt deze behandeld als de **klasse** parameter.</span><span class="sxs-lookup"><span data-stu-id="eb962-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="eb962-133">Dit betekent dat de laatste opdracht kan worden uitgegeven door te typen:</span><span class="sxs-lookup"><span data-stu-id="eb962-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="eb962-134">De **Win32_OperatingSystem** klasse heeft nog veel meer eigenschappen dan de hier weergegeven.</span><span class="sxs-lookup"><span data-stu-id="eb962-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="eb962-135">De eigenschappen kunt u Get-lid.</span><span class="sxs-lookup"><span data-stu-id="eb962-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="eb962-136">De eigenschappen van een WMI-klasse zijn automatisch beschikbaar, zoals andere eigenschappen van het object:</span><span class="sxs-lookup"><span data-stu-id="eb962-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="eb962-137">Eigenschappen van de niet-standaard met indeling Cmdlets weer te geven</span><span class="sxs-lookup"><span data-stu-id="eb962-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="eb962-138">Als u wilt dat de gegevens in de **Win32_OperatingSystem** klasse is niet standaard weergegeven, kunt u deze weergeven doen met behulp van de **indeling** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="eb962-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="eb962-139">Bijvoorbeeld, als u gegevens beschikbaar geheugen weergeven wilt, typt u:</span><span class="sxs-lookup"><span data-stu-id="eb962-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="eb962-140">Jokertekens werken met namen van eigenschappen in **Format-Table**, zodat de laatste pipeline-element kan worden teruggebracht naar `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="eb962-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="eb962-141">De geheugengegevens is mogelijk beter leesbare indeling als een lijst door te typen:</span><span class="sxs-lookup"><span data-stu-id="eb962-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
