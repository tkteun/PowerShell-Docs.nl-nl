---
ms.date: 02/03/2020
keywords: Power shell, kern
title: Belang rijke wijzigingen voor Power shell 6,0
ms.openlocfilehash: 47ed14cceed86e4dd04a8e0079af00f6a98988ea
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995451"
---
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="47728-103">Belang rijke wijzigingen voor Power shell 6. x</span><span class="sxs-lookup"><span data-stu-id="47728-103">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="47728-104">Functies die niet meer beschikbaar zijn in Power shell core</span><span class="sxs-lookup"><span data-stu-id="47728-104">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="47728-105">Modules die niet zijn verzonden voor Power shell 6. x</span><span class="sxs-lookup"><span data-stu-id="47728-105">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="47728-106">De volgende modules zijn niet voor verschillende compatibiliteits redenen opgenomen in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="47728-106">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="47728-107">ISE</span><span class="sxs-lookup"><span data-stu-id="47728-107">ISE</span></span>
- <span data-ttu-id="47728-108">Micro soft. Power shell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="47728-108">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="47728-109">Micro soft. Power shell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="47728-109">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="47728-110">Micro soft. Power shell. Operation. validatie</span><span class="sxs-lookup"><span data-stu-id="47728-110">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="47728-111">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="47728-111">PSScheduledJob</span></span>
- <span data-ttu-id="47728-112">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="47728-112">PSWorkflow</span></span>
- <span data-ttu-id="47728-113">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="47728-113">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="47728-114">PowerShell-werkstroom</span><span class="sxs-lookup"><span data-stu-id="47728-114">PowerShell Workflow</span></span>

<span data-ttu-id="47728-115">[Power shell workflow][workflow] is een functie in Windows Power shell die is gebaseerd op [Windows Workflow Foundation (WF)][workflow-foundation] waarmee robuuste runbooks kunnen worden gemaakt voor langdurige of geparalleleerde taken.</span><span class="sxs-lookup"><span data-stu-id="47728-115">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="47728-116">Vanwege het ontbreken van ondersteuning voor Windows Workflow Foundation in .NET core, bieden we geen ondersteuning voor Power shell-werk stroom in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="47728-116">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="47728-117">In de toekomst willen we native parallellisme/gelijktijdigheid inschakelen in de Power shell-taal zonder dat Power shell-werk stroom nodig is.</span><span class="sxs-lookup"><span data-stu-id="47728-117">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="47728-118">Als er een controle punt moet worden gebruikt om een script te hervatten nadat het besturings systeem opnieuw is opgestart, raden we u aan taak planner te gebruiken om een script uit te voeren op het opstarten van het besturings systeem, maar moet het script een eigen status behouden (zoals het persistent maken van een bestand).</span><span class="sxs-lookup"><span data-stu-id="47728-118">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="47728-119">Aangepaste modules</span><span class="sxs-lookup"><span data-stu-id="47728-119">Custom snap-ins</span></span>

<span data-ttu-id="47728-120">[Power shell-][snapin] modules zijn een voorganger van Power shell-modules die geen uitgebreide aanneming hebben in de Power shell-community.</span><span class="sxs-lookup"><span data-stu-id="47728-120">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="47728-121">Vanwege de complexiteit van ondersteunende modules en het ontbreken van gebruik in de Community ondersteunen we geen aangepaste modules meer in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="47728-121">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="47728-122">Nu worden de `ActiveDirectory`-en `DnsClient`-modules in Windows en Windows Server onderbroken.</span><span class="sxs-lookup"><span data-stu-id="47728-122">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="47728-123">WMI v1-cmdlets</span><span class="sxs-lookup"><span data-stu-id="47728-123">WMI v1 cmdlets</span></span>

