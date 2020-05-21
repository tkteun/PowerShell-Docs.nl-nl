---
title: Wat is er nieuw in Power shell Core 6,1
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,1
ms.date: 09/13/2018
ms.openlocfilehash: 070ecb871003487e2f1ff7b0d56c44c562acaaf8
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565077"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="acae7-103">Wat is er nieuw in Power shell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="acae7-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="acae7-104">Hieronder vindt u een selectie van een aantal belang rijke nieuwe functies en wijzigingen die zijn geïntroduceerd in Power shell Core 6,1.</span><span class="sxs-lookup"><span data-stu-id="acae7-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="acae7-105">Er **zijn ook talloze** ' saaie dingen ' die Power shell sneller en stabieler maken (plus veel problemen met oplossingen).</span><span class="sxs-lookup"><span data-stu-id="acae7-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span> <span data-ttu-id="acae7-106">Bekijk onze [wijzigingen logboek op github](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)voor een volledige lijst met wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="acae7-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="acae7-107">En we noemen we een aantal van de onderstaande namen, hartelijk dank voor [alle mede werkers van de Community](https://github.com/PowerShell/PowerShell/graphs/contributors) die deze release hebben gemaakt.</span><span class="sxs-lookup"><span data-stu-id="acae7-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="acae7-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="acae7-108">.NET Core 2.1</span></span>

<span data-ttu-id="acae7-109">Power shell Core 6,1 is verplaatst naar .NET Core 2,1 nadat deze is [uitgebracht in mei](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), wat resulteert in een aantal verbeteringen in Power shell, met inbegrip van:</span><span class="sxs-lookup"><span data-stu-id="acae7-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="acae7-110">prestatie verbeteringen (Zie [hieronder](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="acae7-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="acae7-111">Ondersteuning voor Alpine Linux (preview-versie)</span><span class="sxs-lookup"><span data-stu-id="acae7-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="acae7-112">[Ondersteuning voor algemeen hulp programma van .net](/dotnet/core/tools/global-tools) -binnenkort beschikbaar in Power shell</span><span class="sxs-lookup"><span data-stu-id="acae7-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="acae7-113">Windows-compatibiliteits pakket voor .NET core</span><span class="sxs-lookup"><span data-stu-id="acae7-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="acae7-114">In Windows leverde het .NET-team het [Windows-compatibiliteits pakket voor .net core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), een set assembly's die een aantal verwijderde api's toevoegen aan .net core in Windows.</span><span class="sxs-lookup"><span data-stu-id="acae7-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="acae7-115">We hebben het Windows-compatibiliteits pakket toegevoegd aan Power shell Core 6,1-release, zodat alle modules of scripts die gebruikmaken van deze Api's, kunnen worden gebruikt om ze beschikbaar te stellen.</span><span class="sxs-lookup"><span data-stu-id="acae7-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="acae7-116">Met het Windows-compatibiliteits pakket kan Power shell core gebruikmaken **van meer dan 1900 cmdlets die worden geleverd met Windows 10 oktober 2018 update en Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="acae7-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="acae7-117">Ondersteuning voor White List van toepassingen</span><span class="sxs-lookup"><span data-stu-id="acae7-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="acae7-118">Power shell Core 6,1 heeft pariteit met Windows Power shell 5,1 met ondersteuning voor [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) en de Application white list van [device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) .</span><span class="sxs-lookup"><span data-stu-id="acae7-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span> <span data-ttu-id="acae7-119">Met Application white list kunt u nauw keurig bepalen welke binaire bestanden mogen worden uitgevoerd met de [modus](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/)voor de beperkte Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="acae7-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="acae7-120">Prestatieverbeteringen</span><span class="sxs-lookup"><span data-stu-id="acae7-120">Performance improvements</span></span>

