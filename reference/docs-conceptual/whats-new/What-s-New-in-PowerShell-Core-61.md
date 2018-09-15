---
title: Wat is er nieuw in PowerShell Core 6.1
description: Nieuwe functies en wijzigingen die zijn uitgebracht in PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: b95b9dd504ea2a165a4689a3b28d2298644e5e68
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611519"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="05256-103">Wat is er nieuw in PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="05256-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="05256-104">Hieronder ziet u een selectie van een aantal van de belangrijkste nieuwe functies en wijzigingen die zijn geïntroduceerd in PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="05256-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="05256-105">Er is ook **ton** van "fijne" waardoor PowerShell sneller en stabieler (plus veel en veel fouten opgelost).</span><span class="sxs-lookup"><span data-stu-id="05256-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="05256-106">Voor een volledige lijst van wijzigingen, Bekijk onze [changelog op GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="05256-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="05256-107">En hoewel we noemen enkele onderstaande namen, Hartelijk dank aan [alle van de community-inzenders](https://github.com/PowerShell/PowerShell/graphs/contributors) die deze versie mogelijk gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05256-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="05256-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="05256-108">.NET Core 2.1</span></span>

<span data-ttu-id="05256-109">PowerShell Core 6.1 verplaatst naar .NET Core 2.1 nadat deze is [die zijn uitgebracht in mei](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), wat resulteert in een aantal verbeteringen in PowerShell, met inbegrip van:</span><span class="sxs-lookup"><span data-stu-id="05256-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="05256-110">Verbeterde prestaties (Zie [hieronder](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="05256-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="05256-111">Alpine Linux-ondersteuning (preview)</span><span class="sxs-lookup"><span data-stu-id="05256-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="05256-112">[Ondersteuning voor .NET-algemeen hulpmiddel](/dotnet/core/tools/global-tools) - komende snel naar PowerShell</span><span class="sxs-lookup"><span data-stu-id="05256-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="05256-113">Windows-compatibiliteitspakket voor .NET Core</span><span class="sxs-lookup"><span data-stu-id="05256-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="05256-114">Op Windows, het team van .NET verzonden de [Windows-compatibiliteitspakket voor .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), een set met assembly's die een aantal toevoegen verwijderd API's terug naar .NET Core in Windows.</span><span class="sxs-lookup"><span data-stu-id="05256-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="05256-115">We hebben het Windows-compatibiliteitspakket naar PowerShell Core 6.1 release toegevoegd zodat alle modules of scripts die gebruikmaken van deze API's kunnen erop vertrouwen dat ze beschikbaar worden gesteld.</span><span class="sxs-lookup"><span data-stu-id="05256-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="05256-116">De Windows-compatibiliteitspakket kunt u PowerShell Core gebruiken **meer dan 1900 cmdlets die worden geleverd met Windows 10 oktober 2018 Update en Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="05256-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="05256-117">Ondersteuning voor opname in de Whitelist</span><span class="sxs-lookup"><span data-stu-id="05256-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="05256-118">PowerShell Core 6.1 heeft pariteit met de ondersteuning van Windows PowerShell 5.1 [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) en [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) opname in de whitelist.</span><span class="sxs-lookup"><span data-stu-id="05256-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/en-us/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="05256-119">Opname in de whitelist kunt gedetailleerde controle over welke binaire bestanden mogen worden uitgevoerd gebruikt in combinatie met PowerShell [beperkte taalmodus](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span><span class="sxs-lookup"><span data-stu-id="05256-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="05256-120">Verbeterde prestaties</span><span class="sxs-lookup"><span data-stu-id="05256-120">Performance improvements</span></span>

<span data-ttu-id="05256-121">Enkele belangrijke prestatieverbeteringen doorgevoerd in PowerShell Core 6.0.</span><span class="sxs-lookup"><span data-stu-id="05256-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="05256-122">PowerShell Core 6.1 blijft voor het verbeteren van de snelheid van bepaalde bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="05256-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="05256-123">Bijvoorbeeld, `Group-Object` met 66% van heeft zijn sped:</span><span class="sxs-lookup"><span data-stu-id="05256-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="05256-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="05256-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="05256-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="05256-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="05256-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="05256-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="05256-127">Tijd (sec)</span><span class="sxs-lookup"><span data-stu-id="05256-127">Time (sec)</span></span>   | <span data-ttu-id="05256-128">25.178</span><span class="sxs-lookup"><span data-stu-id="05256-128">25.178</span></span>                 | <span data-ttu-id="05256-129">19.653</span><span class="sxs-lookup"><span data-stu-id="05256-129">19.653</span></span>              | <span data-ttu-id="05256-130">6.641</span><span class="sxs-lookup"><span data-stu-id="05256-130">6.641</span></span>               |
| <span data-ttu-id="05256-131">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="05256-131">Speed-up (%)</span></span> | <span data-ttu-id="05256-132">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="05256-132">N/A</span></span>                    | <span data-ttu-id="05256-133">21,9%</span><span class="sxs-lookup"><span data-stu-id="05256-133">21.9%</span></span>               | <span data-ttu-id="05256-134">66.2%</span><span class="sxs-lookup"><span data-stu-id="05256-134">66.2%</span></span>               |

<span data-ttu-id="05256-135">Op deze manier zijn sorteren scenario's zoals deze verbeterd door meer dan 15%:</span><span class="sxs-lookup"><span data-stu-id="05256-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="05256-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="05256-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="05256-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="05256-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="05256-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="05256-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="05256-139">Tijd (sec)</span><span class="sxs-lookup"><span data-stu-id="05256-139">Time (sec)</span></span>   | <span data-ttu-id="05256-140">12.170</span><span class="sxs-lookup"><span data-stu-id="05256-140">12.170</span></span>                 | <span data-ttu-id="05256-141">8.493</span><span class="sxs-lookup"><span data-stu-id="05256-141">8.493</span></span>               | <span data-ttu-id="05256-142">7.08</span><span class="sxs-lookup"><span data-stu-id="05256-142">7.08</span></span>                |
| <span data-ttu-id="05256-143">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="05256-143">Speed-up (%)</span></span> | <span data-ttu-id="05256-144">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="05256-144">N/A</span></span>                    | <span data-ttu-id="05256-145">30,2%</span><span class="sxs-lookup"><span data-stu-id="05256-145">30.2%</span></span>               | <span data-ttu-id="05256-146">16.6%</span><span class="sxs-lookup"><span data-stu-id="05256-146">16.6%</span></span>               |

<span data-ttu-id="05256-147">`Import-Csv` heeft ook zijn sped van aanzienlijk na een regressie vanuit Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05256-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="05256-148">Het volgende voorbeeld wordt een test CSV met 26,616 rijen en zes kolommen:</span><span class="sxs-lookup"><span data-stu-id="05256-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="05256-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="05256-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="05256-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="05256-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="05256-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="05256-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="05256-152">Tijd (sec)</span><span class="sxs-lookup"><span data-stu-id="05256-152">Time (sec)</span></span>   | <span data-ttu-id="05256-153">0.441</span><span class="sxs-lookup"><span data-stu-id="05256-153">0.441</span></span>                  | <span data-ttu-id="05256-154">1.069</span><span class="sxs-lookup"><span data-stu-id="05256-154">1.069</span></span>               | <span data-ttu-id="05256-155">0.268</span><span class="sxs-lookup"><span data-stu-id="05256-155">0.268</span></span>                  |
| <span data-ttu-id="05256-156">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="05256-156">Speed-up (%)</span></span> | <span data-ttu-id="05256-157">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="05256-157">N/A</span></span>                    | <span data-ttu-id="05256-158">-142.4%</span><span class="sxs-lookup"><span data-stu-id="05256-158">-142.4%</span></span>             | <span data-ttu-id="05256-159">74.9% (% 39.2 van WPS)</span><span class="sxs-lookup"><span data-stu-id="05256-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="05256-160">Ten slotte de conversie van JSON in `PSObject` up heeft zijn sped met meer dan 50% sinds Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05256-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="05256-161">Het volgende voorbeeld wordt een ~ 2MB test JSON-bestand:</span><span class="sxs-lookup"><span data-stu-id="05256-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="05256-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="05256-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="05256-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="05256-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="05256-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="05256-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="05256-165">Tijd (sec)</span><span class="sxs-lookup"><span data-stu-id="05256-165">Time (sec)</span></span>   | <span data-ttu-id="05256-166">0.259</span><span class="sxs-lookup"><span data-stu-id="05256-166">0.259</span></span>                  | <span data-ttu-id="05256-167">0.577</span><span class="sxs-lookup"><span data-stu-id="05256-167">0.577</span></span>               | <span data-ttu-id="05256-168">0,125</span><span class="sxs-lookup"><span data-stu-id="05256-168">0.125</span></span>                  |
| <span data-ttu-id="05256-169">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="05256-169">Speed-up (%)</span></span> | <span data-ttu-id="05256-170">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="05256-170">N/A</span></span>                    | <span data-ttu-id="05256-171">-122.8%</span><span class="sxs-lookup"><span data-stu-id="05256-171">-122.8%</span></span>             | <span data-ttu-id="05256-172">78,3% (% 51.7 van WPS)</span><span class="sxs-lookup"><span data-stu-id="05256-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a><span data-ttu-id="05256-173">Controleer `system32` voor modules die compatibel zijn postvak in op Windows</span><span class="sxs-lookup"><span data-stu-id="05256-173">Check `system32` for compatible inbox modules on Windows</span></span>

<span data-ttu-id="05256-174">Een getal van postvak in PowerShell-modules om ze te markeren als zijnde compatibel met PowerShell Core is bijgewerkt in de Windows 10 1809 update en Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="05256-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of inbox PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="05256-175">Wanneer PowerShell Core 6.1 wordt gestart, wordt deze automatisch bevatten `$windir\System32` als onderdeel van de `PSModulePath` omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="05256-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="05256-176">Echter het toont alleen modules `Get-Module` en `Import-Module` als de `CompatiblePSEdition` is gemarkeerd als compatibel met `Core`.</span><span class="sxs-lookup"><span data-stu-id="05256-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="05256-177">Mogelijk ziet u andere beschikbare modules, afhankelijk van welke functies en onderdelen zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="05256-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="05256-178">U kunt dit gedrag om weer te geven van alle modules met behulp van overschrijven de `-SkipEditionCheck` parameter overschakelen.</span><span class="sxs-lookup"><span data-stu-id="05256-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="05256-179">We hebben ook hebt toegevoegd een `PSEdition` eigenschap aan de tabeluitvoer.</span><span class="sxs-lookup"><span data-stu-id="05256-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="05256-180">Bekijk voor meer informatie over dit gedrag [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="05256-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="05256-181">Markdown-cmdlets en -rendering</span><span class="sxs-lookup"><span data-stu-id="05256-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="05256-182">Markdown is een standaard voor het maken van documenten in leesbare tekst zonder opmaak met eenvoudige opmaak die kan worden gerenderd in HTML.</span><span class="sxs-lookup"><span data-stu-id="05256-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="05256-183">We hebben enkele cmdlets toegevoegd in 6.1 waarmee u kunt converteren en Markdown-documenten in de console weergegeven met inbegrip van:</span><span class="sxs-lookup"><span data-stu-id="05256-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="05256-184">Bijvoorbeeld, `Show-Markdown` een Markdown-bestand in de console wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="05256-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Show-Markdown-voorbeeld](./images/markdown_example.png)

<span data-ttu-id="05256-186">Bekijk voor meer informatie over de werking van deze cmdlets [deze RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="05256-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="05256-187">Vlaggen voor experimentele functie</span><span class="sxs-lookup"><span data-stu-id="05256-187">Experimental feature flags</span></span>

<span data-ttu-id="05256-188">Vlaggen voor experimentele functie kunnen gebruikers in te schakelen functies die nog niet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="05256-188">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="05256-189">Deze experimentele functies worden niet ondersteund en fouten kunnen hebben.</span><span class="sxs-lookup"><span data-stu-id="05256-189">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="05256-190">U kunt meer informatie over deze functie in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="05256-190">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="05256-191">Verbeteringen voor web-cmdlet</span><span class="sxs-lookup"><span data-stu-id="05256-191">Web cmdlet improvements</span></span>

<span data-ttu-id="05256-192">Dankzij @markekraus, heel veel verbeteringen zijn aangebracht aan onze web-cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="05256-192">Thanks to @markekraus, a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="05256-193">en [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="05256-193">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="05256-194">[Pull-aanvraag #6109](https://github.com/PowerShell/PowerShell/pull/6109) -codering is ingesteld op UTF-8 voor standaard `application-json` antwoorden</span><span class="sxs-lookup"><span data-stu-id="05256-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="05256-195">[Pull-aanvraag #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parameter om toe te staan `Content-Type` kopteksten die niet compatibel zijn met standaarden</span><span class="sxs-lookup"><span data-stu-id="05256-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="05256-196">[Pull-aanvraag #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` parameter voor de ondersteuning van vereenvoudigd `multipart/form-data` ondersteunen</span><span class="sxs-lookup"><span data-stu-id="05256-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="05256-197">[Pull-aanvraag #6338](https://github.com/PowerShell/PowerShell/pull/6338) - compatibele, niet-hoofdlettergevoelige verwerken van relatie-sleutels</span><span class="sxs-lookup"><span data-stu-id="05256-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="05256-198">[Pull-aanvraag #6447](https://github.com/PowerShell/PowerShell/pull/6447) -toevoegen `-Resume` parameter voor cmdlets voor web</span><span class="sxs-lookup"><span data-stu-id="05256-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="05256-199">Verbeteringen voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="05256-199">Remoting improvements</span></span>

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a><span data-ttu-id="05256-200">PowerShell Direct probeert eerst te gebruiken PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="05256-200">PowerShell Direct tries to use PowerShell Core first</span></span>

<span data-ttu-id="05256-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is een functie van PowerShell en Hyper-V, waarmee u verbinding maken met een Hyper-V virtuele machine zonder netwerkverbinding of andere services extern beheer.</span><span class="sxs-lookup"><span data-stu-id="05256-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM without network connectivity or other remote management services.</span></span>

<span data-ttu-id="05256-202">In het verleden verbonden PowerShell Direct met behulp van het postvak in Windows PowerShell-exemplaar op de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="05256-202">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the VM.</span></span>
<span data-ttu-id="05256-203">Nu, PowerShell Direct eerst verbinding probeert te maken met behulp van de beschikbare `pwsh.exe` op de `PATH` omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="05256-203">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="05256-204">Als `pwsh.exe` is niet beschikbaar is, PowerShell Direct terugvalt voor het gebruik van `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="05256-204">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="05256-205">`Enable-PSRemoting` nu maakt u afzonderlijke externe eindpunten voor de preview-versies</span><span class="sxs-lookup"><span data-stu-id="05256-205">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="05256-206">`Enable-PSRemoting` u maakt nu twee externe communicatie van sessieconfiguraties:</span><span class="sxs-lookup"><span data-stu-id="05256-206">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="05256-207">Een voor de belangrijkste versie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05256-207">One for the major version of PowerShell.</span></span> <span data-ttu-id="05256-208">Bijvoorbeeld,`PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="05256-208">For example,`PowerShell.6`.</span></span> <span data-ttu-id="05256-209">Dit eindpunt dat kan worden gebruikt voor updates van de secundaire versie als de sessieconfiguratie 'systeembrede' PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="05256-209">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="05256-210">Een specifieke versies sessieconfiguratie, bijvoorbeeld: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="05256-210">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="05256-211">Dit gedrag is handig als u wilt dat meerdere versies van PowerShell 6 geïnstalleerd en toegankelijk is op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="05256-211">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="05256-212">Bovendien preview-versies van PowerShell nu toegang tot hun eigen remoting sessieconfiguraties nadat de `Enable-PSRemoting` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="05256-212">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="05256-213">De uitvoer kan afwijken als u WinRM voordat u dit nog niet hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="05256-213">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="05256-214">Vervolgens ziet u afzonderlijke PowerShell-sessie-configuraties voor de Preview-versie en stabiel builds van PowerShell 6, en voor elke specifieke versie.</span><span class="sxs-lookup"><span data-stu-id="05256-214">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="05256-215">`user@host:port` syntaxis die worden ondersteund voor SSH</span><span class="sxs-lookup"><span data-stu-id="05256-215">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="05256-216">SSH clients ondersteunen meestal een verbindingsreeks in de indeling `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="05256-216">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="05256-217">Met de toevoeging van SSH als protocol voor externe communicatie van PowerShell, is er ondersteuning toegevoegd voor deze indeling van de verbindingsreeks:</span><span class="sxs-lookup"><span data-stu-id="05256-217">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="05256-218">MSI-optie voor het toevoegen van contextmenu explorer-shell op Windows</span><span class="sxs-lookup"><span data-stu-id="05256-218">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="05256-219">Dankzij @bergmeister, nu u in het contextmenu op Windows kunt.</span><span class="sxs-lookup"><span data-stu-id="05256-219">Thanks to @bergmeister, now you can enable a context menu on Windows.</span></span> <span data-ttu-id="05256-220">U kunt nu uw systeembrede-installatie van PowerShell 6.1 openen vanuit een willekeurige map in Windows Explorer:</span><span class="sxs-lookup"><span data-stu-id="05256-220">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Shell-contextmenu voor PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="05256-222">Goodies</span><span class="sxs-lookup"><span data-stu-id="05256-222">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="05256-223">"Als Administrator uitvoeren' in de lijst met Windows snelkoppeling naar de landingspagina</span><span class="sxs-lookup"><span data-stu-id="05256-223">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="05256-224">Dankzij @bergmeister, van de snelkoppeling van de PowerShell Core jump lijst bevat nu 'Als Administrator uitvoeren':</span><span class="sxs-lookup"><span data-stu-id="05256-224">Thanks to @bergmeister, the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Uitvoeren als administrator in de lijst met PowerShell 6 landingspagina](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="05256-226">`cd -` terug naar de vorige map</span><span class="sxs-lookup"><span data-stu-id="05256-226">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="05256-227">Of op Linux:</span><span class="sxs-lookup"><span data-stu-id="05256-227">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="05256-228">Bovendien `cd --` wordt gewijzigd in `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="05256-228">Also, `cd --` changes to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="05256-229">Dankzij @iSazonov, wordt de [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet heeft zijn overgezet naar PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="05256-229">Thanks to @iSazonov, the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="05256-230">`Update-Help` Als niet-beheerder</span><span class="sxs-lookup"><span data-stu-id="05256-230">`Update-Help` as non-admin</span></span>

<span data-ttu-id="05256-231">Op veler verzoek `Update-Help` langer moet worden uitgevoerd als beheerder.</span><span class="sxs-lookup"><span data-stu-id="05256-231">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="05256-232">`Update-Help` opslaan van Help-informatie naar een map binnen het bereik van gebruiker is nu standaard.</span><span class="sxs-lookup"><span data-stu-id="05256-232">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="05256-233">Nieuwe methoden/eigenschappen op `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="05256-233">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="05256-234">Dankzij @iSazonov, hebben we nieuwe methoden en eigenschappen die moeten toegevoegd `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="05256-234">Thanks to @iSazonov, we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="05256-235">`PSCustomObject` bevat nu een `Count` / `Length` eigenschap waarmee het aantal items.</span><span class="sxs-lookup"><span data-stu-id="05256-235">`PSCustomObject` now includes a `Count`/`Length` property that gives the number of items.</span></span>

<span data-ttu-id="05256-236">Deze voorbeelden retourneren `2` als het aantal `PSCustomObjects` in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="05256-236">Both of these examples return `2` as the number of `PSCustomObjects` in the collection.</span></span>

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

<span data-ttu-id="05256-237">Deze taak bevat ook `ForEach` en `Where` methoden waarmee u kunt werken en te filteren op `PSCustomObject` items:</span><span class="sxs-lookup"><span data-stu-id="05256-237">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

<span data-ttu-id="05256-238">Dankzij @SimonWahlin, hebben we toegevoegd aan de `-Not` parameter `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="05256-238">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="05256-239">U kunt nu een object in de pijplijn voor de niet-aanwezigheid van een eigenschap of een eigenschapswaarde van null/leeg filteren.</span><span class="sxs-lookup"><span data-stu-id="05256-239">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="05256-240">Met deze opdracht retourneert bijvoorbeeld alle services die niet geen afhankelijke services gedefinieerd zijn:</span><span class="sxs-lookup"><span data-stu-id="05256-240">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="05256-241">`New-ModuleManifest` Hiermee maakt u een stuklijst zonder UTF-8-document</span><span class="sxs-lookup"><span data-stu-id="05256-241">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="05256-242">Opgegeven onze verplaatsen naar stuklijst zonder UTF-8 in PowerShell 6.0, we hebben bijgewerkt de `New-ModuleManifest` cmdlet om een document stuklijst zonder UTF-8 in plaats van een UTF-16 een te maken.</span><span class="sxs-lookup"><span data-stu-id="05256-242">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="05256-243">Conversies van PSMethod gemachtigde</span><span class="sxs-lookup"><span data-stu-id="05256-243">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="05256-244">Dankzij @powercode, we ondersteunen nu de conversie van een `PSMethod` in een gemachtigde.</span><span class="sxs-lookup"><span data-stu-id="05256-244">Thanks to @powercode, we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="05256-245">Hiermee kunt u voor handelingen zoals doorgeven `PSMethod` `[M]::DoubleStrLen` als de waarde van een gemachtigde in `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="05256-245">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="05256-246">Bekijk voor meer informatie over deze wijziging [pull-aanvraag #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="05256-246">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="05256-247">Standaarddeviatie in `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="05256-247">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="05256-248">Dankzij @CloudyDino, hebben we toegevoegd aan een `StandardDeviation` eigenschap `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="05256-248">Thanks to @CloudyDino, we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="05256-249">Dankzij @maybe-hello-world, `Get-PfxCertificate` heeft nu de `Password` parameter, waarbij een `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="05256-249">Thanks to @maybe-hello-world, `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="05256-250">Hiermee kunt u niet-interactief gebruiken:</span><span class="sxs-lookup"><span data-stu-id="05256-250">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="05256-251">Het verwijderen van de `more` functie</span><span class="sxs-lookup"><span data-stu-id="05256-251">Removal of the `more` function</span></span>

<span data-ttu-id="05256-252">In het verleden PowerShell een functie in Windows met de naam verzonden `more` die verpakt `more.com`.</span><span class="sxs-lookup"><span data-stu-id="05256-252">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="05256-253">Deze functie is nu verwijderd.</span><span class="sxs-lookup"><span data-stu-id="05256-253">That function has now been removed.</span></span>

<span data-ttu-id="05256-254">Ook de `help` functie gewijzigd in het gebruik van `more.com` op Windows of van het systeem standaard pager is opgegeven door `$env:PAGER` op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="05256-254">Also the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="05256-255">`cd DriveName:` retourneert nu gebruikers aan de huidige werkmap op het desbetreffende station</span><span class="sxs-lookup"><span data-stu-id="05256-255">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="05256-256">Eerder, met behulp van `Set-Location` of `cd` om terug te keren naar een PSDrive gebruikers verzonden naar de standaardlocatie voor dat station.</span><span class="sxs-lookup"><span data-stu-id="05256-256">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="05256-257">Dankzij @mcbobke, gebruikers worden nu verzonden naar de laatste bekende huidige werkmap voor deze sessie.</span><span class="sxs-lookup"><span data-stu-id="05256-257">Thanks to @mcbobke, users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="05256-258">Windows PowerShell type accelerators</span><span class="sxs-lookup"><span data-stu-id="05256-258">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="05256-259">In Windows PowerShell, hebben we het volgende type accelerators zodat het eenvoudiger om te werken met hun respectieve gegevenstypen opgenomen:</span><span class="sxs-lookup"><span data-stu-id="05256-259">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="05256-260">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="05256-260">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="05256-261">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="05256-261">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="05256-262">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="05256-262">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="05256-263">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="05256-263">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="05256-264">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="05256-264">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="05256-265">Deze accelerators type niet zijn opgenomen in PowerShell 6, maar zijn toegevoegd aan die wordt uitgevoerd op Windows PowerShell-6.1.</span><span class="sxs-lookup"><span data-stu-id="05256-265">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="05256-266">Deze typen zijn nuttig bij het maken van eenvoudig AD en WMI-objecten.</span><span class="sxs-lookup"><span data-stu-id="05256-266">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="05256-267">U kunt bijvoorbeeld een query met behulp van LDAP:</span><span class="sxs-lookup"><span data-stu-id="05256-267">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="05256-268">Deze voorbeelden maken een Win32_OperatingSystem CIM-object:</span><span class="sxs-lookup"><span data-stu-id="05256-268">Both of these examples create a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="05256-269">`-lp` alias voor alle `-LiteralPath` parameters</span><span class="sxs-lookup"><span data-stu-id="05256-269">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="05256-270">Dankzij @kvprasoon, we hebben nu een parameteralias `-lp` voor alle de ingebouwde PowerShell-cmdlets die u hebt een `-LiteralPath` parameter.</span><span class="sxs-lookup"><span data-stu-id="05256-270">Thanks to @kvprasoon, we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="05256-271">Belangrijke wijzigingen</span><span class="sxs-lookup"><span data-stu-id="05256-271">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="05256-272">MSI-gebaseerde installatiepaden op Windows</span><span class="sxs-lookup"><span data-stu-id="05256-272">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="05256-273">Op Windows, is het MSI-pakket nu wordt geïnstalleerd in het volgende pad:</span><span class="sxs-lookup"><span data-stu-id="05256-273">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="05256-274">`$env:ProgramFiles\PowerShell\6\` voor de installatie van de stabiele van 6.x</span><span class="sxs-lookup"><span data-stu-id="05256-274">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="05256-275">`$env:ProgramFiles\PowerShell\6-preview\` voor de installatie van de Preview-versie van 6.x</span><span class="sxs-lookup"><span data-stu-id="05256-275">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="05256-276">Deze wijziging zorgt ervoor dat PowerShell Core bijgewerkt/afgehandeld door de Microsoft Update worden kunnen.</span><span class="sxs-lookup"><span data-stu-id="05256-276">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="05256-277">Bekijk voor meer informatie, [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="05256-277">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="05256-278">Telemetrie kan alleen worden uitgeschakeld met een omgevingsvariabele</span><span class="sxs-lookup"><span data-stu-id="05256-278">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="05256-279">PowerShell Core worden standaard telemetriegegevens naar Microsoft verzonden wanneer deze wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="05256-279">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="05256-280">De gegevens bevatten de naam van besturingssysteem, de versie van het besturingssysteem en de PowerShell-versie.</span><span class="sxs-lookup"><span data-stu-id="05256-280">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="05256-281">Deze gegevens kan we meer inzicht in de omgevingen waar PowerShell wordt gebruikt en kan we nieuwe functies en oplossingen prioriteren.</span><span class="sxs-lookup"><span data-stu-id="05256-281">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="05256-282">Als u wilt zich afmelden deze telemetrische gegevens, stel de omgevingsvariabele `POWERSHELL_TELEMETRY_OPTOUT` naar `true`, `yes`, of `1`.</span><span class="sxs-lookup"><span data-stu-id="05256-282">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="05256-283">We bieden geen ondersteuning voor het verwijderen van het bestand `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` telemetrie uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="05256-283">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="05256-284">Basisverificatie toegestaan via HTTP in PowerShell voor externe toegang voor Unix-platforms</span><span class="sxs-lookup"><span data-stu-id="05256-284">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="05256-285">Om te voorkomen dat het gebruik van niet-versleuteld verkeer, nu vereist gebruik van NTLM/Negotiate- of HTTPS PowerShell voor externe toegang op Unix-platforms.</span><span class="sxs-lookup"><span data-stu-id="05256-285">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="05256-286">Bekijk voor meer informatie over deze wijzigingen [pull-aanvraag #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span><span class="sxs-lookup"><span data-stu-id="05256-286">For more information on these changes, check out [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="05256-287">Verwijderd `VisualBasic` als een ondersteunde taal in Add-Type</span><span class="sxs-lookup"><span data-stu-id="05256-287">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="05256-288">In het verleden kon u compileren Visual Basic met behulp van code de `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05256-288">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="05256-289">Visual Basic is die zelden worden gebruikt met `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="05256-289">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="05256-290">We hebben verwijderd deze functie om de grootte van PowerShell te verkleinen.</span><span class="sxs-lookup"><span data-stu-id="05256-290">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="05256-291">Het gebruik van opgeschoond `CommandTypes.Workflow` en `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="05256-291">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="05256-292">Bekijk voor meer informatie over deze wijzigingen [pull-aanvraag #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="05256-292">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>
