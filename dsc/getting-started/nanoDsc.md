---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC gebruiken op Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686584"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="13d8c-103">DSC gebruiken op Nano Server</span><span class="sxs-lookup"><span data-stu-id="13d8c-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="13d8c-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="13d8c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="13d8c-105">**DSC op Nano Server** is een optioneel pakket in de `NanoServer\Packages` map van de Windows Server 2016-media.</span><span class="sxs-lookup"><span data-stu-id="13d8c-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="13d8c-106">Het pakket kan worden geïnstalleerd wanneer u een VHD voor een Nano-Server door op te geven maken **Microsoft-NanoServer-DSC-Package** als de waarde van de **pakketten** parameter van de **New-NanoServerImage**  functie.</span><span class="sxs-lookup"><span data-stu-id="13d8c-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="13d8c-107">Als u een VHD voor een virtuele machine maakt, wordt door de opdracht er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="13d8c-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="13d8c-108">Zie voor meer informatie over het installeren en gebruiken van Nano Server, evenals over het beheren van Nano Server met externe communicatie van PowerShell [aan de slag met Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span><span class="sxs-lookup"><span data-stu-id="13d8c-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="13d8c-109">DSC-functies die beschikbaar zijn op Nano Server</span><span class="sxs-lookup"><span data-stu-id="13d8c-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="13d8c-110">Omdat Nano Server alleen een beperkte set API's in vergelijking met een volledige versie van Windows Server ondersteunt, heeft DSC op Nano Server geen volledig functionele pariteit met DSC op volledige SKU's voor de tijd die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="13d8c-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="13d8c-111">DSC op Nano Server is in ontwikkeling en is nog niet de functie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="13d8c-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="13d8c-112">De volgende DSC-functies zijn momenteel beschikbaar in Nano Server:</span><span class="sxs-lookup"><span data-stu-id="13d8c-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="13d8c-113">Zowel push als pull-modi</span><span class="sxs-lookup"><span data-stu-id="13d8c-113">Both push and pull modes</span></span>