<span data-ttu-id="47728-124">Vanwege de complexiteit van het ondersteunen van twee sets WMI-modules, hebben we de WMI v1-cmdlets uit Power shell core verwijderd:</span><span class="sxs-lookup"><span data-stu-id="47728-124">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="47728-125">In plaats daarvan wordt u aangeraden de CIM-cmdlets (ook wel WMI v2) te gebruiken die dezelfde functionaliteit bieden als nieuwe functionaliteit en een opnieuw ontworpen syntaxis:</span><span class="sxs-lookup"><span data-stu-id="47728-125">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="47728-126">Micro soft. Power shell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="47728-126">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="47728-127">Als gevolg van het gebruik van niet-ondersteunde Api's, is `Microsoft.PowerShell.LocalAccounts` verwijderd uit Power shell core totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="47728-127">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="47728-128">`New-WebServiceProxy`-cmdlet verwijderd</span><span class="sxs-lookup"><span data-stu-id="47728-128">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="47728-129">.NET core biedt geen ondersteuning voor het Windows Communication Framework, dat services biedt voor het gebruik van het SOAP-protocol.</span><span class="sxs-lookup"><span data-stu-id="47728-129">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="47728-130">Deze cmdlet is verwijderd omdat SOAP is vereist.</span><span class="sxs-lookup"><span data-stu-id="47728-130">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="47728-131">`*-Transaction` cmdlets verwijderd</span><span class="sxs-lookup"><span data-stu-id="47728-131">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="47728-132">Deze cmdlets hebben een zeer beperkt gebruik.</span><span class="sxs-lookup"><span data-stu-id="47728-132">These cmdlets had very limited usage.</span></span> <span data-ttu-id="47728-133">De beslissing is genomen om de ondersteuning voor hen te stoppen.</span><span class="sxs-lookup"><span data-stu-id="47728-133">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="47728-134">Beveiligings-cmdlets die niet beschikbaar zijn op niet-Windows-platforms</span><span class="sxs-lookup"><span data-stu-id="47728-134">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="47728-135">`*-Computer`en andere Windows-specifieke cmdlets</span><span class="sxs-lookup"><span data-stu-id="47728-135">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="47728-136">Als gevolg van het gebruik van niet-ondersteunde Api's, zijn de volgende cmdlets uit Power shell core verwijderd totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="47728-136">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a><span data-ttu-id="47728-137">`*-Counter`-cmdlets</span><span class="sxs-lookup"><span data-stu-id="47728-137">`*-Counter` cmdlets</span></span>

