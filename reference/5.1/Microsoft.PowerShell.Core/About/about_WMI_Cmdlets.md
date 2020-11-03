---
description: Bevat achtergrond informatie over Windows Management Instrumentation (WMI) en Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI_Cmdlets
ms.openlocfilehash: c2099c005cedf64e9621d66d6757419320c9b43e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252727"
---
# <a name="about-wmi-cmdlets"></a><span data-ttu-id="9f3ea-104">Over WMI-cmdlets</span><span class="sxs-lookup"><span data-stu-id="9f3ea-104">About WMI Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="9f3ea-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9f3ea-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="9f3ea-106">Bevat achtergrond informatie over Windows Management Instrumentation (WMI) en Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-106">Provides background information about Windows Management Instrumentation (WMI) and Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="9f3ea-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9f3ea-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9f3ea-108">In dit onderwerp vindt u informatie over de WMI-technologie, de WMI-cmdlets voor Windows Power shell, op WMI gebaseerde externe toegang, WMI-accelerators en WMI-probleem oplossing.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-108">This topic provides information about WMI technology, the WMI cmdlets for Windows PowerShell, WMI-based remoting, WMI accelerators, and WMI troubleshooting.</span></span> <span data-ttu-id="9f3ea-109">Dit onderwerp bevat ook koppelingen naar meer informatie over WMI.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-109">This topic also provides links to more information about WMI.</span></span>

### <a name="about-wmi"></a><span data-ttu-id="9f3ea-110">OVER WMI</span><span class="sxs-lookup"><span data-stu-id="9f3ea-110">ABOUT WMI</span></span>

<span data-ttu-id="9f3ea-111">Windows Management Instrumentation (WMI) is de Microsoft-implementatie van Web-Based Enterprise Management (WBEM), een industrie-initiatief om een standaardtechnologie te ontwikkelen voor het werken met beheerinformatie in een bedrijfsomgeving.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-111">Windows Management Instrumentation (WMI) is the Microsoft implementation of Web-Based Enterprise Management (WBEM), which is an industry initiative to develop a standard technology for accessing management information in an enterprise environment.</span></span> <span data-ttu-id="9f3ea-112">WMI maakt gebruik van het industrie-initiatief Common Information Model (CIM) om systemen, toepassingen, netwerken, apparaten en andere beheerde onderdelen te representeren.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-112">WMI uses the Common Information Model (CIM) industry standard to represent systems, applications, networks, devices, and other managed components.</span></span> <span data-ttu-id="9f3ea-113">CIM is ontwikkeld en wordt onderhouden door Distributed Management Task Force (DMTF).</span><span class="sxs-lookup"><span data-stu-id="9f3ea-113">CIM is developed and maintained by the Distributed Management Task Force (DMTF).</span></span> <span data-ttu-id="9f3ea-114">U kunt WMI gebruiken voor het beheren van lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-114">You can use WMI to manage both local and remote computers.</span></span> <span data-ttu-id="9f3ea-115">U kunt WMI bijvoorbeeld gebruiken om het volgende te doen:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-115">For example, you can use WMI to do the following:</span></span>

- <span data-ttu-id="9f3ea-116">Start een proces op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-116">Start a process on a remote computer.</span></span>
- <span data-ttu-id="9f3ea-117">Een computer op afstand opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-117">Restart a computer remotely.</span></span>
- <span data-ttu-id="9f3ea-118">Een lijst ophalen van de toepassingen die op een lokale of externe computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-118">Get a list of the applications that are installed on a local or remote computer.</span></span>
- <span data-ttu-id="9f3ea-119">Een query uitvoeren op de Windows-gebeurtenis logboeken op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-119">Query the Windows event logs on a local or remote computer.</span></span>

### <a name="the-wmi-cmdlets-for-windows-powershell"></a><span data-ttu-id="9f3ea-120">DE WMI-CMDLETS VOOR WINDOWS POWER SHELL</span><span class="sxs-lookup"><span data-stu-id="9f3ea-120">THE WMI CMDLETS FOR WINDOWS POWERSHELL</span></span>

