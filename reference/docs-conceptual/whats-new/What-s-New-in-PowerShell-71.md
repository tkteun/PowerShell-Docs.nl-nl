---
title: Wat is er nieuw in Power shell 7,1
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell 7,1
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577204"
---
# <a name="whats-new-in-powershell-71"></a><span data-ttu-id="c2fd7-103">Wat is er nieuw in Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="c2fd7-103">What's New in PowerShell 7.1</span></span>

<span data-ttu-id="c2fd7-104">Op 11 november 2020 hebben we de algemene Beschik baarheid van Power shell 7,1 [aangekondigd](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) .</span><span class="sxs-lookup"><span data-stu-id="c2fd7-104">On November 11, 2020 we [announced](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) the general availability of PowerShell 7.1.</span></span> <span data-ttu-id="c2fd7-105">Voortbouwend op de basis die is vastgesteld in Power shell 7,0, onze inspanningen gericht op problemen van de community en bevatten een aantal verbeteringen en oplossingen.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-105">Building on the foundation established in PowerShell 7.0, our efforts focused on community issues and include a number of improvements and fixes.</span></span> <span data-ttu-id="c2fd7-106">We streven ernaar om ervoor te zorgen dat Power shell een stabiel en het beste platform blijft.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-106">We are committed to ensuring that PowerShell remains a stable and performant platform.</span></span>

<span data-ttu-id="c2fd7-107">Power shell 7,1 bevat de volgende functies, updates en belang rijke wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-107">PowerShell 7.1 includes the following features, updates, and breaking changes.</span></span>

- <span data-ttu-id="c2fd7-108">PSReadLine 2.1.0, met inbegrip van voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="c2fd7-108">PSReadLine 2.1.0, which includes Predictive IntelliSense</span></span>
- <span data-ttu-id="c2fd7-109">Power shell 7,1 is gepubliceerd op de Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="c2fd7-109">PowerShell 7.1 has been published to the Microsoft Store</span></span>
- <span data-ttu-id="c2fd7-110">Installatie pakketten bijgewerkt voor nieuwe versies van besturings systemen met ondersteuning voor ARM64</span><span class="sxs-lookup"><span data-stu-id="c2fd7-110">Installer packages updated for new OS versions with support for ARM64</span></span>
- <span data-ttu-id="c2fd7-111">4 nieuwe experimentele functies en twee experimentele functies gepromoveerd tot mainstream</span><span class="sxs-lookup"><span data-stu-id="c2fd7-111">4 new experimental features and 2 experimental features promoted to mainstream</span></span>
- <span data-ttu-id="c2fd7-112">Verschillende belang rijke wijzigingen om de bruikbaarheid te verbeteren</span><span class="sxs-lookup"><span data-stu-id="c2fd7-112">Several breaking changes to improve usability</span></span>

<span data-ttu-id="c2fd7-113">Zie de [wijzigingen logboek](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) in de GitHub-opslag plaats voor een volledige lijst met wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-113">For a complete list of changes, see the [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) in the GitHub repository.</span></span>

## <a name="psreadline-210"></a><span data-ttu-id="c2fd7-114">PSReadLine 2.1.0</span><span class="sxs-lookup"><span data-stu-id="c2fd7-114">PSReadLine 2.1.0</span></span>

<span data-ttu-id="c2fd7-115">Power shell 7,1 bevat ook PSReadLine 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-115">PowerShell 7.1 also include PSReadLine 2.1.0.</span></span> <span data-ttu-id="c2fd7-116">Deze versie bevat voorspellende IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-116">This version includes Predictive IntelliSense.</span></span> <span data-ttu-id="c2fd7-117">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) in het Power shell-blog voor meer informatie over de functie voor voorspellende IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-117">For more information about the Predictive IntelliSense feature, see the [announcement](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) in the PowerShell blog.</span></span>

## <a name="microsoft-store-installer-package"></a><span data-ttu-id="c2fd7-118">Microsoft Store Installer-pakket</span><span class="sxs-lookup"><span data-stu-id="c2fd7-118">Microsoft Store installer package</span></span>