<span data-ttu-id="acae7-121">Power shell Core 6,0 heeft enkele belang rijke prestatie verbeteringen aangebracht.</span><span class="sxs-lookup"><span data-stu-id="acae7-121">PowerShell Core 6.0 made some significant performance improvements.</span></span> <span data-ttu-id="acae7-122">Power shell Core 6,1 blijft de snelheid van bepaalde bewerkingen verbeteren.</span><span class="sxs-lookup"><span data-stu-id="acae7-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="acae7-123">`Group-Object`Is bijvoorbeeld sped %66%:</span><span class="sxs-lookup"><span data-stu-id="acae7-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="acae7-124">Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="acae7-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="acae7-125">Power shell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="acae7-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="acae7-126">Power shell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="acae7-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="acae7-127">Tijd (SEC)</span><span class="sxs-lookup"><span data-stu-id="acae7-127">Time (sec)</span></span>   | <span data-ttu-id="acae7-128">25,178</span><span class="sxs-lookup"><span data-stu-id="acae7-128">25.178</span></span>                 | <span data-ttu-id="acae7-129">19,653</span><span class="sxs-lookup"><span data-stu-id="acae7-129">19.653</span></span>              | <span data-ttu-id="acae7-130">6,641</span><span class="sxs-lookup"><span data-stu-id="acae7-130">6.641</span></span>               |
| <span data-ttu-id="acae7-131">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="acae7-131">Speed-up (%)</span></span> | <span data-ttu-id="acae7-132">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="acae7-132">N/A</span></span>                    | <span data-ttu-id="acae7-133">21,9%</span><span class="sxs-lookup"><span data-stu-id="acae7-133">21.9%</span></span>               | <span data-ttu-id="acae7-134">66,2%</span><span class="sxs-lookup"><span data-stu-id="acae7-134">66.2%</span></span>               |

<span data-ttu-id="acae7-135">Op dezelfde manier kunnen sorterings scenario's zoals deze worden verbeterd met meer dan 15%:</span><span class="sxs-lookup"><span data-stu-id="acae7-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="acae7-136">Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="acae7-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="acae7-137">Power shell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="acae7-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="acae7-138">Power shell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="acae7-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="acae7-139">Tijd (SEC)</span><span class="sxs-lookup"><span data-stu-id="acae7-139">Time (sec)</span></span>   | <span data-ttu-id="acae7-140">12,170</span><span class="sxs-lookup"><span data-stu-id="acae7-140">12.170</span></span>                 | <span data-ttu-id="acae7-141">8,493</span><span class="sxs-lookup"><span data-stu-id="acae7-141">8.493</span></span>               | <span data-ttu-id="acae7-142">7,08</span><span class="sxs-lookup"><span data-stu-id="acae7-142">7.08</span></span>                |
| <span data-ttu-id="acae7-143">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="acae7-143">Speed-up (%)</span></span> | <span data-ttu-id="acae7-144">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="acae7-144">N/A</span></span>                    | <span data-ttu-id="acae7-145">30,2%</span><span class="sxs-lookup"><span data-stu-id="acae7-145">30.2%</span></span>               | <span data-ttu-id="acae7-146">16,6%</span><span class="sxs-lookup"><span data-stu-id="acae7-146">16.6%</span></span>               |