<span data-ttu-id="9f3ea-121">Windows Power shell implementeert WMI-functionaliteit via een set cmdlets die standaard beschikbaar zijn in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-121">Windows PowerShell implements WMI functionality through a set of cmdlets that are available in Windows PowerShell by default.</span></span> <span data-ttu-id="9f3ea-122">U kunt deze cmdlets gebruiken voor het volt ooien van de end-to-end taken die nodig zijn voor het beheren van lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-122">You can use these cmdlets to complete the end-to-end tasks necessary to manage local and remote computers.</span></span>

<span data-ttu-id="9f3ea-123">De volgende WMI-cmdlets zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-123">The following WMI cmdlets are included.</span></span>

|<span data-ttu-id="9f3ea-124">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f3ea-124">Cmdlet</span></span>           |<span data-ttu-id="9f3ea-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f3ea-125">Description</span></span>                                   |
|-----------------|----------------------------------------------|
|<span data-ttu-id="9f3ea-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="9f3ea-126">Get-WmiObject</span></span>    |<span data-ttu-id="9f3ea-127">Hiermee worden instanties van WMI-klassen of-gegevens opgehaald</span><span class="sxs-lookup"><span data-stu-id="9f3ea-127">Gets instances of WMI classes or information</span></span>  |
|                 |<span data-ttu-id="9f3ea-128">over de beschik bare klassen.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-128">about the available classes.</span></span>                  |
|<span data-ttu-id="9f3ea-129">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="9f3ea-129">Invoke-WmiMethod</span></span> |<span data-ttu-id="9f3ea-130">WMI-methoden aanroept.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-130">Calls WMI methods.</span></span>                            |
|<span data-ttu-id="9f3ea-131">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="9f3ea-131">Register-WmiEvent</span></span>|<span data-ttu-id="9f3ea-132">Abonneren op een WMI-gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-132">Subscribes to a WMI event.</span></span>                    |
|<span data-ttu-id="9f3ea-133">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="9f3ea-133">Remove-WmiObject</span></span> |<span data-ttu-id="9f3ea-134">WMI-klassen en-instanties worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-134">Deletes WMI classes and instances.</span></span>            |
|<span data-ttu-id="9f3ea-135">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="9f3ea-135">Set-WmiInstance</span></span>  |<span data-ttu-id="9f3ea-136">Hiermee worden instanties van WMI-klassen gemaakt of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-136">Creates or modifies instances of WMI classes.</span></span> |

### <a name="sample-commands"></a><span data-ttu-id="9f3ea-137">VOORBEELD OPDRACHTEN</span><span class="sxs-lookup"><span data-stu-id="9f3ea-137">SAMPLE COMMANDS</span></span>
<span data-ttu-id="9f3ea-138">Met de volgende opdracht wordt de BIOS-informatie voor de lokale computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-138">The following command displays the BIOS information for the local computer.</span></span>

```powershell
C:\PS> get-wmiobject win32_bios | format-list *
```

<span data-ttu-id="9f3ea-139">De volgende opdracht geeft informatie weer over de WinRM-service voor drie externe computers.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-139">The following command displays information about the WinRM service for three remote computers.</span></span>

```powershell
$wql = "select * from win32_service where name='WinRM'"
get-wmiobject -query $wql -computername server01, server01, server03
```

<span data-ttu-id="9f3ea-140">Met de volgende complexe opdracht worden alle exemplaren van een programma afgesloten.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-140">The following more complex command exits all instances of a program.</span></span>

```powershell
C:\PS> notepad.exe
C:\PS> $wql = "select * from win32_process where name='notepad.exe'"
C:\PS> $np = get-wmiobject -query $wql
C:\PS> $np | remove-wmiobject
```

### <a name="wmi-based-remoting"></a><span data-ttu-id="9f3ea-141">EXTERNE TOEGANG OP BASIS VAN WMI</span><span class="sxs-lookup"><span data-stu-id="9f3ea-141">WMI-BASED REMOTING</span></span>