- <span data-ttu-id="13d8c-114">Alle DSC-cmdlets die aanwezig zijn op een volledige versie van Windows Server, waaronder het volgende:</span><span class="sxs-lookup"><span data-stu-id="13d8c-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="13d8c-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="13d8c-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="13d8c-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="13d8c-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="13d8c-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="13d8c-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="13d8c-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="13d8c-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="13d8c-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="13d8c-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="13d8c-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="13d8c-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="13d8c-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="13d8c-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="13d8c-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="13d8c-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="13d8c-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="13d8c-123">Publish-DscConfiguraiton</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="13d8c-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="13d8c-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="13d8c-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="13d8c-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="13d8c-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="13d8c-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="13d8c-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="13d8c-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="13d8c-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="13d8c-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="13d8c-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="13d8c-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="13d8c-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="13d8c-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="13d8c-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="13d8c-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="13d8c-132">-Configuraties compileren (Zie [DSC-configuraties](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="13d8c-133">**Probleem:** Wachtwoordversleuteling (Zie [beveiligen van het MOF-bestand](../pull-server/secureMOF.md)) tijdens het configureren van de compilatie niet werkt.</span><span class="sxs-lookup"><span data-stu-id="13d8c-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="13d8c-134">Metaconfigurations compileren (Zie [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="13d8c-135">Een resource onder gebruikerscontext uitgevoerd (Zie [DSC uitvoeren met gebruikersreferenties (RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="13d8c-136">Op basis van een klasse resources (Zie [schrijven van een aangepaste DSC-resource met de PowerShell-klassen](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="13d8c-137">Foutopsporing van DSC-resources (Zie [foutopsporing DSC-resources](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="13d8c-138">**Probleem:** Werkt niet als een resource met behulp van PsDscRunAsCredential (Zie [DSC uitvoeren met gebruikersreferenties](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="13d8c-139">Afhankelijkheden van meerdere knooppunten opgeven</span><span class="sxs-lookup"><span data-stu-id="13d8c-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="13d8c-140">Resource-versiebeheer</span><span class="sxs-lookup"><span data-stu-id="13d8c-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="13d8c-141">Pull-client (configuraties en resources) (Zie [instellen van een pull-client met behulp van configuratienamen](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="13d8c-142">Gedeeltelijke configuraties (pull & push)</span><span class="sxs-lookup"><span data-stu-id="13d8c-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="13d8c-143">Rapporteren aan de pull-server</span><span class="sxs-lookup"><span data-stu-id="13d8c-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="13d8c-144">MOF-versleuteling</span><span class="sxs-lookup"><span data-stu-id="13d8c-144">MOF encryption</span></span>

- <span data-ttu-id="13d8c-145">Gebeurtenisregistratie</span><span class="sxs-lookup"><span data-stu-id="13d8c-145">Event logging</span></span>

- <span data-ttu-id="13d8c-146">Azure Automation DSC-rapportage</span><span class="sxs-lookup"><span data-stu-id="13d8c-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="13d8c-147">Resources die volledig functioneel zijn</span><span class="sxs-lookup"><span data-stu-id="13d8c-147">Resources that are fully functional</span></span>

- <span data-ttu-id="13d8c-148">**Archiveren**</span><span class="sxs-lookup"><span data-stu-id="13d8c-148">**Archive**</span></span>
- <span data-ttu-id="13d8c-149">**Omgeving**</span><span class="sxs-lookup"><span data-stu-id="13d8c-149">**Environment**</span></span>
- <span data-ttu-id="13d8c-150">**File**</span><span class="sxs-lookup"><span data-stu-id="13d8c-150">**File**</span></span>
- <span data-ttu-id="13d8c-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="13d8c-151">**Log**</span></span>
- <span data-ttu-id="13d8c-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="13d8c-152">**ProcessSet**</span></span>
- <span data-ttu-id="13d8c-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="13d8c-153">**Registry**</span></span>
- <span data-ttu-id="13d8c-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="13d8c-154">**Script**</span></span>
- <span data-ttu-id="13d8c-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="13d8c-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="13d8c-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="13d8c-156">**WindowsProcess**</span></span>
- <span data-ttu-id="13d8c-157">**WaitForAll** (Zie [afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="13d8c-158">**WaitForAny** (Zie [afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="13d8c-159">**WaitForSome** (Zie [afhankelijkheden van meerdere knooppunten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="13d8c-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="13d8c-160">Resources die, gedeeltelijk functionele zijn</span><span class="sxs-lookup"><span data-stu-id="13d8c-160">Resources that are partially functional</span></span>
- <span data-ttu-id="13d8c-161">**Groep**</span><span class="sxs-lookup"><span data-stu-id="13d8c-161">**Group**</span></span>
- <span data-ttu-id="13d8c-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="13d8c-162">**GroupSet**</span></span>

  <span data-ttu-id="13d8c-163">**Probleem:** Bovenstaande resources mislukken als specifieke exemplaar tweemaal wordt genoemd (met dezelfde configuratie twee keer)</span><span class="sxs-lookup"><span data-stu-id="13d8c-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="13d8c-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="13d8c-164">**Service**</span></span>
- <span data-ttu-id="13d8c-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="13d8c-165">**ServiceSet**</span></span>

  <span data-ttu-id="13d8c-166">**Probleem:** Werkt alleen voor (status) van de service starten/stoppen.</span><span class="sxs-lookup"><span data-stu-id="13d8c-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="13d8c-167">Mislukt, als een probeert te wijzigen van de kenmerken van andere service, zoals het opstarttype van, referenties, beschrijving, enzovoort...</span><span class="sxs-lookup"><span data-stu-id="13d8c-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="13d8c-168">De opgetreden fout is vergelijkbaar met:</span><span class="sxs-lookup"><span data-stu-id="13d8c-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="13d8c-169">*Kan type [management.managementobject] niet vinden: Controleer of de assembly met dit type is geladen.*</span><span class="sxs-lookup"><span data-stu-id="13d8c-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="13d8c-170">Resources die geen functionele</span><span class="sxs-lookup"><span data-stu-id="13d8c-170">Resources that are not functional</span></span>
- <span data-ttu-id="13d8c-171">**User**</span><span class="sxs-lookup"><span data-stu-id="13d8c-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="13d8c-172">DSC-functies niet beschikbaar in Nano Server</span><span class="sxs-lookup"><span data-stu-id="13d8c-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="13d8c-173">De volgende DSC-functies zijn momenteel niet beschikbaar in Nano Server:</span><span class="sxs-lookup"><span data-stu-id="13d8c-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="13d8c-174">MOF-document met versleutelde wachtwoorden ontsleutelen</span><span class="sxs-lookup"><span data-stu-id="13d8c-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="13d8c-175">Pull-Server kan niet op dit moment instellen van een pull-server op Nano Server</span><span class="sxs-lookup"><span data-stu-id="13d8c-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="13d8c-176">Alles dat zich niet in de lijst met de functie werkt</span><span class="sxs-lookup"><span data-stu-id="13d8c-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="13d8c-177">Aangepaste DSC-resources gebruiken in Nano Server</span><span class="sxs-lookup"><span data-stu-id="13d8c-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="13d8c-178">Vanwege een beperkte sets van Windows-API's en CLR-bibliotheken beschikbaar in Nano Server werken DSC-resources die aan de volledige CLR-versie van Windows werken mogelijk niet op Nano Server.</span><span class="sxs-lookup"><span data-stu-id="13d8c-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="13d8c-179">Volledige end-to-end testen voordat u een aangepaste DSC-resources in een productieomgeving implementeert.</span><span class="sxs-lookup"><span data-stu-id="13d8c-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="13d8c-180">Zie ook</span><span class="sxs-lookup"><span data-stu-id="13d8c-180">See Also</span></span>

- [<span data-ttu-id="13d8c-181">Aan de slag met Nano Server</span><span class="sxs-lookup"><span data-stu-id="13d8c-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
