---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: DSC gebruiken op Nano Server
ms.openlocfilehash: fb826455c21833ae4c8dc2ecd731ffce6bf7eaba
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941878"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="2931c-103">DSC gebruiken op Nano Server</span><span class="sxs-lookup"><span data-stu-id="2931c-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="2931c-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="2931c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2931c-105">**DSC op nano server** is een optioneel pakket in de map `NanoServer\Packages` van de Windows Server 2016-media.</span><span class="sxs-lookup"><span data-stu-id="2931c-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="2931c-106">Het pakket kan worden geïnstalleerd wanneer u een VHD maakt voor een nano server door het opgeven van **micro soft-nano server-DSC-package** als de waarde van de para meter **packages** van de functie **New-nano Server image** .</span><span class="sxs-lookup"><span data-stu-id="2931c-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="2931c-107">Als u bijvoorbeeld een VHD voor een virtuele machine maakt, ziet de opdracht er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="2931c-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="2931c-108">Zie aan de slag [met nano server](/windows-server/get-started/getting-started-with-nano-server)voor meer informatie over het installeren en gebruiken van nano server, en het beheren van nano server met externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="2931c-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="2931c-109">DSC-functies die beschikbaar zijn op nano server</span><span class="sxs-lookup"><span data-stu-id="2931c-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="2931c-110">Omdat nano server alleen ondersteuning biedt voor een beperkt aantal Api's in vergelijking met een volledige versie van Windows Server, heeft DSC op nano server niet de volledige functionele pariteit met DSC die op volledige Sku's wordt uitgevoerd voor de tijd.</span><span class="sxs-lookup"><span data-stu-id="2931c-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="2931c-111">DSC op nano server is actief en is nog niet voltooid.</span><span class="sxs-lookup"><span data-stu-id="2931c-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="2931c-112">De volgende DSC-functies zijn momenteel beschikbaar op nano server:</span><span class="sxs-lookup"><span data-stu-id="2931c-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="2931c-113">Zowel push-als pull-modi</span><span class="sxs-lookup"><span data-stu-id="2931c-113">Both push and pull modes</span></span>

