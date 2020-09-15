---
ms.date: 02/03/2020
keywords: Power shell, kern
title: Belang rijke wijzigingen voor Power shell 6,0
ms.openlocfilehash: 9ead635232930598634141369fd2cc299f0b1799
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158187"
---
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="0813d-103">Belang rijke wijzigingen voor Power shell 6. x</span><span class="sxs-lookup"><span data-stu-id="0813d-103">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="0813d-104">Functies die niet meer beschikbaar zijn in Power shell core</span><span class="sxs-lookup"><span data-stu-id="0813d-104">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="0813d-105">Modules die niet zijn verzonden voor Power shell 6. x</span><span class="sxs-lookup"><span data-stu-id="0813d-105">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="0813d-106">De volgende modules zijn niet voor verschillende compatibiliteits redenen opgenomen in Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="0813d-106">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="0813d-107">ISE</span><span class="sxs-lookup"><span data-stu-id="0813d-107">ISE</span></span>
- <span data-ttu-id="0813d-108">Micro soft. Power shell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="0813d-108">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="0813d-109">Micro soft. Power shell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="0813d-109">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="0813d-110">Micro soft. Power shell. Operation. validatie</span><span class="sxs-lookup"><span data-stu-id="0813d-110">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="0813d-111">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="0813d-111">PSScheduledJob</span></span>
- <span data-ttu-id="0813d-112">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="0813d-112">PSWorkflow</span></span>
- <span data-ttu-id="0813d-113">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="0813d-113">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="0813d-114">PowerShell-werkstroom</span><span class="sxs-lookup"><span data-stu-id="0813d-114">PowerShell Workflow</span></span>

<span data-ttu-id="0813d-115">[Power shell workflow][workflow] is een functie in Windows Power shell die is gebaseerd op [Windows Workflow Foundation (WF)][workflow-foundation] waarmee robuuste runbooks kunnen worden gemaakt voor langdurige of geparalleleerde taken.</span><span class="sxs-lookup"><span data-stu-id="0813d-115">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="0813d-116">Vanwege het ontbreken van ondersteuning voor Windows Workflow Foundation in .NET core, bieden we geen ondersteuning voor Power shell-werk stroom in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="0813d-116">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="0813d-117">In de toekomst willen we native parallellisme/gelijktijdigheid inschakelen in de Power shell-taal zonder dat Power shell-werk stroom nodig is.</span><span class="sxs-lookup"><span data-stu-id="0813d-117">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="0813d-118">Als er een controle punt moet worden gebruikt om een script te hervatten nadat het besturings systeem opnieuw is opgestart, raden we u aan taak planner te gebruiken om een script uit te voeren op het opstarten van het besturings systeem, maar moet het script een eigen status behouden (zoals het persistent maken van een bestand).</span><span class="sxs-lookup"><span data-stu-id="0813d-118">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /previous-versions/powershell/scripting/components/workflows-guide
[workflow-foundation]: /dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="0813d-119">Aangepaste modules</span><span class="sxs-lookup"><span data-stu-id="0813d-119">Custom snap-ins</span></span>

<span data-ttu-id="0813d-120">[Power shell-][snapin] modules zijn een voorganger van Power shell-modules die geen uitgebreide aanneming hebben in de Power shell-community.</span><span class="sxs-lookup"><span data-stu-id="0813d-120">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="0813d-121">Vanwege de complexiteit van ondersteunende modules en het ontbreken van gebruik in de Community ondersteunen we geen aangepaste modules meer in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="0813d-121">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="0813d-122">Nu worden de `ActiveDirectory` `DnsClient` modules en in Windows en Windows Server onderbroken.</span><span class="sxs-lookup"><span data-stu-id="0813d-122">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: /powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="0813d-123">WMI v1-cmdlets</span><span class="sxs-lookup"><span data-stu-id="0813d-123">WMI v1 cmdlets</span></span>

