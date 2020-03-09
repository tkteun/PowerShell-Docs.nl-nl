---
title: Compatibiliteit met Power shell 7-module
ms.date: 02/03/2020
ms.openlocfilehash: 1f7a2f4fa04e07b8f56635d0a39e580924ae0134
ms.sourcegitcommit: d34841a44742af1123da007fefbdc24a2f1762dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/07/2020
ms.locfileid: "78926197"
---
# <a name="powershell-7-module-compatibility"></a><span data-ttu-id="de917-102">Compatibiliteit met Power shell 7-module</span><span class="sxs-lookup"><span data-stu-id="de917-102">PowerShell 7 module compatibility</span></span>

<span data-ttu-id="de917-103">Dit artikel bevat een lijst met Power shell-modules die door micro soft zijn gepubliceerd en die beheer en ondersteuning bieden voor diverse micro soft-producten en-services.</span><span class="sxs-lookup"><span data-stu-id="de917-103">This article contains a list of PowerShell modules published by Microsoft that provide management and support for various Microsoft products and services.</span></span> <span data-ttu-id="de917-104">Deze modules zijn bijgewerkt voor gebruik in combi natie met Power shell 7 of getest op compatibiliteit met Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="de917-104">These modules have been updated to work natively with PowerShell 7 or tested for compatibility with PowerShell 7.</span></span>

<span data-ttu-id="de917-105">Deze lijst wordt bijgewerkt met nieuwe informatie, omdat er meer modules worden geïdentificeerd en getest.</span><span class="sxs-lookup"><span data-stu-id="de917-105">This list will be updated with new information as more modules are identified and tested.</span></span> <span data-ttu-id="de917-106">Als u informatie hebt om te delen of problemen met specifieke modules op te lossen, kunt u een probleem melden in de [WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility) -opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="de917-106">If you have information to share or issues with specific modules, please file an issue in the [WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility) repository.</span></span>

## <a name="windows-management-modules"></a><span data-ttu-id="de917-107">Windows-beheer modules</span><span class="sxs-lookup"><span data-stu-id="de917-107">Windows management modules</span></span>

<span data-ttu-id="de917-108">De Windows-beheer modules worden op verschillende manieren geïnstalleerd, afhankelijk van het type Windows en de wijze waarop de module is verpakt.</span><span class="sxs-lookup"><span data-stu-id="de917-108">The Windows management modules are installed in different ways depending on the type of Windows and how the module was packaged.</span></span> <span data-ttu-id="de917-109">Deze modules moeten worden geïnstalleerd vanuit een Power shell-sessie met verhoogde bevoegdheid met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="de917-109">These modules must be installed from an elevate PowerShell session using the **Run as administrator** option.</span></span>

<span data-ttu-id="de917-110">Gebruik op Windows Server de functie naam met de [install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) om de module te installeren.</span><span class="sxs-lookup"><span data-stu-id="de917-110">On Windows Server, use the feature name with the [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) to install the module.</span></span> <span data-ttu-id="de917-111">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="de917-111">For example:</span></span>

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

<span data-ttu-id="de917-112">In Windows 10 moet u een van deze cmdlets gebruiken, afhankelijk van het pakket type:</span><span class="sxs-lookup"><span data-stu-id="de917-112">On Windows 10, you have to use one of these cmdlets depending the package type:</span></span>
- [<span data-ttu-id="de917-113">Enable-WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="de917-113">Enable-WindowsOptionalFeature</span></span>](/powershell/module/dism/enable-windowsoptionalfeature)
- [<span data-ttu-id="de917-114">Add-WindowsCapability</span><span class="sxs-lookup"><span data-stu-id="de917-114">Add-WindowsCapability</span></span>](/powershell/module/dism/add-windowscapability)