<span data-ttu-id="acae7-147">`Import-Csv`is ook aanzienlijk sped na een regressie van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="acae7-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="acae7-148">In het volgende voor beeld wordt een CSV van de test met 26.616 rijen en zes kolommen gebruikt:</span><span class="sxs-lookup"><span data-stu-id="acae7-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="acae7-149">Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="acae7-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="acae7-150">Power shell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="acae7-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="acae7-151">Power shell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="acae7-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="acae7-152">Tijd (SEC)</span><span class="sxs-lookup"><span data-stu-id="acae7-152">Time (sec)</span></span>   | <span data-ttu-id="acae7-153">0,441</span><span class="sxs-lookup"><span data-stu-id="acae7-153">0.441</span></span>                  | <span data-ttu-id="acae7-154">1,069</span><span class="sxs-lookup"><span data-stu-id="acae7-154">1.069</span></span>               | <span data-ttu-id="acae7-155">0,268</span><span class="sxs-lookup"><span data-stu-id="acae7-155">0.268</span></span>                  |
| <span data-ttu-id="acae7-156">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="acae7-156">Speed-up (%)</span></span> | <span data-ttu-id="acae7-157">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="acae7-157">N/A</span></span>                    | <span data-ttu-id="acae7-158">-142,4%</span><span class="sxs-lookup"><span data-stu-id="acae7-158">-142.4%</span></span>             | <span data-ttu-id="acae7-159">74,9% (39,2% van WPS)</span><span class="sxs-lookup"><span data-stu-id="acae7-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="acae7-160">Ten slotte is de conversie van JSON into `PSObject` sped meer dan 50% sinds Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="acae7-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="acae7-161">In het volgende voor beeld wordt een JSON-test bestand van ~ 2 MB gebruikt:</span><span class="sxs-lookup"><span data-stu-id="acae7-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="acae7-162">Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="acae7-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="acae7-163">Power shell Core 6,0</span><span class="sxs-lookup"><span data-stu-id="acae7-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="acae7-164">Power shell Core 6,1</span><span class="sxs-lookup"><span data-stu-id="acae7-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="acae7-165">Tijd (SEC)</span><span class="sxs-lookup"><span data-stu-id="acae7-165">Time (sec)</span></span>   | <span data-ttu-id="acae7-166">0,259</span><span class="sxs-lookup"><span data-stu-id="acae7-166">0.259</span></span>                  | <span data-ttu-id="acae7-167">0,577</span><span class="sxs-lookup"><span data-stu-id="acae7-167">0.577</span></span>               | <span data-ttu-id="acae7-168">0,125</span><span class="sxs-lookup"><span data-stu-id="acae7-168">0.125</span></span>                  |
| <span data-ttu-id="acae7-169">Versnellen (%)</span><span class="sxs-lookup"><span data-stu-id="acae7-169">Speed-up (%)</span></span> | <span data-ttu-id="acae7-170">N.v.t.</span><span class="sxs-lookup"><span data-stu-id="acae7-170">N/A</span></span>                    | <span data-ttu-id="acae7-171">-122,8%</span><span class="sxs-lookup"><span data-stu-id="acae7-171">-122.8%</span></span>             | <span data-ttu-id="acae7-172">78,3% (51,7% van WPS)</span><span class="sxs-lookup"><span data-stu-id="acae7-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="acae7-173">Controleren `system32` op compatibele modules in Windows</span><span class="sxs-lookup"><span data-stu-id="acae7-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="acae7-174">In de Windows 10 1809-update en Windows Server 2019 hebben we een aantal Power shell-modules bijgewerkt om ze te markeren als compatibel met Power shell core.</span><span class="sxs-lookup"><span data-stu-id="acae7-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="acae7-175">Wanneer Power shell Core 6,1 wordt gestart, wordt het automatisch opgenomen `$windir\System32` als onderdeel van de `PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="acae7-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span> <span data-ttu-id="acae7-176">Er worden echter alleen modules beschikbaar gemaakt `Get-Module` en als deze zijn `Import-Module` `CompatiblePSEdition` gemarkeerd als compatibel met `Core` .</span><span class="sxs-lookup"><span data-stu-id="acae7-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>

