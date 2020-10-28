---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: DSC gebruiken op Nano Server
description: DSC is een optioneel pakket dat kan worden geïnstalleerd wanneer u een VHD maakt voor een Windows nano-server.
ms.openlocfilehash: 18585323359abd85515d4db194dae4adbad7c3d8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647067"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="83589-104">DSC gebruiken op Nano Server</span><span class="sxs-lookup"><span data-stu-id="83589-104">Using DSC on Nano Server</span></span>

> <span data-ttu-id="83589-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="83589-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="83589-106">**DSC op nano server** is een optioneel pakket in de `NanoServer\Packages` map van de Windows Server 2016-media.</span><span class="sxs-lookup"><span data-stu-id="83589-106">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="83589-107">Het pakket kan worden geïnstalleerd wanneer u een VHD maakt voor een nano server door het opgeven van **micro soft-nano server-DSC-package** als de waarde van de para meter **packages** van de functie **New-nano Server image** .</span><span class="sxs-lookup"><span data-stu-id="83589-107">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="83589-108">Als u bijvoorbeeld een VHD voor een virtuele machine maakt, ziet de opdracht er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="83589-108">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="83589-109">Zie aan de slag [met nano server](/windows-server/get-started/getting-started-with-nano-server)voor meer informatie over het installeren en gebruiken van nano server, en het beheren van nano server met externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="83589-109">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="83589-110">DSC-functies die beschikbaar zijn op nano server</span><span class="sxs-lookup"><span data-stu-id="83589-110">DSC features available on Nano Server</span></span>

<span data-ttu-id="83589-111">Omdat nano server alleen ondersteuning biedt voor een beperkt aantal Api's in vergelijking met een volledige versie van Windows Server, heeft DSC op nano server niet de volledige functionele pariteit met DSC die op volledige Sku's wordt uitgevoerd voor de tijd.</span><span class="sxs-lookup"><span data-stu-id="83589-111">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="83589-112">DSC op nano server is actief en is nog niet voltooid.</span><span class="sxs-lookup"><span data-stu-id="83589-112">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="83589-113">De volgende DSC-functies zijn momenteel beschikbaar op nano server:</span><span class="sxs-lookup"><span data-stu-id="83589-113">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="83589-114">Zowel push-als pull-modi</span><span class="sxs-lookup"><span data-stu-id="83589-114">Both push and pull modes</span></span>