<span data-ttu-id="0813d-124">Vanwege de complexiteit van het ondersteunen van twee sets WMI-modules, hebben we de WMI v1-cmdlets uit Power shell core verwijderd:</span><span class="sxs-lookup"><span data-stu-id="0813d-124">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="0813d-125">In plaats daarvan wordt u aangeraden de CIM-cmdlets (ook wel WMI v2) te gebruiken die dezelfde functionaliteit bieden als nieuwe functionaliteit en een opnieuw ontworpen syntaxis:</span><span class="sxs-lookup"><span data-stu-id="0813d-125">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

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

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="0813d-126">Micro soft. Power shell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="0813d-126">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="0813d-127">Als gevolg van het gebruik van niet-ondersteunde Api's, `Microsoft.PowerShell.LocalAccounts` is verwijderd uit Power shell core totdat een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="0813d-127">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="0813d-128">`New-WebServiceProxy` cmdlet verwijderd</span><span class="sxs-lookup"><span data-stu-id="0813d-128">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="0813d-129">.NET core biedt geen ondersteuning voor het Windows Communication Framework, dat services biedt voor het gebruik van het SOAP-protocol.</span><span class="sxs-lookup"><span data-stu-id="0813d-129">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="0813d-130">Deze cmdlet is verwijderd omdat SOAP is vereist.</span><span class="sxs-lookup"><span data-stu-id="0813d-130">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="0813d-131">`*-Transaction` cmdlets verwijderd</span><span class="sxs-lookup"><span data-stu-id="0813d-131">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="0813d-132">Deze cmdlets hebben een zeer beperkt gebruik.</span><span class="sxs-lookup"><span data-stu-id="0813d-132">These cmdlets had very limited usage.</span></span> <span data-ttu-id="0813d-133">De beslissing is genomen om de ondersteuning voor hen te stoppen.</span><span class="sxs-lookup"><span data-stu-id="0813d-133">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="0813d-134">Beveiligings-cmdlets die niet beschikbaar zijn op niet-Windows-platforms</span><span class="sxs-lookup"><span data-stu-id="0813d-134">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="0813d-135">`*-Computer`en andere Windows-specifieke cmdlets</span><span class="sxs-lookup"><span data-stu-id="0813d-135">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="0813d-136">Als gevolg van het gebruik van niet-ondersteunde Api's, zijn de volgende cmdlets uit Power shell core verwijderd totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="0813d-136">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

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

### <a name="-counter-cmdlets"></a><span data-ttu-id="0813d-137">`*-Counter` cmdlets</span><span class="sxs-lookup"><span data-stu-id="0813d-137">`*-Counter` cmdlets</span></span>

<span data-ttu-id="0813d-138">Als gevolg van het gebruik van niet-ondersteunde Api's, `*-Counter` is het uit Power shell core verwijderd totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="0813d-138">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="0813d-139">`*-EventLog` cmdlets</span><span class="sxs-lookup"><span data-stu-id="0813d-139">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="0813d-140">Als gevolg van het gebruik van niet-ondersteunde Api's, `*-EventLog` is het verwijderd uit Power shell core.</span><span class="sxs-lookup"><span data-stu-id="0813d-140">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="0813d-141">totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="0813d-141">until a better solution is found.</span></span> <span data-ttu-id="0813d-142">`Get-WinEvent` en `Create-WinEvent` zijn beschikbaar voor het ophalen en maken van gebeurtenissen in Windows.</span><span class="sxs-lookup"><span data-stu-id="0813d-142">`Get-WinEvent` and `Create-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="0813d-143">Cmdlets die gebruikmaken van WPF verwijderd</span><span class="sxs-lookup"><span data-stu-id="0813d-143">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="0813d-144">Het Windows Presentation Framework wordt niet ondersteund op CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0813d-144">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="0813d-145">De volgende cmdlets worden beïnvloed:</span><span class="sxs-lookup"><span data-stu-id="0813d-145">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="0813d-146">De **ShowWindow** -para meter van `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="0813d-146">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="0813d-147">Sommige DSC-cmdlets zijn verwijderd</span><span class="sxs-lookup"><span data-stu-id="0813d-147">Some DSC cmdlets removed</span></span>

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

