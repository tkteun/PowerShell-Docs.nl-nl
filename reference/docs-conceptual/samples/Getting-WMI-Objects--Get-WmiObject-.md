---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Ophalen van WMI-objecten WmiObject
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030212"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="50322-103">WMI-objecten ophalen (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="50322-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="50322-104">WMI-objecten ophalen (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="50322-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="50322-105">Windows Management Instrumentation (WMI) is een kern technologie voor Windows-systeem beheer, omdat een breed scala aan gegevens op een uniforme manier wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="50322-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="50322-106">Als gevolg van de mate waarin WMI mogelijk is, is de Windows Power shell-cmdlet voor toegang tot WMI-objecten, **Get-WmiObject**, een van de handigste voor het uitvoeren van echte werk.</span><span class="sxs-lookup"><span data-stu-id="50322-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="50322-107">We bespreken hoe u Get-WmiObject kunt gebruiken voor toegang tot WMI-objecten en hoe u WMI-objecten kunt gebruiken om specifieke dingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="50322-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="50322-108">WMI-klassen weer geven</span><span class="sxs-lookup"><span data-stu-id="50322-108">Listing WMI Classes</span></span>

<span data-ttu-id="50322-109">Het eerste probleem dat de meeste WMI-gebruikers ondervindt, probeert te ontdekken wat er met WMI kan worden gedaan.</span><span class="sxs-lookup"><span data-stu-id="50322-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="50322-110">WMI-klassen beschrijven de resources die kunnen worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="50322-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="50322-111">Er zijn honderden WMI-klassen waarvan sommige van de eigenschappen tien tallen bevatten.</span><span class="sxs-lookup"><span data-stu-id="50322-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="50322-112">**Get-WmiObject** lost dit probleem op door WMI detecteerbaar te maken.</span><span class="sxs-lookup"><span data-stu-id="50322-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="50322-113">U kunt een lijst weer geven van de WMI-klassen die beschikbaar zijn op de lokale computer door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="50322-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="50322-114">U kunt dezelfde gegevens ophalen van een externe computer met behulp van de para meter ComputerName, waarbij u een computer naam of IP-adres opgeeft:</span><span class="sxs-lookup"><span data-stu-id="50322-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="50322-115">De lijst met klassen die door externe computers wordt geretourneerd, kan variëren als gevolg van het specifieke besturings systeem dat op de computer wordt uitgevoerd en de specifieke WMI-uitbrei dingen die zijn toegevoegd door geïnstalleerde toepassingen.</span><span class="sxs-lookup"><span data-stu-id="50322-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="50322-116">Wanneer u Get-WmiObject gebruikt om verbinding te maken met een externe computer, moet op de externe computer WMI worden uitgevoerd en moet het account dat u gebruikt, zich in de lokale groep Administrators op de externe computer bevinden, onder de standaard configuratie.</span><span class="sxs-lookup"><span data-stu-id="50322-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="50322-117">Windows Power shell hoeft niet te zijn geïnstalleerd op het externe systeem.</span><span class="sxs-lookup"><span data-stu-id="50322-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="50322-118">Hierdoor kunt u besturings systemen beheren waarop geen Windows Power shell wordt uitgevoerd, maar die WMI wel beschikbaar heeft.</span><span class="sxs-lookup"><span data-stu-id="50322-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="50322-119">U kunt zelfs de computer naam toevoegen wanneer u verbinding maakt met het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="50322-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="50322-120">U kunt de naam van de lokale computer, het bijbehorende IP-adres (of het loop back-adres 127.0.0.1) of de WMI-stijl '. ' gebruiken als computer naam.</span><span class="sxs-lookup"><span data-stu-id="50322-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="50322-121">Als u Windows Power shell uitvoert op een computer met de naam Admin01 met IP-adres 192.168.1.90, worden met de volgende opdrachten alle vermeldingen van de WMI-klasse voor die computer geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="50322-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="50322-122">Get-WmiObject maakt standaard gebruik van de naam ruimte root/cimv2.</span><span class="sxs-lookup"><span data-stu-id="50322-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="50322-123">Als u een andere WMI-naam ruimte wilt opgeven, gebruikt u de para meter **naam ruimte** en geeft u het bijbehorende pad naar de naam ruimte op:</span><span class="sxs-lookup"><span data-stu-id="50322-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="50322-124">Details van WMI-klasse weer geven</span><span class="sxs-lookup"><span data-stu-id="50322-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="50322-125">Als u de naam van een WMI-klasse al kent, kunt u deze gebruiken om informatie direct op te halen.</span><span class="sxs-lookup"><span data-stu-id="50322-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="50322-126">Zo is een van de WMI-klassen die meestal worden gebruikt voor het ophalen van informatie over een computer is **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="50322-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="50322-127">Hoewel alle para meters worden weer gegeven, kan de opdracht op een meer beknopte manier worden aangegeven.</span><span class="sxs-lookup"><span data-stu-id="50322-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="50322-128">De para meter **ComputerName** is niet nodig bij het maken van verbinding met het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="50322-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="50322-129">We laten u zien hoe u het meest algemene geval kunt demonstreren en u kunt u herinneren over de para meter.</span><span class="sxs-lookup"><span data-stu-id="50322-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="50322-130">De **naam ruimte** wordt standaard ingesteld op root-cimv2 en kan ook worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="50322-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="50322-131">Ten slotte kunt u met de meeste cmdlets de naam van algemene para meters weglaten.</span><span class="sxs-lookup"><span data-stu-id="50322-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="50322-132">Als er bij Get-WmiObject geen naam is opgegeven voor de eerste para meter, wordt deze door Windows Power shell beschouwd als de **klasse** para meter.</span><span class="sxs-lookup"><span data-stu-id="50322-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="50322-133">Dit betekent dat de laatste opdracht kan zijn uitgegeven door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="50322-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="50322-134">De klasse **Win32_OperatingSystem** heeft veel meer eigenschappen dan hier wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="50322-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="50322-135">U kunt Get-member gebruiken om alle eigenschappen te bekijken.</span><span class="sxs-lookup"><span data-stu-id="50322-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="50322-136">De eigenschappen van een WMI-klasse zijn automatisch beschikbaar, net als andere object eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="50322-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="50322-137">Niet-standaard eigenschappen weer geven met Format-cmdlets</span><span class="sxs-lookup"><span data-stu-id="50322-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="50322-138">Als u informatie wilt weer geven in de klasse **Win32_OperatingSystem** die niet standaard wordt weer gegeven, kunt u de gegevens met behulp van de **Format** -cmdlets bekijken.</span><span class="sxs-lookup"><span data-stu-id="50322-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="50322-139">Als u bijvoorbeeld beschik bare geheugen gegevens wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="50322-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="50322-140">Joker tekens werken met eigenschapnamen in **indelings tabel**, zodat het laatste pijplijn element kan worden beperkt tot `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="50322-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="50322-141">De geheugen gegevens kunnen beter leesbaar zijn als u deze als een lijst formatteert door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="50322-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