<span data-ttu-id="9f3ea-142">Hoewel de mogelijkheid om een lokaal systeem te beheren via WMI nuttig is, is dit de mogelijkheden voor externe toegang die WMI een krachtig beheer programma maken.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-142">While the ability to manage a local system through WMI is useful, it is the remoting capabilities that make WMI a powerful administrative tool.</span></span> <span data-ttu-id="9f3ea-143">WMI maakt gebruik van gedistribueerde Component Object Model (DCOM) van micro soft voor het maken van verbinding met en het beheren van systemen.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-143">WMI uses Microsoft's Distributed Component Object Model (DCOM) to connect to and manage systems.</span></span> <span data-ttu-id="9f3ea-144">Mogelijk moet u sommige systemen configureren om DCOM-verbindingen toe te staan.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-144">You might have to configure some systems to allow DCOM connections.</span></span>
<span data-ttu-id="9f3ea-145">Firewall instellingen en vergrendelde DCOM-machtigingen kunnen de mogelijkheid van WMI om systemen op afstand te beheren blok keren.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-145">Firewall settings and locked-down DCOM permissions can block WMI's ability to remotely manage systems.</span></span>

### <a name="wmi-type-accelerators"></a><span data-ttu-id="9f3ea-146">WMI-TYPE ACCELERATORS</span><span class="sxs-lookup"><span data-stu-id="9f3ea-146">WMI TYPE ACCELERATORS</span></span>

<span data-ttu-id="9f3ea-147">Windows Power shell bevat WMI-type Accelerators.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-147">Windows PowerShell includes WMI type accelerators.</span></span> <span data-ttu-id="9f3ea-148">Deze WMI-type Accelerators (snelkoppelingen) bieden meer directe toegang tot WMI-objecten dan een niet-type versnelling zou toestaan.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-148">These WMI type accelerators (shortcuts) allow more direct access to a WMI objects than a non-type accelerator approach would allow.</span></span>

<span data-ttu-id="9f3ea-149">De volgende typen accelerators worden ondersteund met WMI:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-149">The following type accelerators are supported with WMI:</span></span>

<span data-ttu-id="9f3ea-150">[WMISEARCHER]-een snelkoppeling voor het zoeken naar WMI-objecten.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-150">[WMISEARCHER] - A shortcut for searching for WMI objects.</span></span>

<span data-ttu-id="9f3ea-151">[WMICLASS]: een snelkoppeling voor het openen van de statische eigenschappen en methoden van een klasse.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-151">[WMICLASS] - A shortcut for accessing the static properties and methods of a class.</span></span>

<span data-ttu-id="9f3ea-152">[WMI]: een snelkoppeling voor het ophalen van één exemplaar van een klasse.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-152">[WMI] - A shortcut for getting a single instance of a class.</span></span>

<span data-ttu-id="9f3ea-153">[WMISEARCHER] is een type Accelerator voor een ManagementObjectSearcher.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-153">[WMISEARCHER] is a type accelerator for a ManagementObjectSearcher.</span></span> <span data-ttu-id="9f3ea-154">Dit kan een teken reeks constructor zijn om een zoek programma te maken waarin u vervolgens een GET () op kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-154">It can take a string constructor to create a searcher that you can then do a GET() on.</span></span>

<span data-ttu-id="9f3ea-155">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-155">For example:</span></span>

```powershell
PS> $s = [WmiSearcher]'Select * from Win32_Process where Handlecount > 1000'
PS> $s.Get() |sort handlecount |ft handlecount,__path,name -auto

count  __PATH                                              name
-----  ------                                              ----
1105   \\SERVER01\root\cimv2:Win32_Process.Handle="3724"   PowerShell...
1132   \\SERVER01\root\cimv2:Win32_Process.Handle="1388"   winlogon.exe
1495   \\SERVER01\root\cimv2:Win32_Process.Handle="2852"   iexplore.exe
1699   \\SERVER01\root\cimv2:Win32_Process.Handle="1204"   OUTLOOK.EXE
1719   \\SERVER01\root\cimv2:Win32_Process.Handle="1912"   iexplore.exe
2579   \\SERVER01\root\cimv2:Win32_Process.Handle="1768"   svchost.exe
```