<span data-ttu-id="c2fd7-119">Power shell 7,1 is gepubliceerd op de Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-119">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="c2fd7-120">U kunt de Power shell-release vinden op de [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website of in de Store-toepassing in Windows.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-120">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="c2fd7-121">Voor delen van het Microsoft Store-pakket:</span><span class="sxs-lookup"><span data-stu-id="c2fd7-121">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="c2fd7-122">Automatische updates zijn direct in Windows 10 ingebouwd</span><span class="sxs-lookup"><span data-stu-id="c2fd7-122">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="c2fd7-123">Kan worden geïntegreerd met andere software distributie mechanismen, zoals intune en SCCM</span><span class="sxs-lookup"><span data-stu-id="c2fd7-123">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

> [!NOTE]
> <span data-ttu-id="c2fd7-124">Alle configuratie-instellingen op systeem niveau die zijn opgeslagen in, `$PSHOME` kunnen niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-124">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="c2fd7-125">Dit omvat de WSMAN-configuratie.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-125">This includes the WSMAN configuration.</span></span> <span data-ttu-id="c2fd7-126">Hiermee voor komt u dat externe sessies verbinding maken met op opslag gebaseerde installaties van Power shell.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-126">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="c2fd7-127">Configuraties op gebruikers niveau en externe SSH-communicatie worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-127">User-level configurations and SSH remoting are supported.</span></span>

## <a name="other-installers"></a><span data-ttu-id="c2fd7-128">Andere installatie Programma's</span><span class="sxs-lookup"><span data-stu-id="c2fd7-128">Other installers</span></span>

<span data-ttu-id="c2fd7-129">Zie de [Power shell-ondersteunings levenscyclus](/powershell/scripting/powershell-support-lifecycle)voor meer actuele informatie over de ondersteunde besturings systemen en de levens cyclus van de ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-129">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

<span data-ttu-id="c2fd7-130">Controleer de installatie-instructies voor uw voorkeurs besturings systeem:</span><span class="sxs-lookup"><span data-stu-id="c2fd7-130">Check the installation instructions for your preferred operating system:</span></span>

- [<span data-ttu-id="c2fd7-131">Windows</span><span class="sxs-lookup"><span data-stu-id="c2fd7-131">Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows)
- [<span data-ttu-id="c2fd7-132">MacOS</span><span class="sxs-lookup"><span data-stu-id="c2fd7-132">macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos)
- [<span data-ttu-id="c2fd7-133">Linux</span><span class="sxs-lookup"><span data-stu-id="c2fd7-133">Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux)

<span data-ttu-id="c2fd7-134">Daarnaast ondersteunt Power shell 7,1 ARM32-en ARM64-smaakten van Debian, Ubuntu en ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-134">Additionally, PowerShell 7.1 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="c2fd7-135">Hoewel niet officieel wordt ondersteund, heeft de community ook pakketten voor [Arch](https://aur.archlinux.org/packages/powershell/) en Kali Linux verschaft.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-135">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="c2fd7-136">Debian 10 +, CentOS 8 +, Ubuntu 20,04, alpine en arm bieden momenteel geen ondersteuning voor externe toegang via WinRM.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-136">Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine and Arm currently do not support WinRM remoting.</span></span> <span data-ttu-id="c2fd7-137">Zie voor meer informatie over het instellen van op SSH gebaseerde externe communicatie [Power shell voor externe toegang via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="c2fd7-137">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="experimental-features"></a><span data-ttu-id="c2fd7-138">Experimentele functies</span><span class="sxs-lookup"><span data-stu-id="c2fd7-138">Experimental Features</span></span>

<span data-ttu-id="c2fd7-139">Zie [experimentele functies gebruiken](../learn/experimental-features.md)voor meer informatie over de experimentele functies.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-139">For more information about the Experimental Features, see [Using Experimental Features](../learn/experimental-features.md).</span></span>