<span data-ttu-id="47728-138">Als gevolg van het gebruik van niet-ondersteunde Api's, is het `*-Counter` verwijderd uit Power shell core totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="47728-138">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="47728-139">`*-EventLog`-cmdlets</span><span class="sxs-lookup"><span data-stu-id="47728-139">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="47728-140">Als gevolg van het gebruik van niet-ondersteunde Api's, is het `*-EventLog` verwijderd uit Power shell core.</span><span class="sxs-lookup"><span data-stu-id="47728-140">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="47728-141">totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="47728-141">until a better solution is found.</span></span> <span data-ttu-id="47728-142">`Get-WinEvent` en `Create-WinEvent` zijn beschikbaar voor het ophalen en maken van gebeurtenissen in Windows.</span><span class="sxs-lookup"><span data-stu-id="47728-142">`Get-WinEvent` and `Create-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="47728-143">Cmdlets die gebruikmaken van WPF verwijderd</span><span class="sxs-lookup"><span data-stu-id="47728-143">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="47728-144">Het Windows Presentation Framework wordt niet ondersteund op CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="47728-144">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="47728-145">De volgende cmdlets worden beïnvloed:</span><span class="sxs-lookup"><span data-stu-id="47728-145">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="47728-146">De **ShowWindow** -para meter van `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="47728-146">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="47728-147">Sommige DSC-cmdlets zijn verwijderd</span><span class="sxs-lookup"><span data-stu-id="47728-147">Some DSC cmdlets removed</span></span>

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a><span data-ttu-id="47728-148">Wijzigingen in de engine/taal</span><span class="sxs-lookup"><span data-stu-id="47728-148">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a><span data-ttu-id="47728-149">Wijzig de naam van `powershell.exe` in `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="47728-149">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="47728-150">Om gebruikers een deterministische manier te geven om Power shell core aan te roepen in Windows (in plaats van Windows Power shell), is het binaire bestand van Power shell core gewijzigd in `pwsh.exe` op Windows en `pwsh` op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="47728-150">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="47728-151">De kortere naam is ook consistent met de naamgeving van shells op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="47728-151">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a><span data-ttu-id="47728-152">Geen regel einden invoegen in uitvoer (met uitzonde ring van tabellen) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="47728-152">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="47728-153">Voorheen werd de uitvoer uitgelijnd op de breedte van de console en worden er regel einden toegevoegd aan de eind breedte van de console, wat betekent dat de uitvoer niet opnieuw is ingedeeld zoals verwacht als de grootte van de Terminal is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="47728-153">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="47728-154">Deze wijziging is niet toegepast op tabellen, omdat de regel einden nood zakelijk zijn om de kolommen uitgelijnd te laten worden.</span><span class="sxs-lookup"><span data-stu-id="47728-154">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a><span data-ttu-id="47728-155">Null-element controle overs laan voor verzamelingen met een waarde type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="47728-155">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="47728-156">Voor de para meter `Mandatory` en de kenmerken `ValidateNotNull` en `ValidateNotNullOrEmpty` slaat u de null-element controle uit als het element type van de verzameling het waardetype is.</span><span class="sxs-lookup"><span data-stu-id="47728-156">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a><span data-ttu-id="47728-157">Wijzig `$OutputEncoding` om `UTF-8 NoBOM` code ring te gebruiken in plaats van ASCII- [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="47728-157">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="47728-158">De vorige code ring, ASCII (7-bits), resulteert in sommige gevallen in een onjuiste wijziging van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="47728-158">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="47728-159">Deze wijziging is het maken van `UTF-8 NoBOM` standaard, waarmee Unicode-uitvoer wordt bewaard met een code ring die door de meeste hulpprogram ma's en besturings systemen wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="47728-159">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a><span data-ttu-id="47728-160">Verwijder `AllScope` van de meeste standaard aliassen [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="47728-160">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="47728-161">Om het maken van het bereik te versnellen, is `AllScope` verwijderd uit de meeste standaard aliassen.</span><span class="sxs-lookup"><span data-stu-id="47728-161">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="47728-162">`AllScope` is overgebleven voor een aantal veelgebruikte aliassen waarbij de zoek opdracht sneller is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="47728-162">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a><span data-ttu-id="47728-163">`-Verbose` en `-Debug` worden niet meer overschreven `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="47728-163">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="47728-164">Voorheen, als `-Verbose` of `-Debug` zijn opgegeven, overrode het gedrag van `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="47728-164">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="47728-165">Met deze wijziging zijn `-Verbose` en `-Debug` niet langer van invloed op het gedrag van `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="47728-165">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="47728-166">Cmdlet-wijzigingen</span><span class="sxs-lookup"><span data-stu-id="47728-166">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a><span data-ttu-id="47728-167">Invoke-RestMethod retourneert geen nuttige informatie wanneer er geen gegevens worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="47728-167">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="47728-168">#5320</span><span class="sxs-lookup"><span data-stu-id="47728-168">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="47728-169">Wanneer een API wordt geretourneerd alleen `null`, werd invoke-RestMethod als teken `"null"` reeks geserialiseerd in plaats van `$null`.</span><span class="sxs-lookup"><span data-stu-id="47728-169">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="47728-170">Deze wijziging corrigeert de logica in `Invoke-RestMethod` om een geldige JSON van een logische `null` waarde te serialiseren als `$null`.</span><span class="sxs-lookup"><span data-stu-id="47728-170">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a><span data-ttu-id="47728-171">`-Protocol` verwijderen uit `*-Computer`-cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="47728-171">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="47728-172">Als gevolg van problemen met RPC-externe toegang in CoreFX (met name op niet-Windows-platforms) en het garanderen van een consistente externe ervaring in Power shell, is de para meter `-Protocol` verwijderd uit de `\*-Computer`-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="47728-172">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="47728-173">DCOM wordt niet meer ondersteund voor externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="47728-173">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="47728-174">De volgende cmdlets bieden alleen ondersteuning voor externe WSMAN-communicatie:</span><span class="sxs-lookup"><span data-stu-id="47728-174">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="47728-175">Naam wijzigen-computer</span><span class="sxs-lookup"><span data-stu-id="47728-175">Rename-Computer</span></span>
- <span data-ttu-id="47728-176">Opnieuw opstarten-computer</span><span class="sxs-lookup"><span data-stu-id="47728-176">Restart-Computer</span></span>
- <span data-ttu-id="47728-177">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="47728-177">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a><span data-ttu-id="47728-178">`-ComputerName` verwijderen uit `*-Service`-cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="47728-178">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="47728-179">Om het consistente gebruik van PSRP te stimuleren, is de para meter `-ComputerName` verwijderd uit `*-Service`-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="47728-179">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a><span data-ttu-id="47728-180">Herstel `Get-Item -LiteralPath a*b` als `a*b` niet echt bestaat om fout te retour neren [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="47728-180">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="47728-181">Voorheen zou `-LiteralPath` op basis van een Joker teken hetzelfde doen als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten.</span><span class="sxs-lookup"><span data-stu-id="47728-181">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="47728-182">Het juiste gedrag is dat `-LiteralPath` een letterlijke waarde heeft, zodat het een fout moet zijn als het bestand niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="47728-182">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="47728-183">Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.</span><span class="sxs-lookup"><span data-stu-id="47728-183">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a><span data-ttu-id="47728-184">`Import-Csv` moet `PSTypeNames` Toep assen bij het importeren wanneer type gegevens aanwezig zijn in het CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="47728-184">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="47728-185">Voorheen behouden objecten die zijn geëxporteerd met `Export-CSV` met `TypeInformation` geïmporteerd met `ConvertFrom-Csv` de type gegevens niet.</span><span class="sxs-lookup"><span data-stu-id="47728-185">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="47728-186">Met deze wijziging wordt de type-informatie aan `PSTypeNames` lid toegevoegd als deze beschikbaar is vanuit het CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="47728-186">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a><span data-ttu-id="47728-187">`-NoTypeInformation` moet standaard zijn op `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="47728-187">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="47728-188">Deze wijziging is doorgevoerd om de feedback van klanten te verhelpen over het standaard gedrag van `Export-CSV` om type gegevens op te nemen.</span><span class="sxs-lookup"><span data-stu-id="47728-188">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="47728-189">Voorheen voert de cmdlet een opmerking uit als de eerste regel met de type naam van het object.</span><span class="sxs-lookup"><span data-stu-id="47728-189">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="47728-190">De wijziging is het onderdrukken van deze standaard instelling, omdat deze niet wordt begrepen door de meeste hulpprogram ma's.</span><span class="sxs-lookup"><span data-stu-id="47728-190">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="47728-191">Gebruik `-IncludeTypeInformation` om het vorige gedrag te bewaren.</span><span class="sxs-lookup"><span data-stu-id="47728-191">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a><span data-ttu-id="47728-192">Web-cmdlets moeten worden gewaarschuwd wanneer `-Credential` wordt verzonden via niet-versleutelde verbindingen [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="47728-192">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="47728-193">Wanneer u HTTP gebruikt, worden inhoud, inclusief wacht woorden, verzonden als ongecodeerde tekst.</span><span class="sxs-lookup"><span data-stu-id="47728-193">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="47728-194">Deze wijziging is het is niet toegestaan dit standaard te voor komen en een fout te retour neren als de referenties op een onveilige manier worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="47728-194">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="47728-195">Gebruikers kunnen dit omzeilen door gebruik te maken van de `-AllowUnencryptedAuthentication` switch.</span><span class="sxs-lookup"><span data-stu-id="47728-195">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="47728-196">API-wijzigingen</span><span class="sxs-lookup"><span data-stu-id="47728-196">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a><span data-ttu-id="47728-197">`AddTypeCommandBase` klasse verwijderen [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="47728-197">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="47728-198">De `AddTypeCommandBase` klasse is verwijderd uit `Add-Type` om de prestaties te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="47728-198">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="47728-199">Deze klasse wordt alleen gebruikt door de cmdlet Add-type en mag geen invloed hebben op gebruikers.</span><span class="sxs-lookup"><span data-stu-id="47728-199">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a><span data-ttu-id="47728-200">Verenigen cmdlets met para meter `-Encoding` van het type `System.Text.Encoding` zijn [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="47728-200">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="47728-201">De `-Encoding` waarde `Byte` is verwijderd uit de cmdlets van het bestands systeem provider.</span><span class="sxs-lookup"><span data-stu-id="47728-201">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="47728-202">Er wordt nu een nieuwe para meter, `-AsByteStream`, gebruikt om op te geven dat een byte stroom als invoer is vereist of dat de uitvoer een stroom van bytes is.</span><span class="sxs-lookup"><span data-stu-id="47728-202">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a><span data-ttu-id="47728-203">Een beter fout bericht toevoegen voor een lege `-UFormat`-para meter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="47728-203">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="47728-204">Wanneer een lege indelings teken reeks wordt door gegeven aan `-UFormat`, wordt een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="47728-204">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="47728-205">Er is een meer beschrijvende fout toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="47728-205">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a><span data-ttu-id="47728-206">Console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995) opschonen</span><span class="sxs-lookup"><span data-stu-id="47728-206">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="47728-207">De volgende functies zijn verwijderd omdat ze niet worden ondersteund in Power shell core en er zijn geen plannen om ondersteuning toe te voegen, omdat deze bestaan voor verouderde redenen voor Windows Power shell: `-psconsolefile` switch en code, `-importsystemmodules` switch en code, en het wijzigen van de code.</span><span class="sxs-lookup"><span data-stu-id="47728-207">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a><span data-ttu-id="47728-208">`RunspaceConfiguration` ondersteunings [#4942](https://github.com/PowerShell/PowerShell/issues/4942) is verwijderd</span><span class="sxs-lookup"><span data-stu-id="47728-208">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="47728-209">Wanneer u een Power shell-runs Pace programmatisch maakt met behulp van de API, kunt u de verouderde [`RunspaceConfiguration`][runspaceconfig] of de nieuwere [`InitialSessionState`][iss]gebruiken.</span><span class="sxs-lookup"><span data-stu-id="47728-209">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="47728-210">Deze wijziging heeft ondersteuning voor `RunspaceConfiguration` verwijderd en ondersteunt alleen `InitialSessionState`.</span><span class="sxs-lookup"><span data-stu-id="47728-210">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a><span data-ttu-id="47728-211">`CommandInvocationIntrinsics.InvokeScript` BIND argumenten aan `$input` in plaats van `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="47728-211">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="47728-212">Een onjuiste positie van een para meter resulteerde in de argumenten die zijn door gegeven als invoer in plaats van als argumenten.</span><span class="sxs-lookup"><span data-stu-id="47728-212">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a><span data-ttu-id="47728-213">Verwijder de niet-ondersteunde `-showwindow` switch van `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="47728-213">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="47728-214">`-showwindow` is afhankelijk van WPF, wat niet wordt ondersteund op CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="47728-214">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a><span data-ttu-id="47728-215">Toestaan dat \* wordt gebruikt in het registerpad voor `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="47728-215">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="47728-216">Voorheen zou `-LiteralPath` op basis van een Joker teken hetzelfde doen als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten.</span><span class="sxs-lookup"><span data-stu-id="47728-216">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="47728-217">Het juiste gedrag is dat `-LiteralPath` een letterlijke waarde heeft, zodat het een fout moet zijn als het bestand niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="47728-217">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="47728-218">Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.</span><span class="sxs-lookup"><span data-stu-id="47728-218">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a><span data-ttu-id="47728-219">Fix `Set-Service` mislukte test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="47728-219">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="47728-220">Als `New-Service -StartupType foo` eerder is gebruikt, wordt `foo` genegeerd en is de service gemaakt met een standaard opstart type.</span><span class="sxs-lookup"><span data-stu-id="47728-220">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="47728-221">Deze wijziging is het expliciet genereren van een fout voor een ongeldig opstart type.</span><span class="sxs-lookup"><span data-stu-id="47728-221">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a><span data-ttu-id="47728-222">Wijzig de naam van `$IsOSX` in `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="47728-222">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="47728-223">De naamgeving in Power shell moet consistent zijn met de naamgeving en voldoen aan het gebruik van macOS in plaats van OSX.</span><span class="sxs-lookup"><span data-stu-id="47728-223">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="47728-224">Voor de Lees baarheid en consistent wordt er echter geadviseerd dat de Pascal-behuizing.</span><span class="sxs-lookup"><span data-stu-id="47728-224">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a><span data-ttu-id="47728-225">Fout bericht consistent maken wanneer ongeldig script wordt door gegeven aan-bestand, betere fout bij het door geven van een dubbel zinnig argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="47728-225">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="47728-226">De afsluit codes van `pwsh.exe` wijzigen in uitlijnen met UNIX-conventies</span><span class="sxs-lookup"><span data-stu-id="47728-226">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a><span data-ttu-id="47728-227">Het verwijderen van `LocalAccount` en cmdlets van `Diagnostics` modules.</span><span class="sxs-lookup"><span data-stu-id="47728-227">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="47728-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="47728-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="47728-229">Als gevolg van niet-ondersteunde Api's, zijn de `LocalAccounts`-module en de `Counter`-cmdlets in de `Diagnostics`-module verwijderd totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="47728-229">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a><span data-ttu-id="47728-230">Het uitvoeren van een Power shell-script met de BOOL-para meter werkt niet [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="47728-230">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="47728-231">Voorheen werd het gebruik van **Power shell. exe** (nu **pwsh. exe**) uitgevoerd om een Power shell-script uit te voeren met `-File` zonder dat u `$true`/`$false` als parameter waarden kunt door geven.</span><span class="sxs-lookup"><span data-stu-id="47728-231">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="47728-232">Ondersteuning voor `$true`/`$false` als geparseerde waarden aan para meters is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="47728-232">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="47728-233">Switch waarden worden ook ondersteund, omdat de syntaxis die momenteel wordt beschreven, niet werkt.</span><span class="sxs-lookup"><span data-stu-id="47728-233">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a><span data-ttu-id="47728-234">`ClrVersion` eigenschap verwijderen uit `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="47728-234">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="47728-235">De eigenschap `ClrVersion` van `$PSVersionTable` is niet nuttig met CoreCLR. eind gebruikers moeten deze waarde niet gebruiken om de compatibiliteit te bepalen.</span><span class="sxs-lookup"><span data-stu-id="47728-235">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a><span data-ttu-id="47728-236">Positionele para meter voor `powershell.exe` van `-Command` wijzigen in `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="47728-236">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="47728-237">Schakel het shebang-gebruik van Power shell in op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="47728-237">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="47728-238">Dit betekent dat u op UNIX gebaseerde systemen een uitvoerbaar script kunt maken dat Power shell automatisch aanroept in plaats van `pwsh`expliciet aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="47728-238">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="47728-239">Dit betekent ook dat u nu dingen als `powershell foo.ps1` of `powershell fooScript` kunt doen zonder `-File`op te geven.</span><span class="sxs-lookup"><span data-stu-id="47728-239">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="47728-240">Voor deze wijziging moet u echter expliciet `-c` of `-Command` opgeven bij het uitvoeren van dingen als `powershell.exe Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="47728-240">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a><span data-ttu-id="47728-241">[#3958](https://github.com/PowerShell/PowerShell/issues/3958) voor het parseren van Unicode-escape implementeren</span><span class="sxs-lookup"><span data-stu-id="47728-241">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="47728-242">`` `u####`` of `` `u{####}`` wordt geconverteerd naar het bijbehorende Unicode-teken.</span><span class="sxs-lookup"><span data-stu-id="47728-242">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="47728-243">Als u een letterlijke `` `u``wilt uitvoeren, sluit u de apostroffen: ``` ``u```.</span><span class="sxs-lookup"><span data-stu-id="47728-243">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a><span data-ttu-id="47728-244">`New-ModuleManifest` code ring wijzigen in `UTF8NoBOM` op niet-Windows-platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="47728-244">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="47728-245">Voorheen maakt `New-ModuleManifest` psd1-manifesten in UTF-16 met stuk lijst en maakt u een probleem voor Linux-hulpprogram ma's.</span><span class="sxs-lookup"><span data-stu-id="47728-245">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="47728-246">Door deze wijziging wordt de code ring van `New-ModuleManifest` gewijzigd in UTF (geen stuk lijst) in niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="47728-246">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a><span data-ttu-id="47728-247">Voor komen dat `Get-ChildItem` worden herhaald in symlinks (#1875).</span><span class="sxs-lookup"><span data-stu-id="47728-247">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="47728-248">#3780</span><span class="sxs-lookup"><span data-stu-id="47728-248">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="47728-249">Deze wijziging brengt `Get-ChildItem` meer in overeenstemming met de UNIX-`ls -r` en de Windows `dir /s` systeem eigen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="47728-249">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="47728-250">Net als de vermelde opdrachten worden met de cmdlet symbolische koppelingen weer gegeven naar directory's die tijdens recursie zijn gevonden, maar worden ze niet herhaald.</span><span class="sxs-lookup"><span data-stu-id="47728-250">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a><span data-ttu-id="47728-251">Corrigeer `Get-Content -Delimiter` zodat het scheidings teken niet in de geretourneerde regels wordt vermeld [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="47728-251">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="47728-252">Voorheen was de uitvoer tijdens het gebruik van `Get-Content -Delimiter` inconsistent en onhandig omdat het verdere verwerking van de gegevens nodig was om het scheidings teken te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="47728-252">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="47728-253">Met deze wijziging verwijdert u het scheidings teken in geretourneerde regels.</span><span class="sxs-lookup"><span data-stu-id="47728-253">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a><span data-ttu-id="47728-254">Indeling-hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320) implementeren</span><span class="sxs-lookup"><span data-stu-id="47728-254">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="47728-255">De para meter `-Raw` is nu een ' Nee-op ' (in dat geval gebeurt er niets).</span><span class="sxs-lookup"><span data-stu-id="47728-255">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="47728-256">Alle uitvoer wordt weer gegeven met een echte representatie van getallen die alle bytes voor het type bevat (waarvoor de para meter `-Raw` formeel vóór deze wijziging werd uitgevoerd).</span><span class="sxs-lookup"><span data-stu-id="47728-256">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a><span data-ttu-id="47728-257">Power shell werkt als standaard shell niet met script opdracht [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="47728-257">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="47728-258">In UNIX is het een Conventie voor houders om `-i` te accepteren voor een interactieve shell en veel hulp middelen verwachten dit gedrag (`script` bijvoorbeeld en wanneer Power shell als de standaard shell wordt ingesteld) en wordt de shell aangeroepen met de `-i` switch.</span><span class="sxs-lookup"><span data-stu-id="47728-258">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="47728-259">Deze wijziging is opgesplitst in dat `-i` eerder als korte hand zou kunnen worden gebruikt om te voldoen aan `-inputformat`, die nu moet worden `-in`.</span><span class="sxs-lookup"><span data-stu-id="47728-259">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a><span data-ttu-id="47728-260">Type correctie in Get-ComputerInfo eigenschap name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="47728-260">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="47728-261">`BiosSerialNumber` verkeerd gespeld als `BiosSeralNumber` en is gewijzigd in de juiste spelling.</span><span class="sxs-lookup"><span data-stu-id="47728-261">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a><span data-ttu-id="47728-262">`Get-StringHash`-en `Get-FileHash`-cmdlets toevoegen [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="47728-262">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="47728-263">Deze wijziging is dat sommige hash-algoritmen niet worden ondersteund door CoreFX, dus zijn ze niet meer beschikbaar:</span><span class="sxs-lookup"><span data-stu-id="47728-263">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a><span data-ttu-id="47728-264">Validatie toevoegen bij `Get-*`-cmdlets waarbij het door geven van $null alle objecten retourneert in plaats van fout [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="47728-264">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="47728-265">Als `$null` wordt door gegeven aan een van de volgende, wordt een fout gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="47728-265">Passing `$null` to any of the following now throws an error:</span></span>

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a><span data-ttu-id="47728-266">De uitgebreide W3C-indeling voor logboek bestanden toevoegen in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="47728-266">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="47728-267">Voorheen kan de cmdlet `Import-Csv` niet worden gebruikt om de logboek bestanden rechtstreeks te importeren in de uitgebreide W3C-logboek indeling en dat er extra actie moet worden ondernomen.</span><span class="sxs-lookup"><span data-stu-id="47728-267">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="47728-268">Met deze wijziging wordt de uitgebreide W3C-logboek indeling ondersteund.</span><span class="sxs-lookup"><span data-stu-id="47728-268">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a><span data-ttu-id="47728-269">Fout bij het binden van de para meter met `ValueFromRemainingArguments` in PS-functies [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="47728-269">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="47728-270">`ValueFromRemainingArguments` retourneert nu de waarden als een matrix in plaats van een enkele waarde die zelf een matrix is.</span><span class="sxs-lookup"><span data-stu-id="47728-270">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a><span data-ttu-id="47728-271">`BuildVersion` is uit `$PSVersionTable` verwijderd [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="47728-271">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="47728-272">Verwijder de eigenschap `BuildVersion` van `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="47728-272">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="47728-273">Deze eigenschap is gekoppeld aan de Windows-build-versie.</span><span class="sxs-lookup"><span data-stu-id="47728-273">This property was tied to the Windows build version.</span></span> <span data-ttu-id="47728-274">In plaats daarvan raden we u aan `GitCommitId` te gebruiken om de exacte build-versie van Power shell Core op te halen.</span><span class="sxs-lookup"><span data-stu-id="47728-274">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="47728-275">Wijzigingen in Web-cmdlets</span><span class="sxs-lookup"><span data-stu-id="47728-275">Changes to Web Cmdlets</span></span>

<span data-ttu-id="47728-276">De onderliggende .NET API van de Web-cmdlets is gewijzigd in `System.Net.Http.HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="47728-276">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="47728-277">Deze wijziging biedt veel voor delen.</span><span class="sxs-lookup"><span data-stu-id="47728-277">This change provides many benefits.</span></span> <span data-ttu-id="47728-278">Deze wijziging in combi natie met een gebrek aan interoperabiliteit met Internet Explorer heeft geresulteerd in verschillende belang rijke wijzigingen in `Invoke-WebRequest` en `Invoke-RestMethod`.</span><span class="sxs-lookup"><span data-stu-id="47728-278">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="47728-279">`Invoke-WebRequest` ondersteunt nu alleen eenvoudige HTML-parsering.</span><span class="sxs-lookup"><span data-stu-id="47728-279">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="47728-280">`Invoke-WebRequest` retourneert altijd een `BasicHtmlWebResponseObject`-object.</span><span class="sxs-lookup"><span data-stu-id="47728-280">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="47728-281">De eigenschappen `ParsedHtml` en `Forms` zijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="47728-281">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="47728-282">`BasicHtmlWebResponseObject.Headers` waarden zijn nu `String[]` in plaats van `String`.</span><span class="sxs-lookup"><span data-stu-id="47728-282">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="47728-283">`BasicHtmlWebResponseObject.BaseResponse` is nu een `System.Net.Http.HttpResponseMessage`-object.</span><span class="sxs-lookup"><span data-stu-id="47728-283">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="47728-284">De eigenschap `Response` op Web cmdlet Exceptions is nu een `System.Net.Http.HttpResponseMessage`-object.</span><span class="sxs-lookup"><span data-stu-id="47728-284">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="47728-285">Strikte RFC-header parseren is nu standaard voor de para meter `-Headers` en `-UserAgent`.</span><span class="sxs-lookup"><span data-stu-id="47728-285">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="47728-286">Dit kan worden overgeslagen met `-SkipHeaderValidation`.</span><span class="sxs-lookup"><span data-stu-id="47728-286">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="47728-287">`file://`-en `ftp://` URI-schema's worden niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="47728-287">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="47728-288">`System.Net.ServicePointManager`-instellingen worden niet meer nageleefd.</span><span class="sxs-lookup"><span data-stu-id="47728-288">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="47728-289">Er is momenteel geen authenticatie op basis van certificaten beschikbaar in macOS.</span><span class="sxs-lookup"><span data-stu-id="47728-289">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="47728-290">Het gebruik van `-Credential` over een `http://` URI resulteert in een fout.</span><span class="sxs-lookup"><span data-stu-id="47728-290">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="47728-291">Gebruik een `https://` URI of geef de para meter `-AllowUnencryptedAuthentication` op om de fout te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="47728-291">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="47728-292">`-MaximumRedirection` maakt nu een afsluit fout als de omleidings pogingen de gegeven limiet overschrijden in plaats van de resultaten van de laatste omleiding te retour neren.</span><span class="sxs-lookup"><span data-stu-id="47728-292">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="47728-293">In Power shell 6,2 is een wijziging aangebracht in UTF-8-code ring voor JSON-reacties.</span><span class="sxs-lookup"><span data-stu-id="47728-293">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="47728-294">Wanneer een charset niet wordt opgegeven voor een JSON-antwoord, moet de standaard codering UTF-8 zijn per RFC 8259.</span><span class="sxs-lookup"><span data-stu-id="47728-294">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