- <span data-ttu-id="2931c-114">Alle DSC-cmdlets die voor komen in een volledige versie van Windows Server, met inbegrip van het volgende:</span><span class="sxs-lookup"><span data-stu-id="2931c-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="2931c-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2931c-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="2931c-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2931c-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="2931c-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="2931c-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="2931c-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="2931c-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="2931c-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2931c-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="2931c-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2931c-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="2931c-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2931c-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="2931c-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2931c-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="2931c-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2931c-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="2931c-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2931c-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="2931c-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2931c-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="2931c-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="2931c-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="2931c-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2931c-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="2931c-128">Invoke-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="2931c-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="2931c-129">Zoeken-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="2931c-129">Find-DscResource</span></span>](/powershell/module/powershellget/find-dscresource?view=powershell-6)
- [<span data-ttu-id="2931c-130">Get-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="2931c-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="2931c-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="2931c-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="2931c-132">Configuraties compileren (Zie [DSC-configuraties](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="2931c-133">**Name** Wachtwoord versleuteling (Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)) tijdens de compilatie van de configuratie werkt niet.</span><span class="sxs-lookup"><span data-stu-id="2931c-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="2931c-134">Bezig met het compileren van de-configuratie (Zie [de lokale Configuration Manager configureren](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="2931c-135">Een resource uitvoeren onder gebruikers context (Zie [DSC uitvoeren met gebruikers referenties (runas)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="2931c-136">Op klassen gebaseerde resources (Zie [een aangepaste DSC-resource schrijven met Power shell-klassen](/previous-versions//dn948461(v=technet.10)))</span><span class="sxs-lookup"><span data-stu-id="2931c-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)))</span></span>

- <span data-ttu-id="2931c-137">Fout opsporing voor DSC-resources (Zie [fout opsporing voor DSC-resources](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="2931c-138">**Name** Werkt niet als een resource gebruikmaakt van PsDscRunAsCredential (Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="2931c-139">Afhankelijkheden van meerdere knooppunten opgeven</span><span class="sxs-lookup"><span data-stu-id="2931c-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="2931c-140">Resource versie beheer</span><span class="sxs-lookup"><span data-stu-id="2931c-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="2931c-141">Pull-client (configuraties & bronnen) (Zie [een pull-client instellen met behulp van configuratie namen](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="2931c-142">Gedeeltelijke configuraties (pull & push)</span><span class="sxs-lookup"><span data-stu-id="2931c-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="2931c-143">Rapportage aan pull-server</span><span class="sxs-lookup"><span data-stu-id="2931c-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="2931c-144">MOF-versleuteling</span><span class="sxs-lookup"><span data-stu-id="2931c-144">MOF encryption</span></span>

- <span data-ttu-id="2931c-145">Gebeurtenis registratie</span><span class="sxs-lookup"><span data-stu-id="2931c-145">Event logging</span></span>

- <span data-ttu-id="2931c-146">Azure Automation DSC-rapportage</span><span class="sxs-lookup"><span data-stu-id="2931c-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="2931c-147">Volledig functionele bronnen</span><span class="sxs-lookup"><span data-stu-id="2931c-147">Resources that are fully functional</span></span>

- <span data-ttu-id="2931c-148">**Archief**</span><span class="sxs-lookup"><span data-stu-id="2931c-148">**Archive**</span></span>
- <span data-ttu-id="2931c-149">**Variabelen**</span><span class="sxs-lookup"><span data-stu-id="2931c-149">**Environment**</span></span>
- <span data-ttu-id="2931c-150">**File**</span><span class="sxs-lookup"><span data-stu-id="2931c-150">**File**</span></span>
- <span data-ttu-id="2931c-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="2931c-151">**Log**</span></span>
- <span data-ttu-id="2931c-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="2931c-152">**ProcessSet**</span></span>
- <span data-ttu-id="2931c-153">**Registersubsleutel**</span><span class="sxs-lookup"><span data-stu-id="2931c-153">**Registry**</span></span>
- <span data-ttu-id="2931c-154">**Schriften**</span><span class="sxs-lookup"><span data-stu-id="2931c-154">**Script**</span></span>
- <span data-ttu-id="2931c-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="2931c-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="2931c-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="2931c-156">**WindowsProcess**</span></span>
- <span data-ttu-id="2931c-157">**WaitForAll** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="2931c-158">**WaitForAny** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="2931c-159">**WaitForSome** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="2931c-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="2931c-160">Resources die gedeeltelijk functioneel zijn</span><span class="sxs-lookup"><span data-stu-id="2931c-160">Resources that are partially functional</span></span>
- <span data-ttu-id="2931c-161">**Groep**</span><span class="sxs-lookup"><span data-stu-id="2931c-161">**Group**</span></span>
- <span data-ttu-id="2931c-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="2931c-162">**GroupSet**</span></span>

  <span data-ttu-id="2931c-163">**Name** De bovenstaande bronnen mislukken als een specifiek exemplaar twee maal wordt aangeroepen (twee keer dezelfde configuratie uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="2931c-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="2931c-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="2931c-164">**Service**</span></span>
- <span data-ttu-id="2931c-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="2931c-165">**ServiceSet**</span></span>

  <span data-ttu-id="2931c-166">**Name** Werkt alleen voor starten/stoppen (status)-service.</span><span class="sxs-lookup"><span data-stu-id="2931c-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="2931c-167">Mislukt als er wordt geprobeerd andere service kenmerken te wijzigen, zoals opstart type, referenties, Description, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="2931c-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="2931c-168">De fout die wordt gegenereerd, is vergelijkbaar met:</span><span class="sxs-lookup"><span data-stu-id="2931c-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="2931c-169">*Kan type [management. managementobject] niet vinden: Controleer of de assembly met dit type is geladen.*</span><span class="sxs-lookup"><span data-stu-id="2931c-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="2931c-170">Resources die niet functioneel zijn</span><span class="sxs-lookup"><span data-stu-id="2931c-170">Resources that are not functional</span></span>
- <span data-ttu-id="2931c-171">**Gebruiker**</span><span class="sxs-lookup"><span data-stu-id="2931c-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="2931c-172">DSC-functies zijn niet beschikbaar op nano server</span><span class="sxs-lookup"><span data-stu-id="2931c-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="2931c-173">De volgende DSC-functies zijn momenteel niet beschikbaar op nano server:</span><span class="sxs-lookup"><span data-stu-id="2931c-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="2931c-174">MOF-document met versleuteld wacht woord (en) ontsleutelen</span><span class="sxs-lookup"><span data-stu-id="2931c-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="2931c-175">Pull-server: u kunt momenteel geen pull-server op nano server instellen</span><span class="sxs-lookup"><span data-stu-id="2931c-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="2931c-176">Alles wat niet voor komt in de lijst met functies werkt</span><span class="sxs-lookup"><span data-stu-id="2931c-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="2931c-177">Aangepaste DSC-resources gebruiken op nano server</span><span class="sxs-lookup"><span data-stu-id="2931c-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="2931c-178">Vanwege een beperkt aantal Windows-Api's en CLR-bibliotheken die beschikbaar zijn op nano server, werken DSC-resources die werken met de volledige CLR-versie van Windows, niet noodzakelijkerwijs op nano server.</span><span class="sxs-lookup"><span data-stu-id="2931c-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="2931c-179">Voltooi end-to-end tests voordat u eventuele DSC-aangepaste resources implementeert in een productie omgeving.</span><span class="sxs-lookup"><span data-stu-id="2931c-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="2931c-180">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2931c-180">See Also</span></span>

- [<span data-ttu-id="2931c-181">Aan de slag met nano server</span><span class="sxs-lookup"><span data-stu-id="2931c-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