## <a name="enginelanguage-changes"></a><span data-ttu-id="0813d-148">Wijzigingen in de engine/taal</span><span class="sxs-lookup"><span data-stu-id="0813d-148">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101"></a><span data-ttu-id="0813d-149">Naam wijzigen `powershell.exe` in `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="0813d-149">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="0813d-150">Om gebruikers een deterministische manier te geven om Power shell core aan te roepen in Windows (in plaats van Windows Power shell), is het binaire bestand van Power shell core gewijzigd in `pwsh.exe` op Windows en `pwsh` op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="0813d-150">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="0813d-151">De kortere naam is ook consistent met de naamgeving van shells op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="0813d-151">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a><span data-ttu-id="0813d-152">Geen regel einden invoegen in uitvoer (met uitzonde ring van tabellen) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="0813d-152">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="0813d-153">Voorheen werd de uitvoer uitgelijnd op de breedte van de console en worden er regel einden toegevoegd aan de eind breedte van de console, wat betekent dat de uitvoer niet opnieuw is ingedeeld zoals verwacht als de grootte van de Terminal is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="0813d-153">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="0813d-154">Deze wijziging is niet toegepast op tabellen, omdat de regel einden nood zakelijk zijn om de kolommen uitgelijnd te laten worden.</span><span class="sxs-lookup"><span data-stu-id="0813d-154">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a><span data-ttu-id="0813d-155">Null-element controle overs laan voor verzamelingen met een waarde type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="0813d-155">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="0813d-156">Voor de `Mandatory` para meter en `ValidateNotNull` en `ValidateNotNullOrEmpty` -kenmerken slaat u de null-element controle op als het element type van de verzameling het waardetype is.</span><span class="sxs-lookup"><span data-stu-id="0813d-156">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a><span data-ttu-id="0813d-157">Wijziging `$OutputEncoding` van het gebruik `UTF-8 NoBOM` van code ring in plaats van ASCII- [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="0813d-157">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="0813d-158">De vorige code ring, ASCII (7-bits), resulteert in sommige gevallen in een onjuiste wijziging van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="0813d-158">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="0813d-159">Deze wijziging is `UTF-8 NoBOM` standaard, waarbij Unicode-uitvoer wordt bewaard met een code ring die wordt ondersteund door de meeste hulpprogram ma's en besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="0813d-159">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268"></a><span data-ttu-id="0813d-160">Verwijderen `AllScope` uit de meeste standaard aliassen [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="0813d-160">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="0813d-161">Om het bereik sneller te maken, `AllScope` is verwijderd uit de meeste standaard aliassen.</span><span class="sxs-lookup"><span data-stu-id="0813d-161">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="0813d-162">`AllScope` is overgebleven voor enkele veelgebruikte aliassen waarbij de zoek opdracht sneller is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0813d-162">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a><span data-ttu-id="0813d-163">`-Verbose` en worden `-Debug` niet meer overschreven `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="0813d-163">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="0813d-164">Voorheen, als `-Verbose` of `-Debug` was opgegeven, overrode het gedrag van `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="0813d-164">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="0813d-165">Met deze wijziging `-Verbose` en `-Debug` niet langer van invloed op het gedrag van `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="0813d-165">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="0813d-166">Cmdlet-wijzigingen</span><span class="sxs-lookup"><span data-stu-id="0813d-166">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a><span data-ttu-id="0813d-167">Invoke-RestMethod retourneert geen nuttige informatie wanneer er geen gegevens worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0813d-167">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="0813d-168">#5320</span><span class="sxs-lookup"><span data-stu-id="0813d-168">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="0813d-169">Wanneer een API net retourneert `null` , wordt invoke-RestMethod als teken reeks geserialiseerd `"null"` in plaats van `$null` .</span><span class="sxs-lookup"><span data-stu-id="0813d-169">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="0813d-170">Met deze wijziging wordt de logica in `Invoke-RestMethod` voor het op de juiste wijze serialiseren van een geldige letterlijke JSON-waarde met een bepaalde teken `null` reeks `$null` .</span><span class="sxs-lookup"><span data-stu-id="0813d-170">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277"></a><span data-ttu-id="0813d-171">Verwijderen `-Protocol` uit `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="0813d-171">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="0813d-172">Als gevolg van problemen met RPC-externe toegang in CoreFX (met name op niet-Windows-platforms) en het garanderen van een consistente externe ervaring in Power shell, `-Protocol` is de para meter uit de `\*-Computer` cmdlets verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0813d-172">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="0813d-173">DCOM wordt niet meer ondersteund voor externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="0813d-173">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="0813d-174">De volgende cmdlets bieden alleen ondersteuning voor externe WSMAN-communicatie:</span><span class="sxs-lookup"><span data-stu-id="0813d-174">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="0813d-175">Naam wijzigen-computer</span><span class="sxs-lookup"><span data-stu-id="0813d-175">Rename-Computer</span></span>
- <span data-ttu-id="0813d-176">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="0813d-176">Restart-Computer</span></span>
- <span data-ttu-id="0813d-177">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="0813d-177">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090"></a><span data-ttu-id="0813d-178">Verwijderen `-ComputerName` uit `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="0813d-178">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="0813d-179">De `-ComputerName` para meter is verwijderd uit cmdlets om het consistente gebruik van PSRP te stimuleren `*-Service` .</span><span class="sxs-lookup"><span data-stu-id="0813d-179">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a><span data-ttu-id="0813d-180">Herstellen `Get-Item -LiteralPath a*b` Indien `a*b` niet echt bestaat om fout te retour neren [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="0813d-180">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="0813d-181">Als er eerder `-LiteralPath` een Joker teken wordt gegeven, zou dit hetzelfde zijn als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten.</span><span class="sxs-lookup"><span data-stu-id="0813d-181">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="0813d-182">Het juiste gedrag `-LiteralPath` is een letterlijke waarde, dus als het bestand niet bestaat, moet het een fout zijn.</span><span class="sxs-lookup"><span data-stu-id="0813d-182">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="0813d-183">Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.</span><span class="sxs-lookup"><span data-stu-id="0813d-183">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a><span data-ttu-id="0813d-184">`Import-Csv` moet worden toegepast bij `PSTypeNames` het importeren wanneer type gegevens aanwezig zijn in het CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="0813d-184">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="0813d-185">Voorheen behouden objecten die zijn geëxporteerd met `Export-CSV` met met `TypeInformation` geïmporteerd met `ConvertFrom-Csv` niet de type-informatie.</span><span class="sxs-lookup"><span data-stu-id="0813d-185">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="0813d-186">Met deze wijziging worden de type gegevens aan het `PSTypeNames` lid toegevoegd als deze beschikbaar zijn vanuit het CSV-bestand.</span><span class="sxs-lookup"><span data-stu-id="0813d-186">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a><span data-ttu-id="0813d-187">`-NoTypeInformation` moet standaard zijn op `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="0813d-187">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="0813d-188">Deze wijziging is aangebracht om de feedback van klanten te verhelpen over het standaard gedrag van `Export-CSV` om type gegevens op te nemen.</span><span class="sxs-lookup"><span data-stu-id="0813d-188">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="0813d-189">Voorheen voert de cmdlet een opmerking uit als de eerste regel met de type naam van het object.</span><span class="sxs-lookup"><span data-stu-id="0813d-189">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="0813d-190">De wijziging is het onderdrukken van deze standaard instelling, omdat deze niet wordt begrepen door de meeste hulpprogram ma's.</span><span class="sxs-lookup"><span data-stu-id="0813d-190">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="0813d-191">Gebruiken `-IncludeTypeInformation` om het vorige gedrag te bewaren.</span><span class="sxs-lookup"><span data-stu-id="0813d-191">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a><span data-ttu-id="0813d-192">Web-cmdlets moeten worden gewaarschuwd wanneer `-Credential` wordt verzonden via niet-versleutelde verbindingen [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="0813d-192">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="0813d-193">Wanneer u HTTP gebruikt, worden inhoud, inclusief wacht woorden, verzonden als ongecodeerde tekst.</span><span class="sxs-lookup"><span data-stu-id="0813d-193">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="0813d-194">Deze wijziging is het is niet toegestaan dit standaard te voor komen en een fout te retour neren als de referenties op een onveilige manier worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="0813d-194">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="0813d-195">Gebruikers kunnen dit omzeilen door gebruik te maken van de `-AllowUnencryptedAuthentication` Switch.</span><span class="sxs-lookup"><span data-stu-id="0813d-195">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="0813d-196">API-wijzigingen</span><span class="sxs-lookup"><span data-stu-id="0813d-196">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407"></a><span data-ttu-id="0813d-197">`AddTypeCommandBase` [#5407](https://github.com/PowerShell/PowerShell/issues/5407) klasse verwijderen</span><span class="sxs-lookup"><span data-stu-id="0813d-197">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="0813d-198">De `AddTypeCommandBase` klasse is verwijderd uit `Add-Type` om de prestaties te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="0813d-198">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="0813d-199">Deze klasse wordt alleen gebruikt door de cmdlet Add-type en mag geen invloed hebben op gebruikers.</span><span class="sxs-lookup"><span data-stu-id="0813d-199">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a><span data-ttu-id="0813d-200">De cmdlets worden samen met para meters `-Encoding` van het type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="0813d-200">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="0813d-201">De `-Encoding` waarde `Byte` is verwijderd uit de-cmdlets van het bestands systeem provider.</span><span class="sxs-lookup"><span data-stu-id="0813d-201">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="0813d-202">Er wordt nu een nieuwe para meter `-AsByteStream` gebruikt om op te geven dat een byte stroom als invoer is vereist of dat de uitvoer een stroom van bytes is.</span><span class="sxs-lookup"><span data-stu-id="0813d-202">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a><span data-ttu-id="0813d-203">Een beter fout bericht toevoegen voor lege en null- `-UFormat` para meter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="0813d-203">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="0813d-204">Wanneer een lege indelings teken reeks wordt door gegeven aan `-UFormat` , zou er een onhelp-fout bericht worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0813d-204">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="0813d-205">Er is een meer beschrijvende fout toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0813d-205">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995"></a><span data-ttu-id="0813d-206">Console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995) opschonen</span><span class="sxs-lookup"><span data-stu-id="0813d-206">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="0813d-207">De volgende functies zijn verwijderd omdat ze niet worden ondersteund in Power shell core en er zijn geen plannen om ondersteuning toe te voegen, aangezien deze bestaan voor verouderde redenen voor Windows Power shell: `-psconsolefile` Switch en code, `-importsystemmodules` Switch en code, en letter type wijzigen van code.</span><span class="sxs-lookup"><span data-stu-id="0813d-207">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942"></a><span data-ttu-id="0813d-208">`RunspaceConfiguration`Ondersteunings [#4942](https://github.com/PowerShell/PowerShell/issues/4942) verwijderd</span><span class="sxs-lookup"><span data-stu-id="0813d-208">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="0813d-209">Voorheen, wanneer u een Power shell-runs Pace programmatisch maakt met behulp van de API, kunt u de verouderde [`RunspaceConfiguration`][runspaceconfig] of de nieuwere versie gebruiken [`InitialSessionState`][iss] .</span><span class="sxs-lookup"><span data-stu-id="0813d-209">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="0813d-210">Deze wijziging heeft ondersteuning voor `RunspaceConfiguration` en alleen ondersteund `InitialSessionState` .</span><span class="sxs-lookup"><span data-stu-id="0813d-210">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: /dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: /dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a><span data-ttu-id="0813d-211">`CommandInvocationIntrinsics.InvokeScript` argumenten binden aan `$input` in plaats van `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="0813d-211">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="0813d-212">Een onjuiste positie van een para meter resulteerde in de argumenten die zijn door gegeven als invoer in plaats van als argumenten.</span><span class="sxs-lookup"><span data-stu-id="0813d-212">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a><span data-ttu-id="0813d-213">Niet-ondersteunde `-showwindow` Switch verwijderen van `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="0813d-213">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="0813d-214">`-showwindow` is afhankelijk van WPF. dit wordt niet ondersteund in CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0813d-214">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a><span data-ttu-id="0813d-215">Toestaan dat \* wordt gebruikt in het registerpad voor `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="0813d-215">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="0813d-216">Als er eerder `-LiteralPath` een Joker teken wordt gegeven, zou dit hetzelfde zijn als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten.</span><span class="sxs-lookup"><span data-stu-id="0813d-216">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="0813d-217">Het juiste gedrag `-LiteralPath` is een letterlijke waarde, dus als het bestand niet bestaat, moet het een fout zijn.</span><span class="sxs-lookup"><span data-stu-id="0813d-217">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="0813d-218">Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.</span><span class="sxs-lookup"><span data-stu-id="0813d-218">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802"></a><span data-ttu-id="0813d-219">`Set-Service`Mislukte test [#4802](https://github.com/PowerShell/PowerShell/issues/4802) herstellen</span><span class="sxs-lookup"><span data-stu-id="0813d-219">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="0813d-220">Voorheen werd, indien `New-Service -StartupType foo` gebruikt, `foo` genegeerd en is de service gemaakt met een standaard opstart type.</span><span class="sxs-lookup"><span data-stu-id="0813d-220">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="0813d-221">Deze wijziging is het expliciet genereren van een fout voor een ongeldig opstart type.</span><span class="sxs-lookup"><span data-stu-id="0813d-221">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700"></a><span data-ttu-id="0813d-222">Naam wijzigen `$IsOSX` in `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="0813d-222">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="0813d-223">De naamgeving in Power shell moet consistent zijn met de naamgeving en voldoen aan het gebruik van macOS in plaats van OSX.</span><span class="sxs-lookup"><span data-stu-id="0813d-223">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="0813d-224">Voor de Lees baarheid en consistent wordt er echter geadviseerd dat de Pascal-behuizing.</span><span class="sxs-lookup"><span data-stu-id="0813d-224">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a><span data-ttu-id="0813d-225">Fout bericht consistent maken wanneer ongeldig script wordt door gegeven aan-bestand, betere fout bij het door geven van een dubbel zinnig argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="0813d-225">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="0813d-226">De afsluit codes van wijzigen in `pwsh.exe` Uitlijnen met UNIX-conventies</span><span class="sxs-lookup"><span data-stu-id="0813d-226">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a><span data-ttu-id="0813d-227">Het verwijderen van `LocalAccount` en cmdlets uit  `Diagnostics` modules.</span><span class="sxs-lookup"><span data-stu-id="0813d-227">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="0813d-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="0813d-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="0813d-229">Als gevolg van niet-ondersteunde Api's, `LocalAccounts` zijn de module en de `Counter` cmdlets in de `Diagnostics` module verwijderd totdat er een betere oplossing is gevonden.</span><span class="sxs-lookup"><span data-stu-id="0813d-229">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a><span data-ttu-id="0813d-230">Het uitvoeren van een Power shell-script met de BOOL-para meter werkt niet [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="0813d-230">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="0813d-231">Voorheen gebruik **powershell.exe** (nu **pwsh.exe**) om een Power shell-script uit te voeren dat is `-File` ingesteld op geen enkele manier `$true` / `$false` als parameter waarden worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="0813d-231">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="0813d-232">`$true` / `$false` Er is ondersteuning toegevoegd voor als geparseerde waarden voor para meters.</span><span class="sxs-lookup"><span data-stu-id="0813d-232">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="0813d-233">Switch waarden worden ook ondersteund, omdat de syntaxis die momenteel wordt beschreven, niet werkt.</span><span class="sxs-lookup"><span data-stu-id="0813d-233">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027"></a><span data-ttu-id="0813d-234">`ClrVersion`Eigenschap verwijderen uit `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="0813d-234">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="0813d-235">De `ClrVersion` eigenschap van `$PSVersionTable` is niet nuttig met CoreCLR, eind gebruikers moeten deze waarde niet gebruiken om de compatibiliteit te bepalen.</span><span class="sxs-lookup"><span data-stu-id="0813d-235">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a><span data-ttu-id="0813d-236">Positie parameters voor wijzigen `powershell.exe` van in `-Command` `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="0813d-236">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="0813d-237">Schakel het shebang-gebruik van Power shell in op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="0813d-237">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="0813d-238">Dit betekent dat u op UNIX gebaseerde systemen een script bestand kunt maken dat Power shell automatisch aanroept in plaats van expliciet aan te roepen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="0813d-238">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="0813d-239">Dit betekent ook dat u nu dingen kunt doen zoals `powershell foo.ps1` of `powershell fooScript` zonder op te geven `-File` .</span><span class="sxs-lookup"><span data-stu-id="0813d-239">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="0813d-240">Voor deze wijziging moet u echter expliciet opgeven `-c` of als u wilt `-Command` proberen om dingen te doen `powershell.exe Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="0813d-240">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958"></a><span data-ttu-id="0813d-241">[#3958](https://github.com/PowerShell/PowerShell/issues/3958) voor het parseren van Unicode-escape implementeren</span><span class="sxs-lookup"><span data-stu-id="0813d-241">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="0813d-242">`` `u####`` of `` `u{####}`` wordt geconverteerd naar het bijbehorende Unicode-teken.</span><span class="sxs-lookup"><span data-stu-id="0813d-242">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="0813d-243">Als u een letterlijke waarde wilt uitvoeren, sluit u `` `u`` de apostroffen: ``` ``u``` .</span><span class="sxs-lookup"><span data-stu-id="0813d-243">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a><span data-ttu-id="0813d-244">Wijzig de `New-ModuleManifest` code ring in `UTF8NoBOM` op niet-Windows-platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="0813d-244">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="0813d-245">Voorheen `New-ModuleManifest` maakt psd1-manifesten in UTF-16 met stuk lijst, waardoor er een probleem is met Linux-hulpprogram ma's.</span><span class="sxs-lookup"><span data-stu-id="0813d-245">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="0813d-246">Door deze wijziging wordt de code ring van `New-ModuleManifest` als UTF (geen bom) gewijzigd in niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="0813d-246">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a><span data-ttu-id="0813d-247">Geen `Get-ChildItem` herhaling in symlinks (#1875).</span><span class="sxs-lookup"><span data-stu-id="0813d-247">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="0813d-248">#3780</span><span class="sxs-lookup"><span data-stu-id="0813d-248">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="0813d-249">Deze wijziging brengt `Get-ChildItem` meer in overeenstemming met de `ls -r` systeem eigen UNIX-en Windows- `dir /s` opdrachten.</span><span class="sxs-lookup"><span data-stu-id="0813d-249">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="0813d-250">Net als de vermelde opdrachten worden met de cmdlet symbolische koppelingen weer gegeven naar directory's die tijdens recursie zijn gevonden, maar worden ze niet herhaald.</span><span class="sxs-lookup"><span data-stu-id="0813d-250">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a><span data-ttu-id="0813d-251">Corrigeer `Get-Content -Delimiter` het scheidings teken niet in de geretourneerde regels [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="0813d-251">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="0813d-252">Voorheen was de uitvoer tijdens het gebruik `Get-Content -Delimiter` inconsistent en onhandig geworden toen verdere verwerking van de gegevens werd vereist om het scheidings teken te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0813d-252">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="0813d-253">Met deze wijziging verwijdert u het scheidings teken in geretourneerde regels.</span><span class="sxs-lookup"><span data-stu-id="0813d-253">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320"></a><span data-ttu-id="0813d-254">Indeling-hex in C#- [#3320](https://github.com/PowerShell/PowerShell/issues/3320) implementeren</span><span class="sxs-lookup"><span data-stu-id="0813d-254">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="0813d-255">De `-Raw` para meter is nu een ' Nee-op ' (in dat geval gebeurt er niets).</span><span class="sxs-lookup"><span data-stu-id="0813d-255">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="0813d-256">Alle uitvoer wordt weer gegeven met een echte representatie van getallen die alle bytes voor het type bevat (waarvoor de `-Raw` para meter formeel werd uitgevoerd vóór deze wijziging).</span><span class="sxs-lookup"><span data-stu-id="0813d-256">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a><span data-ttu-id="0813d-257">Power shell werkt als standaard shell niet met script opdracht [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="0813d-257">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="0813d-258">In UNIX is het een Conventie voor shells om `-i` een interactieve shell te accepteren en veel hulpprogram ma's verwachten dit gedrag ( `script` bijvoorbeeld wanneer Power shell als de standaard shell wordt ingesteld) en wordt de shell aangeroepen met de `-i` Switch.</span><span class="sxs-lookup"><span data-stu-id="0813d-258">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="0813d-259">Deze wijziging is opgesplitst in die `-i` eerder als korte hand kan worden gebruikt `-inputformat` , wat nu moet worden gevonden `-in` .</span><span class="sxs-lookup"><span data-stu-id="0813d-259">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a><span data-ttu-id="0813d-260">Type correctie in Get-ComputerInfo eigenschap name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="0813d-260">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="0813d-261">`BiosSerialNumber` is verkeerd gespeld `BiosSeralNumber` en is gewijzigd in de juiste spelling.</span><span class="sxs-lookup"><span data-stu-id="0813d-261">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a><span data-ttu-id="0813d-262">`Get-StringHash`#3024 toevoegen en `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="0813d-262">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="0813d-263">Deze wijziging is dat sommige hash-algoritmen niet worden ondersteund door CoreFX, dus zijn ze niet meer beschikbaar:</span><span class="sxs-lookup"><span data-stu-id="0813d-263">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a><span data-ttu-id="0813d-264">Validatie toevoegen voor `Get-*` cmdlets waarbij het door geven van $Null alle objecten retourneert in plaats van fout [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="0813d-264">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="0813d-265">Door door `$null` te geven aan een van de volgende fouten wordt een fout gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="0813d-265">Passing `$null` to any of the following now throws an error:</span></span>

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a><span data-ttu-id="0813d-266">Uitgebreide W3C-indeling van logboek bestand in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482) toevoegen</span><span class="sxs-lookup"><span data-stu-id="0813d-266">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="0813d-267">Voorheen kan de `Import-Csv` cmdlet niet worden gebruikt voor het rechtstreeks importeren van de logboek bestanden in de uitgebreide W3C-logboek indeling en is er extra actie vereist.</span><span class="sxs-lookup"><span data-stu-id="0813d-267">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="0813d-268">Met deze wijziging wordt de uitgebreide W3C-logboek indeling ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0813d-268">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a><span data-ttu-id="0813d-269">Fout bij het binden van de para meter met `ValueFromRemainingArguments` in PS-functies [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="0813d-269">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="0813d-270">`ValueFromRemainingArguments` retourneert nu de waarden als een matrix in plaats van een enkele waarde die zelf een matrix is.</span><span class="sxs-lookup"><span data-stu-id="0813d-270">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415"></a><span data-ttu-id="0813d-271">`BuildVersion` is verwijderd uit `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="0813d-271">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="0813d-272">Verwijder de `BuildVersion` eigenschap van `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="0813d-272">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="0813d-273">Deze eigenschap is gekoppeld aan de Windows-build-versie.</span><span class="sxs-lookup"><span data-stu-id="0813d-273">This property was tied to the Windows build version.</span></span> <span data-ttu-id="0813d-274">In plaats daarvan raden we u `GitCommitId` aan gebruik te maken van om de exacte build-versie van Power shell Core op te halen.</span><span class="sxs-lookup"><span data-stu-id="0813d-274">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="0813d-275">Wijzigingen in Web-cmdlets</span><span class="sxs-lookup"><span data-stu-id="0813d-275">Changes to Web Cmdlets</span></span>