<span data-ttu-id="de917-115">Voor modules die worden geïnstalleerd als Windows-onderdelen:</span><span class="sxs-lookup"><span data-stu-id="de917-115">For modules that install as Windows Features:</span></span>

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName FooFeatureName
```

<span data-ttu-id="de917-116">Voor modules die als Windows-mogelijkheden worden geïnstalleerd, moet u `~~~~0.0.1.0` toevoegen aan het einde van de pakket naam.</span><span class="sxs-lookup"><span data-stu-id="de917-116">For modules that install as Windows Capabilities, you have to append `~~~~0.0.1.0` to the end of the package name.</span></span> <span data-ttu-id="de917-117">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="de917-117">For example:</span></span>

```powershell
Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
```

### <a name="activedirectory"></a><span data-ttu-id="de917-118">ActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="de917-118">ActiveDirectory</span></span>

<span data-ttu-id="de917-119">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-119">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-120">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-120">Compatible with:</span></span>

- <span data-ttu-id="de917-121">Server versie: 1809 + met RSAT-AD-Power shell</span><span class="sxs-lookup"><span data-stu-id="de917-121">Server version: 1809+ with RSAT-AD-PowerShell</span></span>
- <span data-ttu-id="de917-122">Windows 10-versie: 1809 + met RSAT. ActiveDirectory. DS-LDS. tools</span><span class="sxs-lookup"><span data-stu-id="de917-122">Windows 10 version: 1809+ with Rsat.ActiveDirectory.DS-LDS.Tools</span></span>

### <a name="adfs"></a><span data-ttu-id="de917-123">ADFS</span><span class="sxs-lookup"><span data-stu-id="de917-123">ADFS</span></span>

<span data-ttu-id="de917-124">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-124">Status: Untested with Compatibility Layer</span></span>

### <a name="appbackgroundtask"></a><span data-ttu-id="de917-125">AppBackgroundTask</span><span class="sxs-lookup"><span data-stu-id="de917-125">AppBackgroundTask</span></span>

<span data-ttu-id="de917-126">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-126">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-127">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-127">Compatible with:</span></span>

- <span data-ttu-id="de917-128">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-128">Windows 10 version: 1903+</span></span>

### <a name="applocker"></a><span data-ttu-id="de917-129">AppLocker</span><span class="sxs-lookup"><span data-stu-id="de917-129">AppLocker</span></span>

<span data-ttu-id="de917-130">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-130">Status: Untested with Compatibility Layer</span></span>

### <a name="appvclient"></a><span data-ttu-id="de917-131">AppvClient</span><span class="sxs-lookup"><span data-stu-id="de917-131">AppvClient</span></span>

<span data-ttu-id="de917-132">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-132">Status: Untested with Compatibility Layer</span></span>

### <a name="appx"></a><span data-ttu-id="de917-133">Appx</span><span class="sxs-lookup"><span data-stu-id="de917-133">Appx</span></span>

<span data-ttu-id="de917-134">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-134">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-135">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-135">Compatible with:</span></span>

- <span data-ttu-id="de917-136">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-136">Server version: 1809+</span></span>
- <span data-ttu-id="de917-137">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-137">Windows 10 version: 1809+</span></span>

### <a name="assignedaccess"></a><span data-ttu-id="de917-138">AssignedAccess</span><span class="sxs-lookup"><span data-stu-id="de917-138">AssignedAccess</span></span>

<span data-ttu-id="de917-139">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-139">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-140">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-140">Compatible with:</span></span>

- <span data-ttu-id="de917-141">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-141">Windows 10 version: 1809+</span></span>

### <a name="bestpractices"></a><span data-ttu-id="de917-142">BestPractices</span><span class="sxs-lookup"><span data-stu-id="de917-142">BestPractices</span></span>

<span data-ttu-id="de917-143">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-143">Status: Untested with Compatibility Layer</span></span>

### <a name="bitlocker"></a><span data-ttu-id="de917-144">BitLocker</span><span class="sxs-lookup"><span data-stu-id="de917-144">BitLocker</span></span>

<span data-ttu-id="de917-145">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-145">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-146">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-146">Compatible with:</span></span>

- <span data-ttu-id="de917-147">Server versie: 1809 + met BitLocker</span><span class="sxs-lookup"><span data-stu-id="de917-147">Server version: 1809+ with BitLocker</span></span>
- <span data-ttu-id="de917-148">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-148">Windows 10 version: 1809+</span></span>

### <a name="bitstransfer"></a><span data-ttu-id="de917-149">BitsTransfer</span><span class="sxs-lookup"><span data-stu-id="de917-149">BitsTransfer</span></span>

<span data-ttu-id="de917-150">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-150">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-151">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-151">Compatible with:</span></span>

- <span data-ttu-id="de917-152">Server versie: 20H1</span><span class="sxs-lookup"><span data-stu-id="de917-152">Server version: 20H1</span></span>
- <span data-ttu-id="de917-153">Windows 10-versie: 20H1</span><span class="sxs-lookup"><span data-stu-id="de917-153">Windows 10 version: 20H1</span></span>

### <a name="booteventcollector"></a><span data-ttu-id="de917-154">BootEventCollector</span><span class="sxs-lookup"><span data-stu-id="de917-154">BootEventCollector</span></span>

<span data-ttu-id="de917-155">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-155">Status: Untested with Compatibility Layer</span></span>

### <a name="branchcache"></a><span data-ttu-id="de917-156">BranchCache</span><span class="sxs-lookup"><span data-stu-id="de917-156">BranchCache</span></span>

<span data-ttu-id="de917-157">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-157">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-158">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-158">Compatible with:</span></span>

- <span data-ttu-id="de917-159">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-159">Server version: 1809+</span></span>
- <span data-ttu-id="de917-160">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-160">Windows 10 version: 1809+</span></span>

### <a name="cimcmdlets"></a><span data-ttu-id="de917-161">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="de917-161">CimCmdlets</span></span>

<span data-ttu-id="de917-162">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-162">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-163">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-163">Compatible with:</span></span>

- <span data-ttu-id="de917-164">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-164">Built into PowerShell 7</span></span>

### <a name="clusterawareupdating"></a><span data-ttu-id="de917-165">ClusterAwareUpdating</span><span class="sxs-lookup"><span data-stu-id="de917-165">ClusterAwareUpdating</span></span>

<span data-ttu-id="de917-166">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-166">Status: Untested with Compatibility Layer</span></span>

### <a name="configci"></a><span data-ttu-id="de917-167">ConfigCI</span><span class="sxs-lookup"><span data-stu-id="de917-167">ConfigCI</span></span>

<span data-ttu-id="de917-168">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-168">Status: Untested with Compatibility Layer</span></span>

### <a name="defender"></a><span data-ttu-id="de917-169">Beschermd</span><span class="sxs-lookup"><span data-stu-id="de917-169">Defender</span></span>

<span data-ttu-id="de917-170">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-170">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-171">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-171">Compatible with:</span></span>

- <span data-ttu-id="de917-172">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-172">Server version: 1809+</span></span>
- <span data-ttu-id="de917-173">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-173">Windows 10 version: 1809+</span></span>

### <a name="deliveryoptimization"></a><span data-ttu-id="de917-174">DeliveryOptimization</span><span class="sxs-lookup"><span data-stu-id="de917-174">DeliveryOptimization</span></span>

<span data-ttu-id="de917-175">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-175">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-176">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-176">Compatible with:</span></span>

- <span data-ttu-id="de917-177">Server versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-177">Server version: 1903+</span></span>
- <span data-ttu-id="de917-178">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-178">Windows 10 version: 1903+</span></span>

### <a name="dfsn"></a><span data-ttu-id="de917-179">DFSN</span><span class="sxs-lookup"><span data-stu-id="de917-179">DFSN</span></span>

<span data-ttu-id="de917-180">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-180">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-181">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-181">Compatible with:</span></span>

- <span data-ttu-id="de917-182">Server versie: 1809 + met FS-DFS-naam ruimte</span><span class="sxs-lookup"><span data-stu-id="de917-182">Server version: 1809+ with FS-DFS-Namespace</span></span>
- <span data-ttu-id="de917-183">Windows 10-versie: 1809 + met RSAT. FailoverCluster. Management. tools</span><span class="sxs-lookup"><span data-stu-id="de917-183">Windows 10 version: 1809+ with Rsat.FailoverCluster.Management.Tools</span></span>

### <a name="dfsr"></a><span data-ttu-id="de917-184">DFSR</span><span class="sxs-lookup"><span data-stu-id="de917-184">DFSR</span></span>

<span data-ttu-id="de917-185">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-185">Status: Untested with Compatibility Layer</span></span>

### <a name="dhcpserver"></a><span data-ttu-id="de917-186">DHCP</span><span class="sxs-lookup"><span data-stu-id="de917-186">DhcpServer</span></span>

<span data-ttu-id="de917-187">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-187">Status: Untested with Compatibility Layer</span></span>

### <a name="directaccessclientcomponents"></a><span data-ttu-id="de917-188">DirectAccessClientComponents</span><span class="sxs-lookup"><span data-stu-id="de917-188">DirectAccessClientComponents</span></span>

<span data-ttu-id="de917-189">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-189">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-190">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-190">Compatible with:</span></span>

- <span data-ttu-id="de917-191">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-191">Server version: 1809+</span></span>
- <span data-ttu-id="de917-192">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-192">Windows 10 version: 1809+</span></span>

### <a name="dism"></a><span data-ttu-id="de917-193">DISM</span><span class="sxs-lookup"><span data-stu-id="de917-193">Dism</span></span>

<span data-ttu-id="de917-194">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-194">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-195">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-195">Compatible with:</span></span>

- <span data-ttu-id="de917-196">Server versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-196">Server version: 1903+</span></span>
- <span data-ttu-id="de917-197">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-197">Windows 10 version: 1903+</span></span>

### <a name="dnsclient"></a><span data-ttu-id="de917-198">DnsClient</span><span class="sxs-lookup"><span data-stu-id="de917-198">DnsClient</span></span>

<span data-ttu-id="de917-199">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-199">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-200">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-200">Compatible with:</span></span>

- <span data-ttu-id="de917-201">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-201">Server version: 1809+</span></span>
- <span data-ttu-id="de917-202">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-202">Windows 10 version: 1809+</span></span>

### <a name="dnsserver"></a><span data-ttu-id="de917-203">DnsServer</span><span class="sxs-lookup"><span data-stu-id="de917-203">DnsServer</span></span>

<span data-ttu-id="de917-204">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-204">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-205">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-205">Compatible with:</span></span>

- <span data-ttu-id="de917-206">Server versie: 1809 + met DNS of RSAT-DNS-server</span><span class="sxs-lookup"><span data-stu-id="de917-206">Server version: 1809+ with DNS or RSAT-DNS-Server</span></span>
- <span data-ttu-id="de917-207">Windows 10-versie: 1809 + met RSAT. DNS. tools</span><span class="sxs-lookup"><span data-stu-id="de917-207">Windows 10 version: 1809+ with Rsat.Dns.Tools</span></span>

### <a name="eventtracingmanagement"></a><span data-ttu-id="de917-208">EventTracingManagement</span><span class="sxs-lookup"><span data-stu-id="de917-208">EventTracingManagement</span></span>

<span data-ttu-id="de917-209">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-209">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-210">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-210">Compatible with:</span></span>

- <span data-ttu-id="de917-211">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-211">Server version: 1809+</span></span>
- <span data-ttu-id="de917-212">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-212">Windows 10 version: 1809+</span></span>

### <a name="failoverclusters"></a><span data-ttu-id="de917-213">FailoverClusters</span><span class="sxs-lookup"><span data-stu-id="de917-213">FailoverClusters</span></span>

<span data-ttu-id="de917-214">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-214">Status: Untested with Compatibility Layer</span></span>

### <a name="failoverclusterset"></a><span data-ttu-id="de917-215">FailoverClusterSet</span><span class="sxs-lookup"><span data-stu-id="de917-215">FailoverClusterSet</span></span>

<span data-ttu-id="de917-216">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-216">Status: Untested with Compatibility Layer</span></span>

### <a name="fileserverresourcemanager"></a><span data-ttu-id="de917-217">FileServerResourceManager</span><span class="sxs-lookup"><span data-stu-id="de917-217">FileServerResourceManager</span></span>

<span data-ttu-id="de917-218">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-218">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-219">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-219">Compatible with:</span></span>

- <span data-ttu-id="de917-220">Server versie: 1809 + met FS-Resource-Manager</span><span class="sxs-lookup"><span data-stu-id="de917-220">Server version: 1809+ with FS-Resource-Manager</span></span>

### <a name="grouppolicy"></a><span data-ttu-id="de917-221">Architectuur</span><span class="sxs-lookup"><span data-stu-id="de917-221">GroupPolicy</span></span>

<span data-ttu-id="de917-222">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-222">Status: Untested with Compatibility Layer</span></span>

### <a name="hgsclient"></a><span data-ttu-id="de917-223">HgsClient</span><span class="sxs-lookup"><span data-stu-id="de917-223">HgsClient</span></span>

<span data-ttu-id="de917-224">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-224">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-225">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-225">Compatible with:</span></span>

- <span data-ttu-id="de917-226">Server versie: 1903 + met Hyper-V of RSAT-afgeschermde-VM-Hulpprogram Ma's</span><span class="sxs-lookup"><span data-stu-id="de917-226">Server version: 1903+ with Hyper-V or RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="de917-227">Windows 10-versie: 1903 + met RSAT. afgeschermde. VM. tools</span><span class="sxs-lookup"><span data-stu-id="de917-227">Windows 10 version: 1903+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="hgsdiagnostics"></a><span data-ttu-id="de917-228">HgsDiagnostics</span><span class="sxs-lookup"><span data-stu-id="de917-228">HgsDiagnostics</span></span>

<span data-ttu-id="de917-229">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-229">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-230">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-230">Compatible with:</span></span>

- <span data-ttu-id="de917-231">Server versie: 1809 + met Hyper-V of RSAT-afgeschermde-VM-Hulpprogram Ma's</span><span class="sxs-lookup"><span data-stu-id="de917-231">Server version: 1809+ with Hyper-V or RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="de917-232">Windows 10-versie: 1809 + met RSAT. afgeschermde. VM. tools</span><span class="sxs-lookup"><span data-stu-id="de917-232">Windows 10 version: 1809+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="hyper-v"></a><span data-ttu-id="de917-233">Hyper-V</span><span class="sxs-lookup"><span data-stu-id="de917-233">Hyper-V</span></span>

<span data-ttu-id="de917-234">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-234">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-235">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-235">Compatible with:</span></span>

- <span data-ttu-id="de917-236">Server versie: 1809 + met Hyper-V-Power shell</span><span class="sxs-lookup"><span data-stu-id="de917-236">Server version: 1809+ with Hyper-V-PowerShell</span></span>
- <span data-ttu-id="de917-237">Windows 10-versie: 1809 + met micro soft-Hyper-V-Management-Power shell</span><span class="sxs-lookup"><span data-stu-id="de917-237">Windows 10 version: 1809+ with Microsoft-Hyper-V-Management-PowerShell</span></span>

### <a name="iisadministration"></a><span data-ttu-id="de917-238">IISAdministration</span><span class="sxs-lookup"><span data-stu-id="de917-238">IISAdministration</span></span>

<span data-ttu-id="de917-239">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-239">Status: Untested with Compatibility Layer</span></span>

### <a name="international"></a><span data-ttu-id="de917-240">Nederland</span><span class="sxs-lookup"><span data-stu-id="de917-240">International</span></span>

<span data-ttu-id="de917-241">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-241">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-242">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-242">Compatible with:</span></span>

- <span data-ttu-id="de917-243">Server versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-243">Server version: 1903+</span></span>
- <span data-ttu-id="de917-244">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-244">Windows 10 version: 1903+</span></span>

### <a name="ipamserver"></a><span data-ttu-id="de917-245">IpamServer</span><span class="sxs-lookup"><span data-stu-id="de917-245">IpamServer</span></span>

<span data-ttu-id="de917-246">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-246">Status: Untested with Compatibility Layer</span></span>

### <a name="iscsi"></a><span data-ttu-id="de917-247">iSCSI</span><span class="sxs-lookup"><span data-stu-id="de917-247">iSCSI</span></span>

<span data-ttu-id="de917-248">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-248">Status: Untested with Compatibility Layer</span></span>

### <a name="iscsitarget"></a><span data-ttu-id="de917-249">IscsiTarget</span><span class="sxs-lookup"><span data-stu-id="de917-249">IscsiTarget</span></span>

<span data-ttu-id="de917-250">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-250">Status: Untested with Compatibility Layer</span></span>

### <a name="ise"></a><span data-ttu-id="de917-251">ISE</span><span class="sxs-lookup"><span data-stu-id="de917-251">ISE</span></span>

<span data-ttu-id="de917-252">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-252">Status: Untested with Compatibility Layer</span></span>

### <a name="kds"></a><span data-ttu-id="de917-253">KDS</span><span class="sxs-lookup"><span data-stu-id="de917-253">Kds</span></span>

<span data-ttu-id="de917-254">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-254">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-255">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-255">Compatible with:</span></span>

- <span data-ttu-id="de917-256">Server versie: 20H1</span><span class="sxs-lookup"><span data-stu-id="de917-256">Server version: 20H1</span></span>
- <span data-ttu-id="de917-257">Windows 10-versie: 20H1</span><span class="sxs-lookup"><span data-stu-id="de917-257">Windows 10 version: 20H1</span></span>

### <a name="microsoftpowershellarchive"></a><span data-ttu-id="de917-258">Micro soft. Power shell. Archive</span><span class="sxs-lookup"><span data-stu-id="de917-258">Microsoft.PowerShell.Archive</span></span>

<span data-ttu-id="de917-259">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-259">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-260">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-260">Compatible with:</span></span>

- <span data-ttu-id="de917-261">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-261">Built into PowerShell 7</span></span>

### <a name="microsoftpowershelldiagnostics"></a><span data-ttu-id="de917-262">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="de917-262">Microsoft.PowerShell.Diagnostics</span></span>

<span data-ttu-id="de917-263">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-263">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-264">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-264">Compatible with:</span></span>

- <span data-ttu-id="de917-265">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-265">Built into PowerShell 7</span></span>

### <a name="microsoftpowershellhost"></a><span data-ttu-id="de917-266">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="de917-266">Microsoft.PowerShell.Host</span></span>

<span data-ttu-id="de917-267">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-267">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-268">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-268">Compatible with:</span></span>

- <span data-ttu-id="de917-269">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-269">Built into PowerShell 7</span></span>

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="de917-270">Micro soft. Power shell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="de917-270">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="de917-271">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-271">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-272">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-272">Compatible with:</span></span>

- <span data-ttu-id="de917-273">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-273">Server version: 1809+</span></span>
- <span data-ttu-id="de917-274">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-274">Windows 10 version: 1809+</span></span>

### <a name="microsoftpowershellmanagement"></a><span data-ttu-id="de917-275">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="de917-275">Microsoft.PowerShell.Management</span></span>

<span data-ttu-id="de917-276">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-276">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-277">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-277">Compatible with:</span></span>

- <span data-ttu-id="de917-278">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-278">Built into PowerShell 7</span></span>

### <a name="microsoftpowershellodatautils"></a><span data-ttu-id="de917-279">Micro soft. Power shell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="de917-279">Microsoft.PowerShell.ODataUtils</span></span>

<span data-ttu-id="de917-280">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-280">Status: Untested with Compatibility Layer</span></span>

### <a name="microsoftpowershellsecurity"></a><span data-ttu-id="de917-281">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="de917-281">Microsoft.PowerShell.Security</span></span>

<span data-ttu-id="de917-282">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-282">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-283">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-283">Compatible with:</span></span>

- <span data-ttu-id="de917-284">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-284">Built into PowerShell 7</span></span>

### <a name="microsoftpowershellutility"></a><span data-ttu-id="de917-285">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="de917-285">Microsoft.PowerShell.Utility</span></span>

<span data-ttu-id="de917-286">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-286">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-287">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-287">Compatible with:</span></span>

- <span data-ttu-id="de917-288">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-288">Built into PowerShell 7</span></span>

### <a name="microsoftwsmanmanagement"></a><span data-ttu-id="de917-289">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="de917-289">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="de917-290">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-290">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-291">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-291">Compatible with:</span></span>

- <span data-ttu-id="de917-292">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-292">Built into PowerShell 7</span></span>

### <a name="mmagent"></a><span data-ttu-id="de917-293">MMAgent</span><span class="sxs-lookup"><span data-stu-id="de917-293">MMAgent</span></span>

<span data-ttu-id="de917-294">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-294">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-295">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-295">Compatible with:</span></span>

- <span data-ttu-id="de917-296">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-296">Server version: 1809+</span></span>
- <span data-ttu-id="de917-297">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-297">Windows 10 version: 1809+</span></span>

### <a name="mpio"></a><span data-ttu-id="de917-298">MPIO</span><span class="sxs-lookup"><span data-stu-id="de917-298">MPIO</span></span>

<span data-ttu-id="de917-299">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-299">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-300">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-300">Compatible with:</span></span>

- <span data-ttu-id="de917-301">Server versie: 1809 + met meerdere paden-IO</span><span class="sxs-lookup"><span data-stu-id="de917-301">Server version: 1809+ with Multipath-IO</span></span>

### <a name="msdtc"></a><span data-ttu-id="de917-302">MsDtc</span><span class="sxs-lookup"><span data-stu-id="de917-302">MsDtc</span></span>

<span data-ttu-id="de917-303">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-303">Status: Untested with Compatibility Layer</span></span>

### <a name="netadapter"></a><span data-ttu-id="de917-304">NetAdapter</span><span class="sxs-lookup"><span data-stu-id="de917-304">NetAdapter</span></span>

<span data-ttu-id="de917-305">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-305">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-306">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-306">Compatible with:</span></span>

- <span data-ttu-id="de917-307">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-307">Server version: 1809+</span></span>
- <span data-ttu-id="de917-308">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-308">Windows 10 version: 1809+</span></span>

### <a name="netconnection"></a><span data-ttu-id="de917-309">NetConnection</span><span class="sxs-lookup"><span data-stu-id="de917-309">NetConnection</span></span>

<span data-ttu-id="de917-310">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-310">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-311">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-311">Compatible with:</span></span>

- <span data-ttu-id="de917-312">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-312">Server version: 1809+</span></span>
- <span data-ttu-id="de917-313">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-313">Windows 10 version: 1809+</span></span>

### <a name="neteventpacketcapture"></a><span data-ttu-id="de917-314">NetEventPacketCapture</span><span class="sxs-lookup"><span data-stu-id="de917-314">NetEventPacketCapture</span></span>

<span data-ttu-id="de917-315">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-315">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-316">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-316">Compatible with:</span></span>

- <span data-ttu-id="de917-317">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-317">Server version: 1809+</span></span>
- <span data-ttu-id="de917-318">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-318">Windows 10 version: 1809+</span></span>

### <a name="netlbfo"></a><span data-ttu-id="de917-319">NetLbfo</span><span class="sxs-lookup"><span data-stu-id="de917-319">NetLbfo</span></span>

<span data-ttu-id="de917-320">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-320">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-321">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-321">Compatible with:</span></span>

- <span data-ttu-id="de917-322">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-322">Server version: 1809+</span></span>
- <span data-ttu-id="de917-323">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-323">Windows 10 version: 1809+</span></span>

### <a name="netlldpagent"></a><span data-ttu-id="de917-324">NetLldpAgent</span><span class="sxs-lookup"><span data-stu-id="de917-324">NetLldpAgent</span></span>

<span data-ttu-id="de917-325">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-325">Status: Untested with Compatibility Layer</span></span>

### <a name="netnat"></a><span data-ttu-id="de917-326">NetNat</span><span class="sxs-lookup"><span data-stu-id="de917-326">NetNat</span></span>

<span data-ttu-id="de917-327">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-327">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-328">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-328">Compatible with:</span></span>

- <span data-ttu-id="de917-329">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-329">Server version: 1809+</span></span>
- <span data-ttu-id="de917-330">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-330">Windows 10 version: 1809+</span></span>

### <a name="netqos"></a><span data-ttu-id="de917-331">NetQos</span><span class="sxs-lookup"><span data-stu-id="de917-331">NetQos</span></span>

<span data-ttu-id="de917-332">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-332">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-333">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-333">Compatible with:</span></span>

- <span data-ttu-id="de917-334">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-334">Server version: 1809+</span></span>
- <span data-ttu-id="de917-335">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-335">Windows 10 version: 1809+</span></span>

### <a name="netsecurity"></a><span data-ttu-id="de917-336">Netbeveiliging</span><span class="sxs-lookup"><span data-stu-id="de917-336">NetSecurity</span></span>

<span data-ttu-id="de917-337">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-337">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-338">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-338">Compatible with:</span></span>

- <span data-ttu-id="de917-339">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-339">Server version: 1809+</span></span>
- <span data-ttu-id="de917-340">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-340">Windows 10 version: 1809+</span></span>

### <a name="netswitchteam"></a><span data-ttu-id="de917-341">NetSwitchTeam</span><span class="sxs-lookup"><span data-stu-id="de917-341">NetSwitchTeam</span></span>

<span data-ttu-id="de917-342">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-342">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-343">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-343">Compatible with:</span></span>

- <span data-ttu-id="de917-344">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-344">Server version: 1809+</span></span>
- <span data-ttu-id="de917-345">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-345">Windows 10 version: 1809+</span></span>

### <a name="nettcpip"></a><span data-ttu-id="de917-346">NetTCPIP</span><span class="sxs-lookup"><span data-stu-id="de917-346">NetTCPIP</span></span>

<span data-ttu-id="de917-347">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-347">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-348">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-348">Compatible with:</span></span>

- <span data-ttu-id="de917-349">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-349">Server version: 1809+</span></span>
- <span data-ttu-id="de917-350">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-350">Windows 10 version: 1809+</span></span>

### <a name="netwnv"></a><span data-ttu-id="de917-351">NetWNV</span><span class="sxs-lookup"><span data-stu-id="de917-351">NetWNV</span></span>

<span data-ttu-id="de917-352">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-352">Status: Untested with Compatibility Layer</span></span>

### <a name="networkconnectivitystatus"></a><span data-ttu-id="de917-353">NetworkConnectivityStatus</span><span class="sxs-lookup"><span data-stu-id="de917-353">NetworkConnectivityStatus</span></span>

<span data-ttu-id="de917-354">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-354">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-355">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-355">Compatible with:</span></span>

- <span data-ttu-id="de917-356">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-356">Server version: 1809+</span></span>
- <span data-ttu-id="de917-357">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-357">Windows 10 version: 1809+</span></span>

### <a name="networkcontroller"></a><span data-ttu-id="de917-358">Network controller</span><span class="sxs-lookup"><span data-stu-id="de917-358">NetworkController</span></span>

<span data-ttu-id="de917-359">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-359">Status: Untested with Compatibility Layer</span></span>

### <a name="networkcontrollerdiagnostics"></a><span data-ttu-id="de917-360">NetworkControllerDiagnostics</span><span class="sxs-lookup"><span data-stu-id="de917-360">NetworkControllerDiagnostics</span></span>

<span data-ttu-id="de917-361">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-361">Status: Untested with Compatibility Layer</span></span>

### <a name="networkloadbalancingclusters"></a><span data-ttu-id="de917-362">NetworkLoadBalancingClusters</span><span class="sxs-lookup"><span data-stu-id="de917-362">NetworkLoadBalancingClusters</span></span>

<span data-ttu-id="de917-363">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-363">Status: Untested with Compatibility Layer</span></span>

### <a name="networkswitchmanager"></a><span data-ttu-id="de917-364">NetworkSwitchManager</span><span class="sxs-lookup"><span data-stu-id="de917-364">NetworkSwitchManager</span></span>

<span data-ttu-id="de917-365">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-365">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-366">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-366">Compatible with:</span></span>

- <span data-ttu-id="de917-367">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-367">Server version: 1809+</span></span>
- <span data-ttu-id="de917-368">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-368">Windows 10 version: 1809+</span></span>

### <a name="networktransition"></a><span data-ttu-id="de917-369">NetworkTransition</span><span class="sxs-lookup"><span data-stu-id="de917-369">NetworkTransition</span></span>

<span data-ttu-id="de917-370">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-370">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-371">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-371">Compatible with:</span></span>

- <span data-ttu-id="de917-372">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-372">Server version: 1809+</span></span>
- <span data-ttu-id="de917-373">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-373">Windows 10 version: 1809+</span></span>

### <a name="nfs"></a><span data-ttu-id="de917-374">NFS</span><span class="sxs-lookup"><span data-stu-id="de917-374">NFS</span></span>

<span data-ttu-id="de917-375">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-375">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-376">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-376">Compatible with:</span></span>

- <span data-ttu-id="de917-377">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-377">Server version: 1809+</span></span>
- <span data-ttu-id="de917-378">Windows 10-versie: 1809 + met RSAT. Server Manager. tools</span><span class="sxs-lookup"><span data-stu-id="de917-378">Windows 10 version: 1809+ with Rsat.ServerManager.Tools</span></span>

### <a name="packagemanagement"></a><span data-ttu-id="de917-379">Package Management</span><span class="sxs-lookup"><span data-stu-id="de917-379">PackageManagement</span></span>

<span data-ttu-id="de917-380">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-380">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-381">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-381">Compatible with:</span></span>

- <span data-ttu-id="de917-382">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-382">Built into PowerShell 7</span></span>

### <a name="pcsvdevice"></a><span data-ttu-id="de917-383">PcsvDevice</span><span class="sxs-lookup"><span data-stu-id="de917-383">PcsvDevice</span></span>

<span data-ttu-id="de917-384">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-384">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-385">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-385">Compatible with:</span></span>

- <span data-ttu-id="de917-386">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-386">Server version: 1809+</span></span>
- <span data-ttu-id="de917-387">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-387">Windows 10 version: 1809+</span></span>

### <a name="persistentmemory"></a><span data-ttu-id="de917-388">PersistentMemory</span><span class="sxs-lookup"><span data-stu-id="de917-388">PersistentMemory</span></span>

<span data-ttu-id="de917-389">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-389">Status: Untested with Compatibility Layer</span></span>

### <a name="pki"></a><span data-ttu-id="de917-390">PKI</span><span class="sxs-lookup"><span data-stu-id="de917-390">PKI</span></span>

<span data-ttu-id="de917-391">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-391">Status: Untested with Compatibility Layer</span></span>

### <a name="pnpdevice"></a><span data-ttu-id="de917-392">PnpDevice</span><span class="sxs-lookup"><span data-stu-id="de917-392">PnpDevice</span></span>

<span data-ttu-id="de917-393">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-393">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-394">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-394">Compatible with:</span></span>

- <span data-ttu-id="de917-395">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-395">Server version: 1809+</span></span>
- <span data-ttu-id="de917-396">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-396">Windows 10 version: 1809+</span></span>

### <a name="powershellget"></a><span data-ttu-id="de917-397">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="de917-397">PowerShellGet</span></span>

<span data-ttu-id="de917-398">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-398">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-399">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-399">Compatible with:</span></span>

- <span data-ttu-id="de917-400">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-400">Built into PowerShell 7</span></span>

### <a name="printmanagement"></a><span data-ttu-id="de917-401">PrintManagement</span><span class="sxs-lookup"><span data-stu-id="de917-401">PrintManagement</span></span>

<span data-ttu-id="de917-402">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-402">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-403">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-403">Compatible with:</span></span>

- <span data-ttu-id="de917-404">Server versie: 1903 + met Afdruk Services</span><span class="sxs-lookup"><span data-stu-id="de917-404">Server version: 1903+ with Print-Services</span></span>
- <span data-ttu-id="de917-405">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-405">Windows 10 version: 1903+</span></span>

### <a name="processmitigations"></a><span data-ttu-id="de917-406">ProcessMitigations</span><span class="sxs-lookup"><span data-stu-id="de917-406">ProcessMitigations</span></span>

<span data-ttu-id="de917-407">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-407">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-408">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-408">Compatible with:</span></span>

- <span data-ttu-id="de917-409">Server versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-409">Server version: 1903+</span></span>
- <span data-ttu-id="de917-410">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-410">Windows 10 version: 1903+</span></span>

### <a name="provisioning"></a><span data-ttu-id="de917-411">Inrichten</span><span class="sxs-lookup"><span data-stu-id="de917-411">Provisioning</span></span>

<span data-ttu-id="de917-412">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-412">Status: Untested with Compatibility Layer</span></span>

### <a name="psdesiredstateconfiguration"></a><span data-ttu-id="de917-413">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="de917-413">PSDesiredStateConfiguration</span></span>

<span data-ttu-id="de917-414">Status: gedeeltelijk</span><span class="sxs-lookup"><span data-stu-id="de917-414">Status: Partially</span></span>

<span data-ttu-id="de917-415">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-415">Compatible with:</span></span>

- <span data-ttu-id="de917-416">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-416">Built into PowerShell 7</span></span>

### <a name="psdiagnostics"></a><span data-ttu-id="de917-417">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="de917-417">PSDiagnostics</span></span>

<span data-ttu-id="de917-418">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-418">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-419">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-419">Compatible with:</span></span>

- <span data-ttu-id="de917-420">Ingebouwd in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="de917-420">Built into PowerShell 7</span></span>

### <a name="psscheduledjob"></a><span data-ttu-id="de917-421">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="de917-421">PSScheduledJob</span></span>

<span data-ttu-id="de917-422">Status: werkt niet met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-422">Status: Not working with Compatibility Layer</span></span>

<span data-ttu-id="de917-423">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-423">Compatible with:</span></span>

- <span data-ttu-id="de917-424">Ingebouwd in Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="de917-424">Built into PowerShell 5.1</span></span>

### <a name="psworkflow"></a><span data-ttu-id="de917-425">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="de917-425">PSWorkflow</span></span>

<span data-ttu-id="de917-426">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-426">Status: Untested with Compatibility Layer</span></span>

### <a name="psworkflowutility"></a><span data-ttu-id="de917-427">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="de917-427">PSWorkflowUtility</span></span>

<span data-ttu-id="de917-428">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-428">Status: Untested with Compatibility Layer</span></span>

### <a name="remoteaccess"></a><span data-ttu-id="de917-429">Remote</span><span class="sxs-lookup"><span data-stu-id="de917-429">RemoteAccess</span></span>

<span data-ttu-id="de917-430">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-430">Status: Untested with Compatibility Layer</span></span>

### <a name="remotedesktop"></a><span data-ttu-id="de917-431">RemoteDesktop</span><span class="sxs-lookup"><span data-stu-id="de917-431">RemoteDesktop</span></span>

<span data-ttu-id="de917-432">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-432">Status: Untested with Compatibility Layer</span></span>

### <a name="scheduledtasks"></a><span data-ttu-id="de917-433">ScheduledTasks</span><span class="sxs-lookup"><span data-stu-id="de917-433">ScheduledTasks</span></span>

<span data-ttu-id="de917-434">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-434">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-435">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-435">Compatible with:</span></span>

- <span data-ttu-id="de917-436">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-436">Server version: 1809+</span></span>
- <span data-ttu-id="de917-437">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-437">Windows 10 version: 1809+</span></span>

### <a name="secureboot"></a><span data-ttu-id="de917-438">SecureBoot</span><span class="sxs-lookup"><span data-stu-id="de917-438">SecureBoot</span></span>

<span data-ttu-id="de917-439">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-439">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-440">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-440">Compatible with:</span></span>

- <span data-ttu-id="de917-441">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-441">Server version: 1809+</span></span>
- <span data-ttu-id="de917-442">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-442">Windows 10 version: 1809+</span></span>

### <a name="servercore"></a><span data-ttu-id="de917-443">ServerCore</span><span class="sxs-lookup"><span data-stu-id="de917-443">ServerCore</span></span>

<span data-ttu-id="de917-444">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-444">Status: Untested with Compatibility Layer</span></span>

### <a name="servermanager"></a><span data-ttu-id="de917-445">Manager</span><span class="sxs-lookup"><span data-stu-id="de917-445">ServerManager</span></span>

<span data-ttu-id="de917-446">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-446">Status: Untested with Compatibility Layer</span></span>

### <a name="servermanagertasks"></a><span data-ttu-id="de917-447">ServerManagerTasks</span><span class="sxs-lookup"><span data-stu-id="de917-447">ServerManagerTasks</span></span>

<span data-ttu-id="de917-448">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-448">Status: Untested with Compatibility Layer</span></span>

### <a name="shieldedvmdatafile"></a><span data-ttu-id="de917-449">ShieldedVMDataFile</span><span class="sxs-lookup"><span data-stu-id="de917-449">ShieldedVMDataFile</span></span>

<span data-ttu-id="de917-450">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-450">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-451">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-451">Compatible with:</span></span>

- <span data-ttu-id="de917-452">Server versie: 1903 + met RSAT-afgeschermde-VM-Hulpprogram Ma's</span><span class="sxs-lookup"><span data-stu-id="de917-452">Server version: 1903+ with RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="de917-453">Windows 10-versie: 1903 + met RSAT. afgeschermde. VM. tools</span><span class="sxs-lookup"><span data-stu-id="de917-453">Windows 10 version: 1903+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="shieldedvmprovisioning"></a><span data-ttu-id="de917-454">ShieldedVMProvisioning</span><span class="sxs-lookup"><span data-stu-id="de917-454">ShieldedVMProvisioning</span></span>

<span data-ttu-id="de917-455">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-455">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-456">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-456">Compatible with:</span></span>

- <span data-ttu-id="de917-457">Server versie: 1809 + met HostGuardian</span><span class="sxs-lookup"><span data-stu-id="de917-457">Server version: 1809+ with HostGuardian</span></span>
- <span data-ttu-id="de917-458">Windows 10-versie: 1809 + met HostGuardian</span><span class="sxs-lookup"><span data-stu-id="de917-458">Windows 10 version: 1809+ with HostGuardian</span></span>

### <a name="shieldedvmtemplate"></a><span data-ttu-id="de917-459">ShieldedVMTemplate</span><span class="sxs-lookup"><span data-stu-id="de917-459">ShieldedVMTemplate</span></span>

<span data-ttu-id="de917-460">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-460">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-461">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-461">Compatible with:</span></span>

- <span data-ttu-id="de917-462">Server versie: 1809 + met RSAT-afgeschermde-VM-Hulpprogram Ma's</span><span class="sxs-lookup"><span data-stu-id="de917-462">Server version: 1809+ with RSAT-Shielded-VM-Tools</span></span>
- <span data-ttu-id="de917-463">Windows 10-versie: 1809 + met RSAT. afgeschermde. VM. tools</span><span class="sxs-lookup"><span data-stu-id="de917-463">Windows 10 version: 1809+ with Rsat.Shielded.VM.Tools</span></span>

### <a name="smbshare"></a><span data-ttu-id="de917-464">SmbShare</span><span class="sxs-lookup"><span data-stu-id="de917-464">SmbShare</span></span>

<span data-ttu-id="de917-465">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-465">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-466">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-466">Compatible with:</span></span>

- <span data-ttu-id="de917-467">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-467">Server version: 1809+</span></span>
- <span data-ttu-id="de917-468">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-468">Windows 10 version: 1809+</span></span>

### <a name="smbwitness"></a><span data-ttu-id="de917-469">SmbWitness</span><span class="sxs-lookup"><span data-stu-id="de917-469">SmbWitness</span></span>

<span data-ttu-id="de917-470">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-470">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-471">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-471">Compatible with:</span></span>

- <span data-ttu-id="de917-472">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-472">Server version: 1809+</span></span>
- <span data-ttu-id="de917-473">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-473">Windows 10 version: 1809+</span></span>

### <a name="smisconfig"></a><span data-ttu-id="de917-474">SMISConfig</span><span class="sxs-lookup"><span data-stu-id="de917-474">SMISConfig</span></span>

<span data-ttu-id="de917-475">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-475">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-476">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-476">Compatible with:</span></span>

- <span data-ttu-id="de917-477">Server versie: 1903 + met WindowsStorageManagementService</span><span class="sxs-lookup"><span data-stu-id="de917-477">Server version: 1903+ with WindowsStorageManagementService</span></span>

### <a name="sms"></a><span data-ttu-id="de917-478">Sms</span><span class="sxs-lookup"><span data-stu-id="de917-478">SMS</span></span>

<span data-ttu-id="de917-479">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-479">Status: Untested with Compatibility Layer</span></span>

### <a name="softwareinventorylogging"></a><span data-ttu-id="de917-480">SoftwareInventoryLogging</span><span class="sxs-lookup"><span data-stu-id="de917-480">SoftwareInventoryLogging</span></span>

<span data-ttu-id="de917-481">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-481">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-482">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-482">Compatible with:</span></span>

- <span data-ttu-id="de917-483">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-483">Server version: 1809+</span></span>

### <a name="startlayout"></a><span data-ttu-id="de917-484">StartLayout</span><span class="sxs-lookup"><span data-stu-id="de917-484">StartLayout</span></span>

<span data-ttu-id="de917-485">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-485">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-486">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-486">Compatible with:</span></span>

- <span data-ttu-id="de917-487">Server versie: 1809 + met bureaublad ervaring</span><span class="sxs-lookup"><span data-stu-id="de917-487">Server version: 1809+ with Desktop Experience</span></span>
- <span data-ttu-id="de917-488">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-488">Windows 10 version: 1809+</span></span>

### <a name="storage"></a><span data-ttu-id="de917-489">Opslag</span><span class="sxs-lookup"><span data-stu-id="de917-489">Storage</span></span>

<span data-ttu-id="de917-490">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-490">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-491">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-491">Compatible with:</span></span>

- <span data-ttu-id="de917-492">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-492">Server version: 1809+</span></span>
- <span data-ttu-id="de917-493">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-493">Windows 10 version: 1809+</span></span>

### <a name="storagebuscache"></a><span data-ttu-id="de917-494">StorageBusCache</span><span class="sxs-lookup"><span data-stu-id="de917-494">StorageBusCache</span></span>

<span data-ttu-id="de917-495">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-495">Status: Untested with Compatibility Layer</span></span>

### <a name="storagemigrationservice"></a><span data-ttu-id="de917-496">StorageMigrationService</span><span class="sxs-lookup"><span data-stu-id="de917-496">StorageMigrationService</span></span>

<span data-ttu-id="de917-497">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-497">Status: Untested with Compatibility Layer</span></span>

### <a name="storageqos"></a><span data-ttu-id="de917-498">StorageQOS</span><span class="sxs-lookup"><span data-stu-id="de917-498">StorageQOS</span></span>

<span data-ttu-id="de917-499">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-499">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-500">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-500">Compatible with:</span></span>

- <span data-ttu-id="de917-501">Server versie: 1809 + met RSAT-clustering-Power shell</span><span class="sxs-lookup"><span data-stu-id="de917-501">Server version: 1809+ with RSAT-Clustering-PowerShell</span></span>
- <span data-ttu-id="de917-502">Windows 10-versie: 1809 + met RSAT. FailoverCluster. Management. tools</span><span class="sxs-lookup"><span data-stu-id="de917-502">Windows 10 version: 1809+ with Rsat.FailoverCluster.Management.Tools</span></span>

### <a name="storagereplica"></a><span data-ttu-id="de917-503">Storage replica</span><span class="sxs-lookup"><span data-stu-id="de917-503">StorageReplica</span></span>

<span data-ttu-id="de917-504">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-504">Status: Untested with Compatibility Layer</span></span>

### <a name="syncshare"></a><span data-ttu-id="de917-505">SyncShare</span><span class="sxs-lookup"><span data-stu-id="de917-505">SyncShare</span></span>

<span data-ttu-id="de917-506">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-506">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-507">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-507">Compatible with:</span></span>

- <span data-ttu-id="de917-508">Server versie: 1809 + met FS-SyncShareService</span><span class="sxs-lookup"><span data-stu-id="de917-508">Server version: 1809+ with FS-SyncShareService</span></span>

### <a name="systeminsights"></a><span data-ttu-id="de917-509">SystemInsights</span><span class="sxs-lookup"><span data-stu-id="de917-509">SystemInsights</span></span>

<span data-ttu-id="de917-510">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-510">Status: Untested with Compatibility Layer</span></span>

### <a name="tls"></a><span data-ttu-id="de917-511">TLS</span><span class="sxs-lookup"><span data-stu-id="de917-511">TLS</span></span>

<span data-ttu-id="de917-512">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-512">Status: Untested with Compatibility Layer</span></span>

### <a name="troubleshootingpack"></a><span data-ttu-id="de917-513">TroubleshootingPack</span><span class="sxs-lookup"><span data-stu-id="de917-513">TroubleshootingPack</span></span>

<span data-ttu-id="de917-514">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-514">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-515">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-515">Compatible with:</span></span>

- <span data-ttu-id="de917-516">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-516">Windows 10 version: 1903+</span></span>

### <a name="trustedplatformmodule"></a><span data-ttu-id="de917-517">TrustedPlatformModule</span><span class="sxs-lookup"><span data-stu-id="de917-517">TrustedPlatformModule</span></span>

<span data-ttu-id="de917-518">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-518">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-519">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-519">Compatible with:</span></span>

- <span data-ttu-id="de917-520">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-520">Server version: 1809+</span></span>
- <span data-ttu-id="de917-521">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-521">Windows 10 version: 1809+</span></span>

### <a name="uev"></a><span data-ttu-id="de917-522">UEV</span><span class="sxs-lookup"><span data-stu-id="de917-522">UEV</span></span>

<span data-ttu-id="de917-523">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-523">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-524">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-524">Compatible with:</span></span>

- <span data-ttu-id="de917-525">Server versie:? Toekomstige versie van server met bureaublad ervaring?</span><span class="sxs-lookup"><span data-stu-id="de917-525">Server version: ??Future version of Server with Desktop Experience??</span></span>
- <span data-ttu-id="de917-526">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-526">Windows 10 version: 1903+</span></span>

### <a name="updateservices"></a><span data-ttu-id="de917-527">Installeer WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="de917-527">UpdateServices</span></span>

<span data-ttu-id="de917-528">Status: werkt niet met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-528">Status: Not working with Compatibility Layer</span></span>

### <a name="vpnclient"></a><span data-ttu-id="de917-529">VpnClient</span><span class="sxs-lookup"><span data-stu-id="de917-529">VpnClient</span></span>

<span data-ttu-id="de917-530">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-530">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-531">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-531">Compatible with:</span></span>

- <span data-ttu-id="de917-532">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-532">Server version: 1809+</span></span>
- <span data-ttu-id="de917-533">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-533">Windows 10 version: 1809+</span></span>

### <a name="wdac"></a><span data-ttu-id="de917-534">Wdac</span><span class="sxs-lookup"><span data-stu-id="de917-534">Wdac</span></span>

<span data-ttu-id="de917-535">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-535">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-536">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-536">Compatible with:</span></span>

- <span data-ttu-id="de917-537">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-537">Server version: 1809+</span></span>
- <span data-ttu-id="de917-538">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-538">Windows 10 version: 1809+</span></span>

### <a name="webadministration"></a><span data-ttu-id="de917-539">Webbeheer</span><span class="sxs-lookup"><span data-stu-id="de917-539">WebAdministration</span></span>

<span data-ttu-id="de917-540">Status: niet getest met compatibiliteit slaag</span><span class="sxs-lookup"><span data-stu-id="de917-540">Status: Untested with Compatibility Layer</span></span>

### <a name="whea"></a><span data-ttu-id="de917-541">WHEA</span><span class="sxs-lookup"><span data-stu-id="de917-541">WHEA</span></span>

<span data-ttu-id="de917-542">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-542">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-543">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-543">Compatible with:</span></span>

- <span data-ttu-id="de917-544">Server versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-544">Server version: 1903+</span></span>
- <span data-ttu-id="de917-545">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-545">Windows 10 version: 1903+</span></span>

### <a name="windowsdeveloperlicense"></a><span data-ttu-id="de917-546">WindowsDeveloperLicense</span><span class="sxs-lookup"><span data-stu-id="de917-546">WindowsDeveloperLicense</span></span>

<span data-ttu-id="de917-547">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-547">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-548">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-548">Compatible with:</span></span>

- <span data-ttu-id="de917-549">Server versie: 1809 + met bureaublad ervaring</span><span class="sxs-lookup"><span data-stu-id="de917-549">Server version: 1809+ with Desktop Experience</span></span>
- <span data-ttu-id="de917-550">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-550">Windows 10 version: 1809+</span></span>

### <a name="windowserrorreporting"></a><span data-ttu-id="de917-551">WindowsErrorReporting</span><span class="sxs-lookup"><span data-stu-id="de917-551">WindowsErrorReporting</span></span>

<span data-ttu-id="de917-552">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-552">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-553">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-553">Compatible with:</span></span>

- <span data-ttu-id="de917-554">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-554">Server version: 1809+</span></span>
- <span data-ttu-id="de917-555">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-555">Windows 10 version: 1809+</span></span>

### <a name="windowssearch"></a><span data-ttu-id="de917-556">WindowsSearch</span><span class="sxs-lookup"><span data-stu-id="de917-556">WindowsSearch</span></span>

<span data-ttu-id="de917-557">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-557">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-558">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-558">Compatible with:</span></span>

- <span data-ttu-id="de917-559">Windows 10-versie: 1903 +</span><span class="sxs-lookup"><span data-stu-id="de917-559">Windows 10 version: 1903+</span></span>

### <a name="windowsserverbackup"></a><span data-ttu-id="de917-560">WindowsServerBackup</span><span class="sxs-lookup"><span data-stu-id="de917-560">WindowsServerBackup</span></span>

<span data-ttu-id="de917-561">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-561">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-562">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-562">Compatible with:</span></span>

- <span data-ttu-id="de917-563">Server versie: 19H2 met Windows-Server-Backup</span><span class="sxs-lookup"><span data-stu-id="de917-563">Server version: 19H2 with Windows-Server-Backup</span></span>

### <a name="windowsupdate"></a><span data-ttu-id="de917-564">WindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="de917-564">WindowsUpdate</span></span>

<span data-ttu-id="de917-565">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-565">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-566">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-566">Compatible with:</span></span>

- <span data-ttu-id="de917-567">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-567">Server version: 1809+</span></span>
- <span data-ttu-id="de917-568">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-568">Windows 10 version: 1809+</span></span>

### <a name="windowsupdateprovider"></a><span data-ttu-id="de917-569">WindowsUpdateProvider</span><span class="sxs-lookup"><span data-stu-id="de917-569">WindowsUpdateProvider</span></span>

<span data-ttu-id="de917-570">Status: systeem eigen compatibel</span><span class="sxs-lookup"><span data-stu-id="de917-570">Status: Natively Compatible</span></span>

<span data-ttu-id="de917-571">Compatibel met:</span><span class="sxs-lookup"><span data-stu-id="de917-571">Compatible with:</span></span>

- <span data-ttu-id="de917-572">Server versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-572">Server version: 1809+</span></span>
- <span data-ttu-id="de917-573">Windows 10-versie: 1809 +</span><span class="sxs-lookup"><span data-stu-id="de917-573">Windows 10 version: 1809+</span></span>