- <span data-ttu-id="83589-115">Alle DSC-cmdlets die voor komen in een volledige versie van Windows Server, met inbegrip van het volgende:</span><span class="sxs-lookup"><span data-stu-id="83589-115">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="83589-116">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="83589-116">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="83589-117">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="83589-117">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="83589-118">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="83589-118">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="83589-119">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="83589-119">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="83589-120">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="83589-120">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="83589-121">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="83589-121">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="83589-122">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="83589-122">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="83589-123">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="83589-123">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="83589-124">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="83589-124">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="83589-125">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="83589-125">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="83589-126">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="83589-126">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="83589-127">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="83589-127">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="83589-128">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="83589-128">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="83589-129">Invoke-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="83589-129">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="83589-130">Zoeken-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="83589-130">Find-DscResource</span></span>](/powershell/module/powershellget/find-dscresource)
- [<span data-ttu-id="83589-131">Get-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="83589-131">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="83589-132">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="83589-132">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="83589-133">Configuraties compileren (Zie [DSC-configuraties](../configurations/configurations.md))</span><span class="sxs-lookup"><span data-stu-id="83589-133">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="83589-134">**Probleem:** Wachtwoord versleuteling (Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)) tijdens de compilatie van de configuratie werkt niet.</span><span class="sxs-lookup"><span data-stu-id="83589-134">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="83589-135">Bezig met het compileren van de-configuratie (Zie [de lokale Configuration Manager configureren](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="83589-135">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="83589-136">Een resource uitvoeren onder gebruikers context (Zie [DSC uitvoeren met gebruikers referenties (runas)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="83589-136">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="83589-137">Op klassen gebaseerde resources (Zie [een aangepaste DSC-resource schrijven met Power shell-klassen](/previous-versions//dn948461(v=technet.10)))</span><span class="sxs-lookup"><span data-stu-id="83589-137">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)))</span></span>

- <span data-ttu-id="83589-138">Fout opsporing voor DSC-resources (Zie [fout opsporing voor DSC-resources](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="83589-138">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="83589-139">**Probleem:** Werkt niet als een resource gebruikmaakt van PsDscRunAsCredential (Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="83589-139">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="83589-140">Afhankelijkheden van meerdere knooppunten opgeven</span><span class="sxs-lookup"><span data-stu-id="83589-140">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="83589-141">Resource versie beheer</span><span class="sxs-lookup"><span data-stu-id="83589-141">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="83589-142">Pull-client (configuraties & bronnen) (Zie [een pull-client instellen met behulp van configuratie namen](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="83589-142">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="83589-143">Gedeeltelijke configuraties (pull & push)</span><span class="sxs-lookup"><span data-stu-id="83589-143">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="83589-144">Rapportage aan pull-server</span><span class="sxs-lookup"><span data-stu-id="83589-144">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="83589-145">MOF-versleuteling</span><span class="sxs-lookup"><span data-stu-id="83589-145">MOF encryption</span></span>

- <span data-ttu-id="83589-146">Gebeurtenis registratie</span><span class="sxs-lookup"><span data-stu-id="83589-146">Event logging</span></span>

- <span data-ttu-id="83589-147">Azure Automation DSC-rapportage</span><span class="sxs-lookup"><span data-stu-id="83589-147">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="83589-148">Volledig functionele bronnen</span><span class="sxs-lookup"><span data-stu-id="83589-148">Resources that are fully functional</span></span>

  - <span data-ttu-id="83589-149">**Archiveren**</span><span class="sxs-lookup"><span data-stu-id="83589-149">**Archive**</span></span>
  - <span data-ttu-id="83589-150">**Omgeving**</span><span class="sxs-lookup"><span data-stu-id="83589-150">**Environment**</span></span>
  - <span data-ttu-id="83589-151">**File**</span><span class="sxs-lookup"><span data-stu-id="83589-151">**File**</span></span>
  - <span data-ttu-id="83589-152">**Logbestand**</span><span class="sxs-lookup"><span data-stu-id="83589-152">**Log**</span></span>
  - <span data-ttu-id="83589-153">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="83589-153">**ProcessSet**</span></span>
  - <span data-ttu-id="83589-154">**Register**</span><span class="sxs-lookup"><span data-stu-id="83589-154">**Registry**</span></span>
  - <span data-ttu-id="83589-155">**Script**</span><span class="sxs-lookup"><span data-stu-id="83589-155">**Script**</span></span>
  - <span data-ttu-id="83589-156">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="83589-156">**WindowsPackageCab**</span></span>
  - <span data-ttu-id="83589-157">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="83589-157">**WindowsProcess**</span></span>
  - <span data-ttu-id="83589-158">**WaitForAll** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="83589-158">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
  - <span data-ttu-id="83589-159">**WaitForAny** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="83589-159">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
  - <span data-ttu-id="83589-160">**WaitForSome** (Zie [afhankelijkheden van meerdere knoop punten opgeven](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="83589-160">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="83589-161">Resources die gedeeltelijk functioneel zijn</span><span class="sxs-lookup"><span data-stu-id="83589-161">Resources that are partially functional</span></span>

  - <span data-ttu-id="83589-162">**Groep**</span><span class="sxs-lookup"><span data-stu-id="83589-162">**Group**</span></span>
  - <span data-ttu-id="83589-163">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="83589-163">**GroupSet**</span></span>

    <span data-ttu-id="83589-164">**Probleem:** De bovenstaande bronnen mislukken als een specifiek exemplaar twee maal wordt aangeroepen (twee keer dezelfde configuratie uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="83589-164">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  - <span data-ttu-id="83589-165">**Service**</span><span class="sxs-lookup"><span data-stu-id="83589-165">**Service**</span></span>
  - <span data-ttu-id="83589-166">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="83589-166">**ServiceSet**</span></span>

    <span data-ttu-id="83589-167">**Probleem:** Werkt alleen voor starten/stoppen (status)-service.</span><span class="sxs-lookup"><span data-stu-id="83589-167">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="83589-168">Mislukt als er wordt geprobeerd andere service kenmerken te wijzigen, zoals opstart type, referenties, Description, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="83589-168">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="83589-169">De fout die wordt gegenereerd, is vergelijkbaar met:</span><span class="sxs-lookup"><span data-stu-id="83589-169">The error thrown is similar to:</span></span>

    ```
    Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.
    ```

- <span data-ttu-id="83589-170">Resources die niet functioneel zijn</span><span class="sxs-lookup"><span data-stu-id="83589-170">Resources that are not functional</span></span>

  - <span data-ttu-id="83589-171">**Gebruiker**</span><span class="sxs-lookup"><span data-stu-id="83589-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="83589-172">DSC-functies zijn niet beschikbaar op nano server</span><span class="sxs-lookup"><span data-stu-id="83589-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="83589-173">De volgende DSC-functies zijn momenteel niet beschikbaar op nano server:</span><span class="sxs-lookup"><span data-stu-id="83589-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="83589-174">MOF-document met versleuteld wacht woord (en) ontsleutelen</span><span class="sxs-lookup"><span data-stu-id="83589-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="83589-175">Pull-server: u kunt momenteel geen pull-server op nano server instellen</span><span class="sxs-lookup"><span data-stu-id="83589-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="83589-176">Alles wat niet voor komt in de lijst met functies werkt</span><span class="sxs-lookup"><span data-stu-id="83589-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="83589-177">Aangepaste DSC-resources gebruiken op nano server</span><span class="sxs-lookup"><span data-stu-id="83589-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="83589-178">Vanwege een beperkt aantal Windows-Api's en CLR-bibliotheken die beschikbaar zijn op nano server, werken DSC-resources die werken met de volledige CLR-versie van Windows, niet noodzakelijkerwijs op nano server.</span><span class="sxs-lookup"><span data-stu-id="83589-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="83589-179">Voltooi end-to-end tests voordat u eventuele DSC-aangepaste resources implementeert in een productie omgeving.</span><span class="sxs-lookup"><span data-stu-id="83589-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="83589-180">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83589-180">See Also</span></span>

- [<span data-ttu-id="83589-181">Aan de slag met Nano Server</span><span class="sxs-lookup"><span data-stu-id="83589-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