<span data-ttu-id="c2fd7-140">De volgende experimentele functies zijn nu algemene functies in deze release:</span><span class="sxs-lookup"><span data-stu-id="c2fd7-140">The following experimental features are now mainstream features in this release:</span></span>

- [<span data-ttu-id="c2fd7-141">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="c2fd7-141">PSNullConditionalOperators</span></span>](../learn/experimental-features.md#psnullconditionaloperators)
- [<span data-ttu-id="c2fd7-142">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="c2fd7-142">PSUnixFileStat</span></span>](../learn/experimental-features.md#psunixfilestat)

<span data-ttu-id="c2fd7-143">In deze release zijn de volgende experimentele functies toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="c2fd7-143">The following experimental features were added in this release:</span></span>

- [<span data-ttu-id="c2fd7-144">Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="c2fd7-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - <span data-ttu-id="c2fd7-145">Power shell 7,1 breidt deze experimentele functie uit om de para meter **runs Pace** toe te voegen aan alle `*-PSBreakpoint` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-145">PowerShell 7.1 extends this experimental feature to add the **Runspace** parameter to all `*-PSBreakpoint` cmdlets.</span></span> <span data-ttu-id="c2fd7-146">De para meter **runs Pace** geeft een **runs Pace** -object op om te communiceren met onderbrekings punten in de opgegeven runs Pace.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-146">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

- <span data-ttu-id="c2fd7-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) : met deze functie kunt u de paden van de Power shell-provider door geven aan systeem eigen opdrachten die geen Power shell-pad-syntaxis ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - This feature allows you to pass PowerShell provider paths to native commands that don't support PowerShell path syntax.</span></span>

- <span data-ttu-id="c2fd7-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) : wanneer de linkeroperand in een `-replace` operator instructie geen teken reeks is, wordt die operand geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span> <span data-ttu-id="c2fd7-149">Als de functie is ingeschakeld, gebruikt de conversie geen cultuur instellingen voor teken reeks conversie.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-149">With the feature enabled, the conversion does not use Culture settings for string conversion.</span></span>

- <span data-ttu-id="c2fd7-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) legt de basis voor de ondersteuning van toekomstige voorspellende IntelliSense-invoeg toepassingen.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) lays the groundwork to support future Predictive IntelliSense plug-ins.</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="c2fd7-151">Wijzigingen en verbeteringen te verbreken</span><span class="sxs-lookup"><span data-stu-id="c2fd7-151">Breaking Changes and Improvements</span></span>

- <span data-ttu-id="c2fd7-152">Oplossing `$?` niet wanneer een `$false` systeem eigen opdracht schrijft naar `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span><span class="sxs-lookup"><span data-stu-id="c2fd7-152">Fix `$?` to not be `$false` when native command writes to `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span></span>

  <span data-ttu-id="c2fd7-153">Het is gebruikelijk dat systeem eigen opdrachten schrijven naar `stderr` zonder dat ze een fout aangeven.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-153">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="c2fd7-154">Deze wijziging `$?` is alleen ingesteld op `$false` wanneer de systeem eigen opdracht ook een afsluit code heeft die niet gelijk is aan nul.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-154">With this change `$?` is set to `$false` only when the native command also has a non-zero exit code.</span></span> <span data-ttu-id="c2fd7-155">Deze wijziging is niet gerelateerd aan het experimentele onderdeel `PSNotApplyErrorActionToStderr` .</span><span class="sxs-lookup"><span data-stu-id="c2fd7-155">This change is unrelated to the experimental feature `PSNotApplyErrorActionToStderr`.</span></span>

- <span data-ttu-id="c2fd7-156">`$ErrorActionPreference`Geen invloed hebben op de `stderr` uitvoer van systeem eigen opdrachten ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span><span class="sxs-lookup"><span data-stu-id="c2fd7-156">Make `$ErrorActionPreference` not affect `stderr` output of native commands ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span></span>

  <span data-ttu-id="c2fd7-157">Het is gebruikelijk dat systeem eigen opdrachten schrijven naar `stderr` zonder dat ze een fout aangeven.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-157">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="c2fd7-158">Met deze wijziging `stderr` wordt de uitvoer nog steeds vastgelegd in **ErrorRecord** -objecten, maar de runtime is niet meer van toepassing `$ErrorActionPreference` als de **ErrorRecord** afkomstig is van een native opdracht.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-158">With this change, `stderr` output is still captured in **ErrorRecord** objects, but the runtime no longer applies `$ErrorActionPreference` if the **ErrorRecord** comes from a native command.</span></span>

- <span data-ttu-id="c2fd7-159">Wijzig de naam in `-FromUnixTime` `-UnixTimeSeconds` `Get-Date` om Unix-tijd invoer ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) toe te staan (bedankt @aetos382 !)</span><span class="sxs-lookup"><span data-stu-id="c2fd7-159">Rename `-FromUnixTime` to `-UnixTimeSeconds` on `Get-Date` to allow Unix time input ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (Thanks @aetos382!)</span></span>

  <span data-ttu-id="c2fd7-160">De `-FromUnixTime` para meter is toegevoegd tijdens 7,1-Preview. 2.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-160">The `-FromUnixTime` parameter was added during 7.1-preview.2.</span></span> <span data-ttu-id="c2fd7-161">De naam van de para meter is gewijzigd om deze beter te laten overeenkomen met het gegevens type.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-161">The parameter was renamed to better match the data type.</span></span> <span data-ttu-id="c2fd7-162">Deze para meter neemt een geheel getal in seconden sinds 1 januari 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-162">This parameter takes an integer value that represents in seconds since January 1, 1970, 0:00:00.</span></span>

  <span data-ttu-id="c2fd7-163">In dit voor beeld wordt een Unix-tijd (vertegenwoordigd door het aantal seconden sinds 1970-01-01 0:00:00) geconverteerd naar DateTime.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-163">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- <span data-ttu-id="c2fd7-164">Een expliciet opgegeven benoemde para meter mag vervangen door de naam van de hashtabel splatting (#13162)</span><span class="sxs-lookup"><span data-stu-id="c2fd7-164">Allow explicitly specified named parameter to supersede the same one from hashtable splatting (#13162)</span></span>

  <span data-ttu-id="c2fd7-165">Met deze wijziging worden de benoemde para meters van splatting verplaatst naar het einde van de lijst met para meters, zodat deze zijn gebonden nadat alle expliciet opgegeven benoemde para meters zijn gebonden.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-165">With this change, the named parameters from splatting are moved to the end of the parameter list so that they are bound after all explicitly specified named parameters are bound.</span></span> <span data-ttu-id="c2fd7-166">Parameter binding voor eenvoudige functies genereert geen fout wanneer een opgegeven benoemde para meter niet kan worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-166">Parameter binding for simple functions doesn't throw an error when a specified named parameter cannot be found.</span></span> <span data-ttu-id="c2fd7-167">Onbekende benoemde para meters zijn gekoppeld aan de `$args` para meter van de functie Simple.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-167">Unknown named parameters are bound to the `$args` parameter of the simple function.</span></span> <span data-ttu-id="c2fd7-168">Als u splatting verplaatst naar het einde van de argumenten lijst, wordt de volg orde gewijzigd waarin de para meters worden weer gegeven `$args` .</span><span class="sxs-lookup"><span data-stu-id="c2fd7-168">Moving splatting to the end of the argument list changes the order the parameters appears in `$args`.</span></span>

  <span data-ttu-id="c2fd7-169">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c2fd7-169">For example:</span></span>

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  <span data-ttu-id="c2fd7-170">In het vorige gedrag is **MYPATH** niet gebonden aan `-Path` het derde argument in de lijst met argumenten.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-170">In the previous behavior, **MyPath** is not bound to `-Path` because it's the third argument in the argument list.</span></span> <span data-ttu-id="c2fd7-171"># #, Zodat deze wordt gecenteerd in ' $args ' samen met `Blah = "World"`</span><span class="sxs-lookup"><span data-stu-id="c2fd7-171">## So it ends up being stuffed into '$args' along with `Blah = "World"`</span></span>

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  <span data-ttu-id="c2fd7-172">Met deze wijziging worden de argumenten van `@hash` verplaatst naar het einde van de lijst met argumenten.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-172">With this change, the arguments from `@hash` are moved to the end of the argument list.</span></span> <span data-ttu-id="c2fd7-173">**MYPATH** wordt het eerste argument in de lijst, dus is het gebonden aan `-Path` .</span><span class="sxs-lookup"><span data-stu-id="c2fd7-173">**MyPath** becomes the first argument in the list, so it is bound to `-Path`.</span></span>

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- <span data-ttu-id="c2fd7-174">De para meter voor de switch parameter `-Qualifier` niet positioneel instellen `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (bedankt @yecril71pl !)</span><span class="sxs-lookup"><span data-stu-id="c2fd7-174">Make the switch parameter `-Qualifier` not positional for `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (Thanks @yecril71pl!)</span></span>

- <span data-ttu-id="c2fd7-175">De werkmap omzetten als letterlijk pad voor `Start-Process` wanneer deze niet is opgegeven ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (bedankt @NoMoreFood !)</span><span class="sxs-lookup"><span data-stu-id="c2fd7-175">Resolve the working directory as literal path for `Start-Process` when it's not specified ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (Thanks @NoMoreFood!)</span></span>

- <span data-ttu-id="c2fd7-176">Stel de `-OutFile` para meter in Web-cmdlets als volgt `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="c2fd7-176">Make `-OutFile` parameter in web cmdlets to work like `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="c2fd7-177">Teken reeks parameter binding voor `BigInteger` numerieke letterlijke waarden ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) oplossen (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="c2fd7-177">Fix string parameter binding for `BigInteger` numeric literals ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (Thanks @vexx32!)</span></span>

- <span data-ttu-id="c2fd7-178">In Windows `Start-Process` maakt een proces omgeving met alle omgevings variabelen uit de huidige sessie, met behulp van `-UseNewEnvironment` een nieuwe standaard proces omgeving ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="c2fd7-178">On Windows, `Start-Process` creates a process environment with all the environment variables from current session, using `-UseNewEnvironment` creates a new default process environment ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="c2fd7-179">Retour resultaat niet laten teruglopen bij `PSObject` het converteren van een `ScriptBlock` naar een gemachtigde ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span><span class="sxs-lookup"><span data-stu-id="c2fd7-179">Do not wrap return result in `PSObject` when converting a `ScriptBlock` to a delegate ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span></span>

  <span data-ttu-id="c2fd7-180">Wanneer een `ScriptBlock` is geconverteerd naar een type gemachtigde dat moet worden gebruikt in de C#-context, wordt het resultaat in een niet- `PSObject` nood zakelijk probleem gewrappt:</span><span class="sxs-lookup"><span data-stu-id="c2fd7-180">When a `ScriptBlock` is converted to a delegate type to be used in C# context, wrapping the result in a `PSObject` brings unneeded troubles:</span></span>

  - <span data-ttu-id="c2fd7-181">Wanneer de waarde wordt geconverteerd naar het retour type van de gemachtigde, `PSObject` wordt in feite onverpakt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-181">When the value is converted to the delegate return type, the `PSObject` essentially gets unwrapped.</span></span> <span data-ttu-id="c2fd7-182">Het `PSObject` is dus niet nodig.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-182">So the `PSObject` is unneeded.</span></span>
  - <span data-ttu-id="c2fd7-183">Wanneer het retour type van de gemachtigde is `object` , wordt het verpakt in een gepakte manier `PSObject` om in C#-code te werken.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-183">When the delegate return type is `object`, it gets wrapped in a `PSObject` making it hard to work with in C# code.</span></span>

  <span data-ttu-id="c2fd7-184">Na deze wijziging is het geretourneerde object het onderliggende object.</span><span class="sxs-lookup"><span data-stu-id="c2fd7-184">After this change, the returned object is the underlying object.</span></span>