<span data-ttu-id="9f3ea-156">[WMICLASS] is een type Accelerator voor ManagementClass.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-156">[WMICLASS] is a type accelerator for ManagementClass.</span></span> <span data-ttu-id="9f3ea-157">Dit heeft een teken reeks constructor die een lokaal of absoluut WMI-pad naar een WMI-klasse gebruikt en een object retourneert dat is gekoppeld aan deze klasse.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-157">This has a string constructor that takes a local or absolute WMI path to a WMI class and returns an object that is bound to that class.</span></span>

<span data-ttu-id="9f3ea-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-158">For example:</span></span>

```powershell
PS> $c = [WMICLASS]"root\cimv2:WIn32_Process"
PS> $c |fl *
Name             : Win32_Process
__GENUS          : 1
__CLASS          : Win32_Process
__SUPERCLASS     : CIM_Process
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Process
__PROPERTY_COUNT : 45
__DERIVATION     : {CIM_Process, CIM_LogicalElement,
                   CIM_ManagedSystemElement}
__SERVER         : SERVER01
__NAMESPACE      : ROOT\cimv2
__PATH           : \\SERVER01\ROOT\cimv2:Win32_Process
```

<span data-ttu-id="9f3ea-159">[WMI] is een type Accelerator voor ManagementObject.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-159">[WMI] is a type accelerator for ManagementObject.</span></span> <span data-ttu-id="9f3ea-160">Dit heeft een teken reeks constructor die een lokaal of absoluut WMI-pad naar een WMI-exemplaar gebruikt en een object retourneert dat is gekoppeld aan dat exemplaar.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-160">This has a string constructor that takes a local or absolute WMI path to a WMI instance and returns an object that is bound to that instance.</span></span>

<span data-ttu-id="9f3ea-161">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-161">For example:</span></span>

```powershell
PS> $p = [WMI]'\\SERVER01\root\cimv2:Win32_Process.Handle="1204"'
PS> $p.Name
OUTLOOK.EXE
```

### <a name="wmi-troubleshooting"></a><span data-ttu-id="9f3ea-162">WMI-PROBLEMEN OPLOSSEN</span><span class="sxs-lookup"><span data-stu-id="9f3ea-162">WMI TROUBLESHOOTING</span></span>

<span data-ttu-id="9f3ea-163">De volgende problemen zijn de meest voorkomende problemen die zich kunnen voordoen wanneer u verbinding probeert te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-163">The following problems are the most common problems that might occur when you try to connect to a remote computer.</span></span>

<span data-ttu-id="9f3ea-164">Probleem 1: de externe computer is niet online.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-164">Problem 1: The remote computer is not online.</span></span>

<span data-ttu-id="9f3ea-165">Als een computer offline is, kunt u er geen verbinding mee maken met behulp van WMI.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-165">If a computer is offline, you will not be able to connect to it by using WMI.</span></span>
<span data-ttu-id="9f3ea-166">U ontvangt mogelijk het volgende foutbericht:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-166">You may receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

<span data-ttu-id="9f3ea-167">Als dit fout bericht wordt weer gegeven, controleert u of de computer online is.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-167">If you receive this error message, verify that the computer is online.</span></span> <span data-ttu-id="9f3ea-168">Probeer de externe computer te pingen.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-168">Try to ping the remote computer.</span></span>

<span data-ttu-id="9f3ea-169">Probleem 2: u hebt geen lokale Administrator rechten op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-169">Problem 2: You do not have local administrator rights on the remote computer.</span></span>

<span data-ttu-id="9f3ea-170">Als u WMI op afstand wilt gebruiken, moet u over lokale beheerders rechten beschikken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-170">To use WMI remotely, you must have local administrator rights on the remote computer.</span></span> <span data-ttu-id="9f3ea-171">Als u dit niet doet, wordt de toegang tot die computer geweigerd.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-171">If you do not, access to that computer will be denied.</span></span>