<span data-ttu-id="0813d-276">De onderliggende .NET API van de Web-cmdlets is gewijzigd in `System.Net.Http.HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="0813d-276">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="0813d-277">Deze wijziging biedt veel voor delen.</span><span class="sxs-lookup"><span data-stu-id="0813d-277">This change provides many benefits.</span></span> <span data-ttu-id="0813d-278">Deze wijziging in combi natie met een gebrek aan interoperabiliteit met Internet Explorer heeft tot gevolg dat er verschillende belang rijke wijzigingen zijn aangebracht in `Invoke-WebRequest` en `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="0813d-278">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="0813d-279">`Invoke-WebRequest` ondersteunt nu alleen eenvoudige HTML-parsering.</span><span class="sxs-lookup"><span data-stu-id="0813d-279">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="0813d-280">`Invoke-WebRequest` retourneert altijd een- `BasicHtmlWebResponseObject` object.</span><span class="sxs-lookup"><span data-stu-id="0813d-280">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="0813d-281">De `ParsedHtml` `Forms` Eigenschappen en zijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0813d-281">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="0813d-282">`BasicHtmlWebResponseObject.Headers` de waarden zijn nu `String[]` in plaats van `String` .</span><span class="sxs-lookup"><span data-stu-id="0813d-282">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="0813d-283">`BasicHtmlWebResponseObject.BaseResponse` is nu een `System.Net.Http.HttpResponseMessage` object.</span><span class="sxs-lookup"><span data-stu-id="0813d-283">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="0813d-284">De `Response` eigenschap van uitzonde ringen op Web-cmdlets is nu een `System.Net.Http.HttpResponseMessage` object.</span><span class="sxs-lookup"><span data-stu-id="0813d-284">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="0813d-285">Strikte RFC-header parseren is nu standaard voor de `-Headers` `-UserAgent` para meter en.</span><span class="sxs-lookup"><span data-stu-id="0813d-285">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="0813d-286">Dit kan worden omzeild met `-SkipHeaderValidation` .</span><span class="sxs-lookup"><span data-stu-id="0813d-286">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="0813d-287">`file://` en `ftp://` URI-schema's worden niet meer ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0813d-287">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="0813d-288">`System.Net.ServicePointManager` de instellingen worden niet meer nageleefd.</span><span class="sxs-lookup"><span data-stu-id="0813d-288">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="0813d-289">Er is momenteel geen authenticatie op basis van certificaten beschikbaar in macOS.</span><span class="sxs-lookup"><span data-stu-id="0813d-289">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="0813d-290">Het gebruik van `-Credential` via een `http://` URI resulteert in een fout.</span><span class="sxs-lookup"><span data-stu-id="0813d-290">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="0813d-291">Gebruik een `https://` URI of geef de `-AllowUnencryptedAuthentication` para meter op om de fout te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="0813d-291">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="0813d-292">`-MaximumRedirection` produceert nu een afsluit fout wanneer de omleidings pogingen de gegeven limiet overschrijden in plaats van de resultaten van de laatste omleiding te retour neren.</span><span class="sxs-lookup"><span data-stu-id="0813d-292">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="0813d-293">In Power shell 6,2 is een wijziging aangebracht in UTF-8-code ring voor JSON-reacties.</span><span class="sxs-lookup"><span data-stu-id="0813d-293">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="0813d-294">Wanneer een charset niet wordt opgegeven voor een JSON-antwoord, moet de standaard codering UTF-8 zijn per RFC 8259.</span><span class="sxs-lookup"><span data-stu-id="0813d-294">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