```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="acae7-177">U ziet mogelijk verschillende beschik bare modules, afhankelijk van de functies en onderdelen die zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="acae7-177">You may see different available modules depending on what roles and features are installed.</span></span>

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

<span data-ttu-id="acae7-178">U kunt dit gedrag negeren om alle modules weer te geven met behulp van de `-SkipEditionCheck` para meter switch.</span><span class="sxs-lookup"><span data-stu-id="acae7-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="acae7-179">Er is ook een `PSEdition` eigenschap toegevoegd aan de tabel uitvoer.</span><span class="sxs-lookup"><span data-stu-id="acae7-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="acae7-180">Raadpleeg [Power shell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)voor meer informatie over dit gedrag.</span><span class="sxs-lookup"><span data-stu-id="acae7-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="acae7-181">Cmdlets en rendering weer geven</span><span class="sxs-lookup"><span data-stu-id="acae7-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="acae7-182">Prijs verlaging is een standaard voor het maken van Lees bare tekst documenten met basis opmaak die in HTML kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="acae7-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="acae7-183">Er zijn enkele cmdlets toegevoegd in 6,1 waarmee u de verkortings documenten kunt converteren en weer geven in de-console, met inbegrip van:</span><span class="sxs-lookup"><span data-stu-id="acae7-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="acae7-184">Een voor beeld `Show-Markdown` : Hiermee wordt een bestand met een prijs opgave in de-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="acae7-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Voor beeld van korting weer geven](media/What-s-New-in-PowerShell-Core-61/markdown_example.png)

<span data-ttu-id="acae7-186">Bekijk [deze rfc's](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)voor meer informatie over de werking van deze cmdlets.</span><span class="sxs-lookup"><span data-stu-id="acae7-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="acae7-187">Experimentele functie vlaggen</span><span class="sxs-lookup"><span data-stu-id="acae7-187">Experimental feature flags</span></span>

<span data-ttu-id="acae7-188">We hebben ondersteuning voor [experimentele functies][]ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="acae7-188">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="acae7-189">Hierdoor kunnen Power shell-ontwikkel aars nieuwe functies leveren en feedback ontvangen voordat het ontwerp is voltooid.</span><span class="sxs-lookup"><span data-stu-id="acae7-189">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="acae7-190">Op deze manier wordt voor komen dat wijzigingen worden aangebracht naarmate het ontwerp wordt ontwikkeld.</span><span class="sxs-lookup"><span data-stu-id="acae7-190">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="acae7-191">Gebruik `Get-ExperimentalFeature` om een lijst met beschik bare experimentele functies op te halen.</span><span class="sxs-lookup"><span data-stu-id="acae7-191">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="acae7-192">U kunt deze functies in-of uitschakelen met `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature` .</span><span class="sxs-lookup"><span data-stu-id="acae7-192">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="acae7-193">Meer informatie over deze functie vindt u in [Power shell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="acae7-193">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="acae7-194">Verbeteringen voor web-cmdlets</span><span class="sxs-lookup"><span data-stu-id="acae7-194">Web cmdlet improvements</span></span>

<span data-ttu-id="acae7-195">Dankzij [@markekraus](https://github.com/markekraus) onze web-cmdlets hebt u een volledig Slew van verbeteringen aangebracht:[`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="acae7-195">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="acae7-196">en [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod) .</span><span class="sxs-lookup"><span data-stu-id="acae7-196">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="acae7-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) : standaard codering ingesteld op UTF-8 voor `application-json` antwoorden</span><span class="sxs-lookup"><span data-stu-id="acae7-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="acae7-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation`para meter voor het toestaan van `Content-Type` headers die niet compatibel zijn met standaarden</span><span class="sxs-lookup"><span data-stu-id="acae7-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="acae7-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form`para meter ter ondersteuning van vereenvoudigde `multipart/form-data` ondersteuning</span><span class="sxs-lookup"><span data-stu-id="acae7-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="acae7-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) -compatibele, hoofdletter gevoelige verwerking van relatie sleutels</span><span class="sxs-lookup"><span data-stu-id="acae7-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="acae7-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - `-Resume` para meter voor web-cmdlets toevoegen</span><span class="sxs-lookup"><span data-stu-id="acae7-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="acae7-202">Externe verbeteringen</span><span class="sxs-lookup"><span data-stu-id="acae7-202">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="acae7-203">Power shell direct voor containers probeert eerst Power shell core te gebruiken</span><span class="sxs-lookup"><span data-stu-id="acae7-203">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="acae7-204">[Power shell direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is een functie van Power shell en hyper-v waarmee u verbinding kunt maken met een hyper-v-VM of-container zonder netwerk verbinding of andere services voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="acae7-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="acae7-205">In het verleden is Power shell direct verbonden via de Windows Power shell-instantie postvak in in de container.</span><span class="sxs-lookup"><span data-stu-id="acae7-205">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span> <span data-ttu-id="acae7-206">Nu probeert Power shell direct eerst verbinding te maken met behulp van de beschik bare `pwsh.exe` `PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="acae7-206">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span> <span data-ttu-id="acae7-207">Als deze `pwsh.exe` niet beschikbaar is, valt Power shell direct terug naar het gebruik `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="acae7-207">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="acae7-208">`Enable-PSRemoting`maakt nu afzonderlijke externe eind punten voor Preview-versies</span><span class="sxs-lookup"><span data-stu-id="acae7-208">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="acae7-209">`Enable-PSRemoting`maakt nu twee externe sessie configuraties:</span><span class="sxs-lookup"><span data-stu-id="acae7-209">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="acae7-210">Een voor de primaire versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="acae7-210">One for the major version of PowerShell.</span></span> <span data-ttu-id="acae7-211">Bijvoorbeeld `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="acae7-211">For example, `PowerShell.6`.</span></span> <span data-ttu-id="acae7-212">Dit eind punt dat kan worden verzorgd voor alle secundaire versie-updates als de ' systeembrede ' configuratie van de Power shell 6-sessie</span><span class="sxs-lookup"><span data-stu-id="acae7-212">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="acae7-213">Een versie-specifieke sessie configuratie, bijvoorbeeld:`PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="acae7-213">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="acae7-214">Dit is handig als u wilt dat er meerdere Power shell 6-versies op dezelfde computer zijn geïnstalleerd en toegankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="acae7-214">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="acae7-215">Daarnaast krijgen Preview-versies van Power shell nu hun eigen externe sessie configuraties na het uitvoeren van de `Enable-PSRemoting` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="acae7-215">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="acae7-216">Uw uitvoer kan verschillen als u WinRM nog niet hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="acae7-216">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="acae7-217">Vervolgens kunt u afzonderlijke Power shell-sessie configuraties bekijken voor de preview-versie en stabiele builds van Power shell 6, en voor elke specifieke versies.</span><span class="sxs-lookup"><span data-stu-id="acae7-217">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

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

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="acae7-218">`user@host:port`syntaxis die wordt ondersteund voor SSH</span><span class="sxs-lookup"><span data-stu-id="acae7-218">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="acae7-219">SSH-clients ondersteunen doorgaans een connection string in de indeling `user@host:port` .</span><span class="sxs-lookup"><span data-stu-id="acae7-219">SSH clients typically support a connection string in the format `user@host:port`.</span></span> <span data-ttu-id="acae7-220">Met het toevoegen van SSH als protocol voor externe communicatie met Power Shell hebben we ondersteuning toegevoegd voor deze indeling van connection string:</span><span class="sxs-lookup"><span data-stu-id="acae7-220">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="acae7-221">MSI-optie om het context menu van de Explorer-Shell toe te voegen in Windows</span><span class="sxs-lookup"><span data-stu-id="acae7-221">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="acae7-222">Bedankt [@bergmeister](https://github.com/bergmeister) , u kunt nu een context menu inschakelen in Windows.</span><span class="sxs-lookup"><span data-stu-id="acae7-222">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="acae7-223">U kunt nu de systeembrede installatie van Power shell 6,1 openen vanuit een wille keurige map in Windows Verkenner:</span><span class="sxs-lookup"><span data-stu-id="acae7-223">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Context menu van shell voor Power shell 6](media/What-s-New-in-PowerShell-Core-61/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="acae7-225">Goodies</span><span class="sxs-lookup"><span data-stu-id="acae7-225">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="acae7-226">"Als administrator uitvoeren" in de Jump List van Windows-snelkoppelingen</span><span class="sxs-lookup"><span data-stu-id="acae7-226">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="acae7-227">Hartelijk dank voor [@bergmeister](https://github.com/bergmeister) de Jump List van de Power shell core-snelkoppeling bevat nu "als administrator uitvoeren":</span><span class="sxs-lookup"><span data-stu-id="acae7-227">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Als administrator uitvoeren in de Power shell 6 Jump List](media/What-s-New-in-PowerShell-Core-61/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="acae7-229">`cd -`Hiermee wordt naar de vorige map gekeerd</span><span class="sxs-lookup"><span data-stu-id="acae7-229">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="acae7-230">Of op Linux:</span><span class="sxs-lookup"><span data-stu-id="acae7-230">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="acae7-231">`cd`En `cd --` Wijzig naar `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="acae7-231">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="acae7-232">Hartelijk dank voor [@iSazonov](https://github.com/iSazonov) de [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet is geporteerd naar Power shell core.</span><span class="sxs-lookup"><span data-stu-id="acae7-232">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="acae7-233">`Update-Help`Als niet-beheerder</span><span class="sxs-lookup"><span data-stu-id="acae7-233">`Update-Help` as non-admin</span></span>

<span data-ttu-id="acae7-234">Op de populaire vraag `Update-Help` hoeft u niet meer te worden uitgevoerd als beheerder.</span><span class="sxs-lookup"><span data-stu-id="acae7-234">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span> <span data-ttu-id="acae7-235">`Update-Help`de standaard instelling is dat de Help-informatie wordt opgeslagen in een map die door de gebruiker is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="acae7-235">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="acae7-236">Nieuwe methoden/eigenschappen op`PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="acae7-236">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="acae7-237">Hartelijk dank voor het [@iSazonov](https://github.com/iSazonov) toevoegen van nieuwe methoden en eigenschappen aan `PSCustomObject` .</span><span class="sxs-lookup"><span data-stu-id="acae7-237">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span> <span data-ttu-id="acae7-238">`PSCustomObject`bevat nu een `Count` / `Length` eigenschap zoals andere objecten.</span><span class="sxs-lookup"><span data-stu-id="acae7-238">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="acae7-239">Dit werk omvat ook `ForEach` en `Where` methoden waarmee u items kunt gebruiken en filteren `PSCustomObject` :</span><span class="sxs-lookup"><span data-stu-id="acae7-239">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="acae7-240">Bedankt voor @SimonWahlin het toevoegen van de `-Not` para meter aan `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="acae7-240">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span> <span data-ttu-id="acae7-241">U kunt nu een object filteren in de pijp lijn voor het niet bestaan van een eigenschap, of een eigenschaps waarde van Null/empty.</span><span class="sxs-lookup"><span data-stu-id="acae7-241">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="acae7-242">Met deze opdracht worden bijvoorbeeld alle services geretourneerd waarvoor geen afhankelijke services zijn gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="acae7-242">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="acae7-243">`New-ModuleManifest`Hiermee maakt u een stuk lijst zonder UTF-8-document</span><span class="sxs-lookup"><span data-stu-id="acae7-243">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="acae7-244">Gezien onze overgang naar een stuk lijst-minder UTF-8 in Power shell 6,0, hebben we de `New-ModuleManifest` cmdlet bijgewerkt om een stuk lijst van minder dan UTF-8-documenten te maken in plaats van een UTF-16 1.</span><span class="sxs-lookup"><span data-stu-id="acae7-244">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="acae7-245">Conversies van PSMethod die moeten worden gedelegeerd</span><span class="sxs-lookup"><span data-stu-id="acae7-245">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="acae7-246">Hartelijk dank voor [@powercode](https://github.com/powercode) het ondersteunen van de conversie van een `PSMethod` naar een gemachtigde.</span><span class="sxs-lookup"><span data-stu-id="acae7-246">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span> <span data-ttu-id="acae7-247">Op die manier kunt u dingen doen `PSMethod` `[M]::DoubleStrLen` als een gemachtigde waarde in `[M]::AggregateString` :</span><span class="sxs-lookup"><span data-stu-id="acae7-247">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

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

<span data-ttu-id="acae7-248">Bekijk [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)voor meer informatie over deze wijziging.</span><span class="sxs-lookup"><span data-stu-id="acae7-248">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="acae7-249">Standaard afwijking in`Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="acae7-249">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="acae7-250">Hartelijk dank voor [@CloudyDino](https://github.com/CloudyDino) het toevoegen van een `StandardDeviation` eigenschap aan `Measure-Object` :</span><span class="sxs-lookup"><span data-stu-id="acae7-250">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

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

<span data-ttu-id="acae7-251">Bedankt, [@maybe-hello-world](https://github.com/maybe-hello-world) `Get-PfxCertificate` nu heeft de `Password` para meter, die wordt gebruikt voor `SecureString` .</span><span class="sxs-lookup"><span data-stu-id="acae7-251">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="acae7-252">Hierdoor kunt u het niet-interactief gebruiken:</span><span class="sxs-lookup"><span data-stu-id="acae7-252">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="acae7-253">De functie verwijderen `more`</span><span class="sxs-lookup"><span data-stu-id="acae7-253">Removal of the `more` function</span></span>

<span data-ttu-id="acae7-254">In het verleden heeft Power shell een functie geleverd in Windows `more` die is verpakt `more.com` .</span><span class="sxs-lookup"><span data-stu-id="acae7-254">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span> <span data-ttu-id="acae7-255">Deze functie is nu verwijderd.</span><span class="sxs-lookup"><span data-stu-id="acae7-255">That function has now been removed.</span></span>

<span data-ttu-id="acae7-256">Daarnaast is de `help` functie gewijzigd in gebruik `more.com` in Windows, of de standaard paginering van het systeem die is opgegeven door `$env:PAGER` op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="acae7-256">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="acae7-257">`cd DriveName:`retourneert nu gebruikers naar de huidige werkmap in dat station</span><span class="sxs-lookup"><span data-stu-id="acae7-257">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="acae7-258">Voorheen gebruik `Set-Location` of `cd` om terug te gaan naar een PSDrive die gebruikers naar de standaard locatie voor dat station heeft verzonden.</span><span class="sxs-lookup"><span data-stu-id="acae7-258">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="acae7-259">Bedankt voor [@mcbobke](https://github.com/mcbobke) , gebruikers worden nu verzonden naar de laatst bekende huidige werkmap voor die sessie.</span><span class="sxs-lookup"><span data-stu-id="acae7-259">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="acae7-260">Windows Power shell-type Accelerators</span><span class="sxs-lookup"><span data-stu-id="acae7-260">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="acae7-261">In Windows Power shell zijn de volgende typen Accelerators opgenomen om gemakkelijker te kunnen werken met hun respectieve typen:</span><span class="sxs-lookup"><span data-stu-id="acae7-261">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="acae7-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="acae7-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="acae7-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="acae7-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="acae7-264">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="acae7-264">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="acae7-265">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="acae7-265">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="acae7-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="acae7-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="acae7-267">Deze typen Accelerators zijn niet opgenomen in Power shell 6, maar zijn toegevoegd aan Power shell 6,1 uitgevoerd in Windows.</span><span class="sxs-lookup"><span data-stu-id="acae7-267">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="acae7-268">Deze typen zijn handig om eenvoudig AD-en WMI-objecten te maken.</span><span class="sxs-lookup"><span data-stu-id="acae7-268">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="acae7-269">U kunt bijvoorbeeld query's uitvoeren met behulp van LDAP:</span><span class="sxs-lookup"><span data-stu-id="acae7-269">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="acae7-270">In het volgende voor beeld wordt een Win32_OperatingSystem CIM-object gemaakt:</span><span class="sxs-lookup"><span data-stu-id="acae7-270">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="acae7-271">In dit voor beeld wordt een ManagementClass-object voor Win32_OperatingSystem-klasse geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="acae7-271">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="acae7-272">`-lp`alias voor alle `-LiteralPath` para meters</span><span class="sxs-lookup"><span data-stu-id="acae7-272">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="acae7-273">[@kvprasoon](https://github.com/kvprasoon)We hebben nu een parameter alias `-lp` voor alle ingebouwde Power shell-cmdlets die een `-LiteralPath` para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="acae7-273">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="acae7-274">Wijzigingen die fouten veroorzaken</span><span class="sxs-lookup"><span data-stu-id="acae7-274">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="acae7-275">MSI-gebaseerde installatie paden in Windows</span><span class="sxs-lookup"><span data-stu-id="acae7-275">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="acae7-276">In Windows wordt het MSI-pakket nu geïnstalleerd op het volgende pad:</span><span class="sxs-lookup"><span data-stu-id="acae7-276">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="acae7-277">`$env:ProgramFiles\PowerShell\6\`voor de stabiele installatie van 6. x</span><span class="sxs-lookup"><span data-stu-id="acae7-277">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="acae7-278">`$env:ProgramFiles\PowerShell\6-preview\`voor de preview-installatie van 6. x</span><span class="sxs-lookup"><span data-stu-id="acae7-278">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="acae7-279">Met deze wijziging wordt ervoor gezorgd dat Power shell core kan worden bijgewerkt/onderhouden door Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="acae7-279">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="acae7-280">Raadpleeg [Power shell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acae7-280">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="acae7-281">Telemetrie kan alleen worden uitgeschakeld met een omgevings variabele</span><span class="sxs-lookup"><span data-stu-id="acae7-281">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="acae7-282">Power shell core verzendt elementaire telemetriegegevens naar micro soft wanneer deze wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="acae7-282">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="acae7-283">De gegevens bevatten de naam van het besturings systeem, de versie van het besturings systeem en de Power shell-versie.</span><span class="sxs-lookup"><span data-stu-id="acae7-283">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="acae7-284">Met deze gegevens kunnen we beter inzicht krijgen in de omgevingen waarin Power shell wordt gebruikt en kunnen we de prioriteit van nieuwe functies en oplossingen bepalen.</span><span class="sxs-lookup"><span data-stu-id="acae7-284">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="acae7-285">Als u deze telemetrie wilt afmelden, stelt u de omgevings variabele `POWERSHELL_TELEMETRY_OPTOUT` in op `true` , `yes` of `1` .</span><span class="sxs-lookup"><span data-stu-id="acae7-285">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="acae7-286">Het verwijderen van het bestand voor het uitschakelen van telemetrie wordt niet meer ondersteund `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` .</span><span class="sxs-lookup"><span data-stu-id="acae7-286">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="acae7-287">Niet toegestaan basis verificatie via HTTP in externe communicatie met Power shell op UNIX-platforms</span><span class="sxs-lookup"><span data-stu-id="acae7-287">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="acae7-288">Om te voor komen dat niet-versleuteld verkeer wordt gebruikt, is het gebruik van NTLM/Negotiate of HTTPS vereist voor externe communicatie van Power shell op UNIX-platforms.</span><span class="sxs-lookup"><span data-stu-id="acae7-288">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="acae7-289">Voor meer informatie over deze wijzigingen raadpleegt u [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="acae7-289">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="acae7-290">Verwijderd `VisualBasic` als een ondersteunde taal in het invoeg type</span><span class="sxs-lookup"><span data-stu-id="acae7-290">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="acae7-291">In het verleden kunt u Visual Basic code compileren met behulp van de `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="acae7-291">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span> <span data-ttu-id="acae7-292">Visual Basic wordt zelden gebruikt met `Add-Type` .</span><span class="sxs-lookup"><span data-stu-id="acae7-292">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="acae7-293">Deze functie is verwijderd om de grootte van Power shell te reduceren.</span><span class="sxs-lookup"><span data-stu-id="acae7-293">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="acae7-294">Opgeruimd gebruik van `CommandTypes.Workflow` en`WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="acae7-294">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="acae7-295">Zie [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)voor meer informatie over deze wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="acae7-295">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="acae7-296">Groep-object sorteert nu de groepen</span><span class="sxs-lookup"><span data-stu-id="acae7-296">Group-Object now sorts the groups</span></span>

<span data-ttu-id="acae7-297">Als onderdeel van de verbetering van de prestaties `Group-Object` retourneert nu een gesorteerde lijst van de groepen.</span><span class="sxs-lookup"><span data-stu-id="acae7-297">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="acae7-298">Hoewel het niet nodig is om de volg orde te gebruiken, kunt u deze wijziging door lopen als u de eerste groep wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="acae7-298">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="acae7-299">We hebben besloten dat deze verbetering van de prestaties de verandering waard was, omdat de impact van de afhankelijkheid van het vorige gedrag laag is.</span><span class="sxs-lookup"><span data-stu-id="acae7-299">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="acae7-300">Zie [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409)voor meer informatie over deze wijziging.</span><span class="sxs-lookup"><span data-stu-id="acae7-300">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