<span data-ttu-id="9f3ea-172">Naam ruimte beveiliging controleren:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-172">To verify namespace security:</span></span>

1. <span data-ttu-id="9f3ea-173">Klik op Start, klik met de rechter muisknop op mijn computer en klik vervolgens op beheren.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-173">Click Start, right-click My Computer, and then click Manage.</span></span>
2. <span data-ttu-id="9f3ea-174">In computer beheer vouwt u services en toepassingen uit, klikt u met de rechter muisknop op WMI-beheer en klikt u vervolgens op Eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-174">In Computer Management, expand Services and Applications, right-click WMI Control, and then click Properties.</span></span>
3. <span data-ttu-id="9f3ea-175">Klik in het dialoog venster WMI Control-eigenschappen op het tabblad Beveiliging.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-175">In the WMI Control Properties dialog box, click  the Security tab.</span></span>

<span data-ttu-id="9f3ea-176">Probleem 3: de toegang tot de externe computer wordt geblokkeerd door een firewall.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-176">Problem 3: A firewall is blocking access to the remote computer.</span></span>

<span data-ttu-id="9f3ea-177">WMI maakt gebruik van de protocollen DCOM (Distributed COM) en RPC (Remote Procedure Call) om via het netwerk te passeren.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-177">WMI uses the DCOM (Distributed COM) and RPC (Remote Procedure Call) protocols to traverse the network.</span></span> <span data-ttu-id="9f3ea-178">Standaard blok keren firewalls DCOM en RPC-verkeer.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-178">By default, many firewalls block DCOM and RPC traffic.</span></span> <span data-ttu-id="9f3ea-179">Als uw firewall deze protocollen blokkeert, mislukt de verbinding.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-179">If your firewall is blocking these protocols, your connection will fail.</span></span> <span data-ttu-id="9f3ea-180">Windows Firewall in micro soft Windows XP Service Pack 2 is bijvoorbeeld zodanig geconfigureerd dat alle ongevraagde netwerk verkeer, waaronder DCOM en WMI, automatisch wordt geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="9f3ea-180">For example, Windows Firewall in Microsoft Windows XP Service Pack 2 is configured to automatically block all unsolicited network traffic, including DCOM and WMI.</span></span> <span data-ttu-id="9f3ea-181">In de standaard configuratie wijst Windows Firewall een binnenkomende WMI-aanvraag af en wordt het volgende fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="9f3ea-181">In its default configuration, Windows Firewall rejects an incoming WMI request, and you receive the following error message:</span></span>

```
Remote server machine does not exist or is unavailable
```

## <a name="see-also"></a><span data-ttu-id="9f3ea-182">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="9f3ea-182">SEE ALSO</span></span>

[<span data-ttu-id="9f3ea-183">Over WMI</span><span class="sxs-lookup"><span data-stu-id="9f3ea-183">About WMI</span></span>](/windows/win32/wmisdk/about-wmi)

[<span data-ttu-id="9f3ea-184">WMI-problemen oplossen</span><span class="sxs-lookup"><span data-stu-id="9f3ea-184">WMI Troubleshooting</span></span>](/windows/win32/wmisdk/wmi-troubleshooting)

[<span data-ttu-id="9f3ea-185">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="9f3ea-185">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="9f3ea-186">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="9f3ea-186">Invoke-WmiMethod</span></span>](xref:Microsoft.PowerShell.Management.Invoke-WmiMethod)

[<span data-ttu-id="9f3ea-187">REGI ster-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="9f3ea-187">Register-WmiEvent</span></span>](xref:Microsoft.PowerShell.Management.Register-WmiEvent)

[<span data-ttu-id="9f3ea-188">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="9f3ea-188">Remove-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Remove-WmiObject)

[<span data-ttu-id="9f3ea-189">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="9f3ea-189">Set-WmiInstance</span></span>](xref:Microsoft.PowerShell.Management.Set-WmiInstance)
