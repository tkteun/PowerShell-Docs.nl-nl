---
title: Wat is er nieuw in PowerShell 7.0
description: Nieuwe functies en wijzigingen uitgebracht in PowerShell 7.0
ms.date: 03/04/2020
ms.openlocfilehash: c858cf46d264ec1c29625eb08e30f71336f4e736
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729950"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="5f5a0-103">Wat is er nieuw in PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="5f5a0-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="5f5a0-104">PowerShell 7.0 is een opensource-, platformoverschrijdende (Windows-, macOS- en Linux)-editie van PowerShell, gebouwd om heterogene omgevingen en hybride cloud te beheren.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="5f5a0-105">In deze release introduceren we een aantal nieuwe functies, waaronder:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="5f5a0-106">Pijplijn-parallellisatie met `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="5f5a0-107">Nieuwe operators:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-107">New operators:</span></span>
  - <span data-ttu-id="5f5a0-108">Ternaire operator: `a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="5f5a0-109">Pijplijnketenoperators: `||` en `&&`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="5f5a0-110">Voorwaardelijke null-operators: `??` en `??=`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="5f5a0-111">Een vereenvoudigde en dynamische foutweergave en `Get-Error` cmdlet voor eenvoudiger onderzoek van fouten</span><span class="sxs-lookup"><span data-stu-id="5f5a0-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="5f5a0-112">Een compatibiliteitslaag waarmee gebruikers modules kunnen importeren in een impliciete Windows PowerShell sessie</span><span class="sxs-lookup"><span data-stu-id="5f5a0-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="5f5a0-113">Automatische meldingen van nieuwe versies</span><span class="sxs-lookup"><span data-stu-id="5f5a0-113">Automatic new version notifications</span></span>
- <span data-ttu-id="5f5a0-114">De mogelijkheid om DSC-resources rechtstreeks vanuit PowerShell 7 aan te roepen (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="5f5a0-115">Zie de [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)voor een volledige lijst met functies en oplossingen.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="5f5a0-116">Waar kan ik PowerShell installeren?</span><span class="sxs-lookup"><span data-stu-id="5f5a0-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="5f5a0-117">PowerShell 7 ondersteunt momenteel de volgende besturingssystemen op x64, waaronder:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="5f5a0-118">Windows 8.1 en 10</span><span class="sxs-lookup"><span data-stu-id="5f5a0-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="5f5a0-119">Windows Server 2012, 2012 R2, 2016 en 2019</span><span class="sxs-lookup"><span data-stu-id="5f5a0-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="5f5a0-120">macOS 10.13+</span><span class="sxs-lookup"><span data-stu-id="5f5a0-120">macOS 10.13+</span></span>
- <span data-ttu-id="5f5a0-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5f5a0-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="5f5a0-122">Fedora 30+</span><span class="sxs-lookup"><span data-stu-id="5f5a0-122">Fedora 30+</span></span>
- <span data-ttu-id="5f5a0-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="5f5a0-123">Debian 9</span></span>
- <span data-ttu-id="5f5a0-124">Ubuntu LTS 16.04+</span><span class="sxs-lookup"><span data-stu-id="5f5a0-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="5f5a0-125">Alpine Linux 3.8+</span><span class="sxs-lookup"><span data-stu-id="5f5a0-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="5f5a0-126">Daarnaast biedt PowerShell 7.0 ondersteuning voor ARM32- en ARM64-varianten van Debian, Ubuntu en ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="5f5a0-127">Controleer de installatie-instructies voor het besturingssysteem van [uw voorkeur: Windows,](/powershell/scripting/install/installing-powershell-core-on-windows) [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)of [Linux.](/powershell/scripting/install/installing-powershell-core-on-linux)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux).</span></span>

<span data-ttu-id="5f5a0-128">Hoewel dit niet officieel wordt ondersteund, biedt de community ook pakketten voor [Arch](https://aur.archlinux.org/packages/powershell/) en Kali Linux.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-129">Debian 10 en CentOS 8 bieden momenteel geen ondersteuning voor remoting van WinRM.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="5f5a0-130">Zie Voor meer informatie over het instellen van op SSH gebaseerde remoting [PowerShell Remoting via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="5f5a0-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="5f5a0-131">Zie De levenscyclus van [PowerShell-ondersteuning](/powershell/scripting/powershell-support-lifecycle)voor meer actuele informatie over ondersteunde besturingssystemen en de levenscyclus van ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="5f5a0-132">PowerShell 7 uitvoeren</span><span class="sxs-lookup"><span data-stu-id="5f5a0-132">Running PowerShell 7</span></span>

<span data-ttu-id="5f5a0-133">PowerShell 7 wordt in een map geïnstalleerd, gescheiden van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-133">PowerShell 7 installs to a directory seperately from Windows PowerShell.</span></span>
<span data-ttu-id="5f5a0-134">Hiermee kunt u PowerShell 7 naast elkaar uitvoeren met Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-134">This enables you to run PowerShell 7 side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="5f5a0-135">Voor PowerShell Core 6.x is PowerShell 7 een in-place upgrade die PowerShell Core 6.x verwijdert.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-135">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="5f5a0-136">PowerShell 7 is geïnstalleerd op `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-136">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="5f5a0-137">De `%programfiles%\PowerShell\7` map wordt toegevoegd aan `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-137">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="5f5a0-138">Met het PowerShell 7-installatiepakket worden eerdere versies van PowerShell Core 6.x:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-138">The PowerShell 7 installer package upgrades previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="5f5a0-139">PowerShell Core 6.x in Windows: `%programfiles%\PowerShell\6` is vervangen door `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-139">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="5f5a0-140">Linux: `/opt/microsoft/powershell/6` wordt vervangen door `/opt/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-140">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="5f5a0-141">macOS: `/usr/local/microsoft/powershell/6` is vervangen door `/usr/local/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-141">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-142">In Windows PowerShell heeft het uitvoerbare bestand om PowerShell te starten de naam `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-142">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="5f5a0-143">In versie 6 en hoger wordt de naam van het uitvoerbare bestand gewijzigd om uitvoering naast elkaar te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-143">In version 6 and above, the executable name is changed to support side-by-side execution.</span></span> <span data-ttu-id="5f5a0-144">De nieuwe naam van het uitvoerbare bestand om PowerShell 7 te starten is `pwsh.exe` .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-144">The new executable name to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="5f5a0-145">Preview-builds blijven in-place als `pwsh-preview` in plaats van onder de map `pwsh` 7-preview.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-145">Preview builds remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="5f5a0-146">Verbeterde compatibiliteit met eerdere Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f5a0-146">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="5f5a0-147">PowerShell 7.0 markeert een overstap naar .NET Core 3.1, waardoor de compatibiliteit met bestaande Windows PowerShell-modules aanzienlijk Windows PowerShell is.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-147">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="5f5a0-148">Dit omvat veel modules in Windows waarvoor GUI-functionaliteit is vereist, zoals en , evenals veel rolbeheermodules die worden aangeboden `Out-GridView` `Show-Command` als onderdeel van Windows.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-148">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="5f5a0-149">Voor Windows wordt een nieuwe switchparameter **UseWindowsPowerShell** toegevoegd aan `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-149">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="5f5a0-150">Met deze switch maakt u een proxymodule in PowerShell 7 die gebruikmaakt van een lokaal Windows PowerShell om impliciet cmdlets uit te voeren die in die module zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-150">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="5f5a0-151">Voor meer informatie over [Import-Module.](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-151">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true).</span></span>

<span data-ttu-id="5f5a0-152">Zie de modulecompatibiliteitstabel voor meer informatie over [](https://aka.ms/PSModuleCompat)welke Microsoft-modules werken met PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-152">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="5f5a0-153">Parallelle uitvoering toegevoegd aan ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="5f5a0-153">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="5f5a0-154">De cmdlet, waarmee items in een verzameling worden itereerd, heeft nu `ForEach-Object` ingebouwde parallellisme met de nieuwe parameter **Parallel.**</span><span class="sxs-lookup"><span data-stu-id="5f5a0-154">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="5f5a0-155">Parallelle scriptblokken gebruiken standaard de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-155">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="5f5a0-156">In dit voorbeeld worden 50.000 logboekgegevens opgehaald uit 5 systeemlogboeken op een lokale Windows-computer:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-156">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="5f5a0-157">De **parameter Parallel** geeft het scriptblok aan dat parallel wordt uitgevoerd voor elke naam van het invoerlogboek.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-157">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="5f5a0-158">De nieuwe **parameter ThrottleLimit** beperkt het aantal scriptblokken dat parallel op een bepaald moment wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-158">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="5f5a0-159">De standaardwaarde is 5.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-159">The default is 5.</span></span>

<span data-ttu-id="5f5a0-160">Gebruik de variabele om het huidige invoerobject in het `$_` scriptblok weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-160">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="5f5a0-161">Gebruik het `$using:` bereik om variabeleverwijzingen door te geven aan het lopende scriptblok.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-161">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="5f5a0-162">Voor meer informatie over [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5f5a0-162">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&preserve-view=true).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="5f5a0-163">Ternaire operator</span><span class="sxs-lookup"><span data-stu-id="5f5a0-163">Ternary operator</span></span>

<span data-ttu-id="5f5a0-164">PowerShell 7.0 introduceert een ternaire operator die zich gedraagt als een vereenvoudigde `if-else` instructie.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-164">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="5f5a0-165">De ternaire operator van PowerShell is nauw gemodelleerd op de syntaxis van de ternaire C#-operator:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-165">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="5f5a0-166">De condition-expression wordt altijd geëvalueerd en het resultaat ervan wordt geconverteerd naar een **Booleaanse** waarde om te bepalen welke vertakking vervolgens wordt geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-166">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="5f5a0-167">De `<if-true>` expressie wordt uitgevoerd als de expressie waar `<condition>` is</span><span class="sxs-lookup"><span data-stu-id="5f5a0-167">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="5f5a0-168">De `<if-false>` expressie wordt uitgevoerd als de expressie `<condition>` onwaar is</span><span class="sxs-lookup"><span data-stu-id="5f5a0-168">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="5f5a0-169">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-169">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="5f5a0-170">Als het pad in dit voorbeeld bestaat, wordt **Pad** bestaat weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-170">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="5f5a0-171">Als het pad niet bestaat, wordt **Pad niet gevonden** weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-171">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="5f5a0-172">Voor meer informatie [over If](/powershell/module/microsoft.powershell.core/about/about_if).</span><span class="sxs-lookup"><span data-stu-id="5f5a0-172">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="5f5a0-173">Pijplijnketenoperators</span><span class="sxs-lookup"><span data-stu-id="5f5a0-173">Pipeline chain operators</span></span>

<span data-ttu-id="5f5a0-174">PowerShell 7 implementeert de `&&` operators en `||` om pijplijnen voorwaardelijk te ketenen.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-174">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="5f5a0-175">Deze operators worden in PowerShell 'pijplijnketenoperators' genoemd en zijn vergelijkbaar met AND- en OR-lijsten in shells zoals **Bash** en **Zsh,** evenals voorwaardelijke verwerkingssymbolen in de Windows Command Shell **(cmd.exe).**</span><span class="sxs-lookup"><span data-stu-id="5f5a0-175">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="5f5a0-176">De `&&` operator voert de rechterpijplijn uit als de pijplijn aan de linkerkant is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-176">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="5f5a0-177">De operator voert `||` daarentegen de rechterpijplijn uit als de pijplijn aan de linkerkant is mislukt.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-177">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-178">Deze operators gebruiken de `$?` variabelen en om te bepalen of een `$LASTEXITCODE` pijplijn is mislukt.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-178">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="5f5a0-179">Hiermee kunt u ze gebruiken met systeemeigen opdrachten en niet alleen met cmdlets of functies.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-179">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="5f5a0-180">Hier slaagt de eerste opdracht en wordt de tweede opdracht uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-180">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="5f5a0-181">Hier mislukt de eerste opdracht en wordt de tweede niet uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-181">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="5f5a0-182">Hier slaagt de eerste opdracht, de tweede opdracht wordt niet uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-182">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="5f5a0-183">Hier mislukt de eerste opdracht, zodat de tweede opdracht wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-183">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="5f5a0-184">Voor meer informatie over [pijplijnketenoperators.](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-184">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7&preserve-view=true).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="5f5a0-185">Null-sameneten, toewijzing en voorwaardelijke operators</span><span class="sxs-lookup"><span data-stu-id="5f5a0-185">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="5f5a0-186">PowerShell 7 bevat null-samen te schalen operator `??` , Null voorwaardelijke toewijzing `??=` en Null voorwaardelijke lidtoegangsoperators `?.` en `?[]` .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-186">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="5f5a0-187">Null-samen te sluiten Operator ?</span><span class="sxs-lookup"><span data-stu-id="5f5a0-187">Null-coalescing Operator ??</span></span>

<span data-ttu-id="5f5a0-188">De operator null-coalescing retourneert de waarde van de linkerope `??` operand als deze niet null is.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-188">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="5f5a0-189">Anders wordt de rechterope operand geëvalueerd en wordt het resultaat ervan retourneert.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-189">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="5f5a0-190">De `??` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-190">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="5f5a0-191">In het volgende voorbeeld wordt de rechteropeenvolger niet geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-191">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="5f5a0-192">Null-operator voor voorwaardelijke toewijzing? =</span><span class="sxs-lookup"><span data-stu-id="5f5a0-192">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="5f5a0-193">De operator voor voorwaardelijke toewijzing van null wijst de waarde van de rechteropend alleen toe aan de linkeropend als de operand aan de linkerkant als null `??=` wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-193">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="5f5a0-194">De `??=` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-194">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="5f5a0-195">In het volgende voorbeeld wordt de rechterope operand niet geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-195">In the following example, the right-hand operand is not evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="5f5a0-196">Null operators voor voorwaardelijke lidtoegang ? .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-196">Null conditional member access operators ?.</span></span> <span data-ttu-id="5f5a0-197">En? [] (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-197">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-198">Dit is een experimentele functie met de **naam PSNullConditionalOperators.**</span><span class="sxs-lookup"><span data-stu-id="5f5a0-198">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="5f5a0-199">Zie Experimentele functies gebruiken [voor meer informatie.](/powershell/scripting/learn/experimental-features)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-199">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="5f5a0-200">Een voorwaardelijke operator null staat alleen toegang tot leden, , of elementtoegang tot de operand toe als die operand als niet-null wordt geëvalueerd; anders wordt `?.` `?[]` null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-200">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-201">Omdat PowerShell deel mag uitmaken van de naam van de variabele, is een formele specificatie van de naam van de variabele `?` vereist voor het gebruik van deze operators.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-201">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="5f5a0-202">Het is dus vereist om te gebruiken `{}` rond de namen van variabelen, zoals of wanneer deel uitmaakt van de `${a}` `?` variabelenaam `${a?}` .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-202">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="5f5a0-203">In het volgende voorbeeld wordt de waarde van de eigenschap Status van het **lid** geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-203">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="5f5a0-204">In het volgende voorbeeld wordt null geretourneerd, zonder toegang te krijgen tot de **lidnaam Status:**</span><span class="sxs-lookup"><span data-stu-id="5f5a0-204">The following example returns null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="5f5a0-205">Op dezelfde manier wordt met `?[]` behulp van de waarde van het element geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-205">Similarly, using `?[]`, the value of the element is returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="5f5a0-206">En wanneer de operand null is, wordt het element niet toegankelijk en wordt null geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-206">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="5f5a0-207">Voor meer informatie [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5f5a0-207">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&preserve-view=true).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="5f5a0-208">Nieuwe weergave: ConciseView en cmdlet Get-Error</span><span class="sxs-lookup"><span data-stu-id="5f5a0-208">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="5f5a0-209">PowerShell 7.0 verbetert de weergave van foutberichten om de leesbaarheid van interactieve en scriptfouten te verbeteren met een nieuwe standaardweergave **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-209">PowerShell 7.0 enhances the display of error messages to improve the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="5f5a0-210">De weergaven kunnen door de gebruiker worden geselecteerd via de voorkeursvariabele `$ErrorView` .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-210">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="5f5a0-211">Als **een fout niet** afkomstig is van een script- of parserfout, is dit een foutbericht met één regel:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-211">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="5f5a0-212">Als de fout optreedt tijdens het uitvoeren van het script of een parseringsfout is, retourneert PowerShell een foutbericht met meerdere lijnen dat de fout bevat, een aanwijzer en een foutbericht dat laat zien waar de fout zich op die regel voordoet.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-212">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="5f5a0-213">Als de terminal geen ondersteuning biedt voor ANSI-kleuren escapereeksen (VT100), worden er geen kleuren weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-213">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![Fout bij het weergeven van een script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="5f5a0-215">De standaardweergave in PowerShell 7 is **ConciseView.**</span><span class="sxs-lookup"><span data-stu-id="5f5a0-215">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="5f5a0-216">De vorige standaardweergave was **NormalView en** u kunt dit selecteren door de voorkeursvariabele in te `$ErrorView` stellen.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-216">The previous default view was **NormalView** and you can select this by setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="5f5a0-217">Er wordt een nieuwe eigenschap **ErrorAccentColor** toegevoegd aan ter `$Host.PrivateData` ondersteuning van het wijzigen van de accentkleur van het foutbericht.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-217">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="5f5a0-218">Een nieuwe cmdlet biedt desgewenst een volledige gedetailleerde weergave van de volledig `Get-Error` gekwalificeerde fout.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-218">A new cmdlet `Get-Error` provides a complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="5f5a0-219">Standaard geeft de cmdlet de volledige details weer, inclusief interne uitzonderingen, van de laatste fout die is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-219">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![Weergeven vanuit Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="5f5a0-221">De `Get-Error` cmdlet ondersteunt invoer van de pijplijn met behulp van de ingebouwde variabele `$Error` .</span><span class="sxs-lookup"><span data-stu-id="5f5a0-221">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="5f5a0-222">`Get-Error` geeft alle doorspijpfouten weer.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-222">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="5f5a0-223">De `Get-Error` cmdlet ondersteunt de parameter **Nieuwste,** zodat u kunt opgeven hoeveel fouten van de huidige sessie u wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-223">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="5f5a0-224">Voor meer informatie over [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5f5a0-224">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7&preserve-view=true).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="5f5a0-225">Melding over nieuwe versie</span><span class="sxs-lookup"><span data-stu-id="5f5a0-225">New version notification</span></span>

<span data-ttu-id="5f5a0-226">PowerShell 7 maakt gebruik van updatemeldingen om gebruikers te waarschuwen dat er updates voor PowerShell bestaan.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-226">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="5f5a0-227">Eenmaal per dag vraagt PowerShell een query uit op een onlineservice om te bepalen of er een nieuwere versie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-227">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-228">De updatecontrole vindt plaats tijdens de eerste sessie in een bepaalde periode van 24 uur.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-228">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="5f5a0-229">Uit prestatieoverwegingen wordt de updatecontrole 3 seconden na het begin van de sessie gestart.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-229">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="5f5a0-230">De melding wordt alleen weergegeven aan het begin van volgende sessies.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-230">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="5f5a0-231">PowerShell abonneert zich standaard op een van twee verschillende meldingskanalen, afhankelijk van de versie/vertakking.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-231">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="5f5a0-232">Ondersteunde, algemeen beschikbare (GA)-versies van PowerShell retourneren alleen meldingen voor bijgewerkte ga-releases.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-232">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="5f5a0-233">Preview- en RELEASE Candidate-releases (RC) melden updates voor preview-, RC- en GA-releases.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-233">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="5f5a0-234">Het gedrag voor updatemeldingen kan worden gewijzigd met behulp van de `$Env:POWERSHELL_UPDATECHECK` omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-234">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="5f5a0-235">De volgende waarden worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-235">The following values are supported:</span></span>

- <span data-ttu-id="5f5a0-236">**De** standaardwaarde is hetzelfde als het niet definiëren van `$Env:POWERSHELL_UPDATECHECK`</span><span class="sxs-lookup"><span data-stu-id="5f5a0-236">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="5f5a0-237">GA-releases melden updates voor GA-releases</span><span class="sxs-lookup"><span data-stu-id="5f5a0-237">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="5f5a0-238">Preview-/RC-releases melden updates voor ga- en preview-releases</span><span class="sxs-lookup"><span data-stu-id="5f5a0-238">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="5f5a0-239">**Met Uitschakelen** wordt de functie voor updatemeldingen uitgeschakeld</span><span class="sxs-lookup"><span data-stu-id="5f5a0-239">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="5f5a0-240">**LTS** waarschuwt alleen updates voor LTS-releases (long-term-servicing)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-240">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-241">De `$Env:POWERSHELL_UPDATECHECK` omgevingsvariabele bestaat pas als deze voor de eerste keer is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-241">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="5f5a0-242">De versiemelding voor alleen `LTS` releases instellen:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-242">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="5f5a0-243">De versiemelding instellen op het `Default` gedrag:</span><span class="sxs-lookup"><span data-stu-id="5f5a0-243">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="5f5a0-244">Voor meer informatie [over updatemeldingen.](/powershell/module/microsoft.powershell.core/about/about_update_notifications)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-244">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="5f5a0-245">Nieuwe ondersteuning voor DSC-resources met Invoke-DSCResource (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-245">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="5f5a0-246">Dit is een experimentele functie met **de naam PSDesiredStateConfiguration.InvokeDscResource.**</span><span class="sxs-lookup"><span data-stu-id="5f5a0-246">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="5f5a0-247">Zie Experimentele functies gebruiken [voor meer informatie.](/powershell/scripting/learn/experimental-features)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-247">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="5f5a0-248">Met `Invoke-DscResource` de cmdlet wordt een methode van een opgegeven PowerShell Desired State Configuration -resource (DSC) uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-248">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="5f5a0-249">Met deze cmdlet wordt een DSC-resource rechtstreeks aanroepen, zonder een configuratiedocument te maken.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-249">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="5f5a0-250">Met deze cmdlet kunnen configuratiebeheerproducten Windows of Linux beheren met behulp van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-250">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="5f5a0-251">Met deze cmdlet kunt u ook debuggen van resources wanneer de DSC-engine wordt uitgevoerd met debugging ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-251">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="5f5a0-252">Met deze opdracht wordt de **set-methode** van een resource met de naam **WindowsProcess** aanroepen en worden de verplichte eigenschappen **Pad** en **Argumenten** opgegeven om het opgegeven Windows-proces te starten.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-252">This command invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

<span data-ttu-id="5f5a0-253">Voor meer informatie over [Invoke-DSCResource.](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-253">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&preserve-view=true).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="5f5a0-254">Belangrijke wijzigingen en verbeteringen</span><span class="sxs-lookup"><span data-stu-id="5f5a0-254">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="5f5a0-255">Wijzigingen die fouten veroorzaken</span><span class="sxs-lookup"><span data-stu-id="5f5a0-255">Breaking Changes</span></span>

- <span data-ttu-id="5f5a0-256">Updatemeldingen ondersteunen LTS en standaardkanalen (#11132)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-256">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="5f5a0-257">Werk Test-Connection zo bij dat het meer werkt zoals in Windows PowerShell (#10697) (Bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-257">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5f5a0-258">$?</span><span class="sxs-lookup"><span data-stu-id="5f5a0-258">Preserve $?</span></span> <span data-ttu-id="5f5a0-259">voor ParenExpression, SubExpression en ArrayExpression (#11040)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-259">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="5f5a0-260">Stel de working directory in op current directory in Start-Job (#10920) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-260">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-261">Zorg $PSCulture consistent wijzigingen in de sessiecultuur (#10138) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-261">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="5f5a0-262">Engine-updates en -oplossingen</span><span class="sxs-lookup"><span data-stu-id="5f5a0-262">Engine Updates and Fixes</span></span>

- <span data-ttu-id="5f5a0-263">Verbeteringen in onderbrekingspunt-API's voor externe scenario's (#11312)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-263">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="5f5a0-264">Probleem opgelost met het lekken van PowerShell-klassedefinitie in een andere Runspace (#11273)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-264">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="5f5a0-265">Regressie in opmaak opgelost die wordt veroorzaakt door de firstordefault-primitieve die is toegevoegd in 7.0.0-Preview1 (#11258)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-265">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="5f5a0-266">Aanvullende Microsoft-modules om bij te houden in PS7-telemetrie (#10751)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-266">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="5f5a0-267">Goedgekeurde functies niet-experimenteel maken (#11303)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-267">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="5f5a0-268">Werk ConciseView bij om TargetObject te gebruiken, indien van toepassing (#11075)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-268">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="5f5a0-269">NullReferenceException opgelost in Openbare methoden van CompletionCompleters (#11274)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-269">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="5f5a0-270">Controle van de threadtoestand van een thread op niet-Windows-platformen (#11301)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-270">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="5f5a0-271">Instelling PSModulePath bijgewerkt voor het samenvoegen van de proces- en machineomgevingsvariabelen (#11276)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-271">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="5f5a0-272">.NET Core naar 3.1.0 (#11260)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-272">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="5f5a0-273">Detectie van $PSHOME vóór $env:PATH (#11141)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-273">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="5f5a0-274">Pwsh toestaan om $env:PSModulePath over te nemen en ervoor te zorgen powershell.exe correct wordt #11057)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-274">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="5f5a0-275">Over naar .NET Core 3.1 preview 1 (#10798)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-275">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="5f5a0-276">Controles van reparsetags in de bestandssysteemprovider (#10431) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-276">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-277">VERVANG CR en de nieuwe regel door een 0x23CE in scriptlogboekregistratie (#10616)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-277">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="5f5a0-278">Los een resourcelek op door de registratie van de gebeurtenis-handler van AppDomain.CurrentDomain.ProcessExit (#10626)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-278">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="5f5a0-279">Voeg ondersteuning toe aan ActionPreference.Break om op te breken in het foutopsporingssysteem wanneer er foutopsporings-, fout-, informatie-, voortgangs-, uitgebreide of waarschuwingsberichten worden gegenereerd (#8205) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-279">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5f5a0-280">Schakel invoegingen van het configuratiescherm in PowerShell Core zonder op te geven. CPL-extensie.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-280">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="5f5a0-281">(#9828)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-281">(#9828)</span></span>
- <span data-ttu-id="5f5a0-282">Ondersteuning voor negatieve getallen in de operator -split (#8960) (bedankt @ece-jacob-scott !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-282">Support negative numbers in -split operator (#8960) (Thanks @ece-jacob-scott!)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="5f5a0-283">Algemene updates en oplossingen voor cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f5a0-283">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="5f5a0-284">Oplossing voor probleem met Raspbian voor het instellen van de datum van bestandswijzigingen in de experimentele functie UnixStat (#11313)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-284">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="5f5a0-285">-AsPlainText toevoegen aan ConvertFrom-SecureString (#11142)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-285">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="5f5a0-286">WindowsPS-versiecontrole toegevoegd voor WinCompat (#11148)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-286">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="5f5a0-287">Foutrapportage in sommige WinCompat-scenario's (#11259)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-287">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="5f5a0-288">Systeemeigen binaire resolver (#11032) toevoegen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-288">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-289">De berekening van de breedte van de char bijwerken om CJK-chars correct te #11262)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-289">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="5f5a0-290">Een Unblock-File voor macOS (#11137)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-290">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="5f5a0-291">Regressie in Get-PSCallStack (#11210) opgelost (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-291">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-292">Automatisch laden van de module ScheduledJob verwijderen bij het gebruik van taak-cmdlets (#11194)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-292">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="5f5a0-293">Voeg OutputType toe aan Get-Error cmdlet en behoud de oorspronkelijke typenamen (#10856)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-293">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="5f5a0-294">Probleem opgelost met null-verwijzing in eigenschap SupportsVirtualTerminal (#11105)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-294">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="5f5a0-295">Limietcontrole toevoegen in Get-WinEvent (#10648) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-295">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-296">Probleem met opdrachtruntime opgelost, zodat StopUpstreamCommandsException niet wordt ingevuld in -ErrorVariable (#10840)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-296">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="5f5a0-297">Stel de uitvoercodeer in op [Console]::OutputEncoding voor systeemeigen opdrachten (#10824)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-297">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="5f5a0-298">Ondersteuning voor codeblokken met meerdere regels in voorbeelden (#10776) (Bedankt @Greg-Smulko !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-298">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="5f5a0-299">Voeg de parameter Culture toe Select-String cmdlet (#10943) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-299">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-300">Probleem Start-Job van een werkmap met een backslash (#11041)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-300">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="5f5a0-301">ConvertFrom-Json: verzamelingen standaard uitpakken (#10861) (bedankt @danstur !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-301">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="5f5a0-302">Gebruik de casegevoelige hashtabel voor Group-Object cmdlet met -CaseSensitive en -AsHashtable-switches (#11030) (Bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-302">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5f5a0-303">Af te handelen uitzondering als het opsnoemen van bestanden mislukt bij het herbouwen van het pad met de juiste casing (#11014)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-303">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="5f5a0-304">Fix ConciseView to show Activity instead of myCommand (#11007) (Beknopte #11007)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-304">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="5f5a0-305">Web-cmdlets toestaan http-foutstatussen (#10466) te negeren (bedankt @vdamewood !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-305">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="5f5a0-306">Het doorspijpen van meer dan één CommandInfo naar Get-Command (#10929)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-306">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="5f5a0-307">Back-Get-Counter cmdlet voor Windows (#10933)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-307">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="5f5a0-308">Zorg ConvertTo-Json [AutomationNull]::Value en [NullString]::Value behandelen als $null (#10957)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-308">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="5f5a0-309">Haakjes verwijderen van ipv6-adres voor SSH-remoting (#10968)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-309">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="5f5a0-310">Crash oplossen als de opdracht die naar pwsh wordt verzonden alleen witruimte is (#10977)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-310">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="5f5a0-311">Platformoverschrijdende Get-Clipboard en Set-Clipboard (#10340)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-311">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="5f5a0-312">Probleem opgelost bij het instellen van het oorspronkelijke pad van het bestandssysteemobject om geen extra schuine streep (#10959)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-312">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="5f5a0-313">Ondersteuning$ $null voor ConvertTo-Json (#10947)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-313">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="5f5a0-314">Back-Out-Printer toevoegen in Windows (#10906)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-314">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="5f5a0-315">Oplossing Start-Job -WorkingDirectory met witruimte (#10951)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-315">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="5f5a0-316">Retourneert de standaardwaarde wanneer null wordt geretourneerd voor een instelling in PSConfiguration.cs (#10963) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-316">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-317">I/O-uitzondering verwerken als niet-#10950)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-317">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="5f5a0-318">Voeg een GraphicalHost-assembly toe om Out-GridView, Show-Command en Get-Help -ShowWindow (#10899)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-318">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="5f5a0-319">Neem ComputerName via pijplijn in Get-HotFix (#10852) (bedankt @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-319">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="5f5a0-320">Tab-voltooiing voor parameters opgelost, zodat algemene parameters als beschikbaar worden weergegeven (#10850)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-320">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="5f5a0-321">Probleem opgelost met GetCorrectCasedPath() om eerst te controleren of er vermeldingen in het systeembestand worden geretourneerd voordat u First() (#10930)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-321">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="5f5a0-322">Stel working directory in op current directory in Start-Job (#10920) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-322">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-323">Wijzig TabExpansion2 om -CursorColumn niet te vereisen en te behandelen als $InputScript.Length (#10849)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-323">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="5f5a0-324">Handle case where Host may not return Rows or Columns of screen (#10938)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-324">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="5f5a0-325">Probleem opgelost met het gebruik van accentkleuren voor hosts die deze niet ondersteunen (#10937)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-325">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="5f5a0-326">Back-Update-List (#10922)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-326">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="5f5a0-327">FWLink-id bijwerken voor Clear-RecycleBin (#10925)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-327">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="5f5a0-328">Sla het bestand tijdens het voltooien van het tabblad over als bestandskenmerken niet kunnen worden gelezen (#10910)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-328">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="5f5a0-329">Back-Clear-RecycleBin voor Windows (#10909)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-329">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="5f5a0-330">Toevoegen `$env:__SuppressAnsiEscapeSequences` om te bepalen of de VT-escapereeks moet worden uitgevoerd (#10814)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-330">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="5f5a0-331">Parameter -NoEmphasize toevoegen om de uitvoer Select-String kleuren (#8963) (bedankt @derek-xia !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-331">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="5f5a0-332">Back-Get-HotFix cmdlet (#10740)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-332">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="5f5a0-333">Maak Add-Type bruikbaar in toepassingen die PowerShell hosten (#10587)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-333">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="5f5a0-334">Gebruik een effectievere evaluatie volgorde in LanguagePrimitives.IsNullLike() (#10781) (Bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-334">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5f5a0-335">De verwerking verbeteren van invoer met gemengde verzamelingspijpen en doorspijpstromen van invoer in Format-Hex (#8674) (Bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-335">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5f5a0-336">Gebruik typeconversie in hashtabels van SSHConnection wanneer de waarde niet overeen komt met het verwachte type (#10720) (Bedankt @SeeminglyScience !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-336">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="5f5a0-337">Probleem Get-Content -ReadCount 0 opgelost wanneer -TotalCount is ingesteld (#10749) (Bedankt @eugenesmlv !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-337">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="5f5a0-338">Foutbericht toegang geweigerd in Get-WinEvent (#10639) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-338">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-339">Tab-voltooiing inschakelen voor variabeletoewijzing die beperkt is of van het type is beperkt (#10646)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-339">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="5f5a0-340">Verwijder ongebruikte eigenschap voor het buiten gebruik hebben van SourceLength, wat opmaakproblemen veroorzaakt (#10765)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-340">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="5f5a0-341">Parameter -Delimiter toevoegen aan ConvertFrom-StringData (#10665) (Bedankt @steviecoaster !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-341">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="5f5a0-342">Positionele parameter voor ScriptBlock toevoegen bij gebruik van Invoke-Command met SSH (#10721) (Bedankt @machgo !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-342">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="5f5a0-343">Informatie over regelcontext tonen als er meerdere regels zijn, maar geen scriptnaam voor ConciseView (#10746)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-343">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="5f5a0-344">Ondersteuning toegevoegd voor \\ wsl$\-paden naar bestandssysteemprovider (#10674)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-344">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="5f5a0-345">De ontbrekende tokentekst voor TokenKind.QuestionMark toevoegen aan parser (#10706)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-345">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="5f5a0-346">Stel de huidige werkmap van elke ForEach-Object -Parallel uitvoerend script in op dezelfde locatie als het aanroepend script.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-346">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="5f5a0-347">(#10672)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-347">(#10672)</span></span>
- <span data-ttu-id="5f5a0-348">Vervang api-ms-win-core-file-l1-2-2.dll door Kernell32.dll findfirstStreamW en FindNextStreamW-API's (#10680) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-348">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-349">Help-opmaakscript aanpassen om StrictMode toleranter (#10563)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-349">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="5f5a0-350">Parameter -SecurityDescriptorSDDL toevoegen aan New-Service (#10483) (bedankt @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-350">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="5f5a0-351">Gegevensuitvoer verwijderen, pinggebruik consolideren in Test-Connection (#10478) (Bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-351">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5f5a0-352">Lees speciale reparsepunten zonder ze te openen (#10662) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-352">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-353">Direct Clear-Host output to terminal (#10681) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-353">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-354">Nieuwe lijn toevoegen voor groeperen met Format-Table en -Eigenschap (#10653)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-354">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="5f5a0-355">Verwijder [ValidateNotNullOrEmpty] uit -InputObject op Get-Random lege tekenreeks toe te staan (#10644)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-355">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="5f5a0-356">Maak het algoritme voor de tekenreeksafstand van het suggestiesysteem niet-#10549 (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-356">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-357">Probleem met null-verwijzing opgelost in ForEach-Object - Parallelle invoerverwerking (#10577)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-357">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="5f5a0-358">Definities PowerShell Core groepsbeleid toevoegen (#10468)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-358">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="5f5a0-359">Werk de consolehost bij voor de ondersteuning van XTPUSHSGR/XTPOPSGR VT-besturingsreeksen die worden gebruikt in scenario's met opstellen.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-359">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="5f5a0-360">(#10208)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-360">(#10208)</span></span>
- <span data-ttu-id="5f5a0-361">Parameter WorkingDirectory toevoegen aan Start-Job (#10324) (Bedankt @davinci26 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-361">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="5f5a0-362">Verwijder de gebeurtenis-handler waardoor onderbrekingspuntwijzigingen ten onrechte zijn gerepliceerd naar het foutopsporingspunt van de hostrunspace (#10503) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-362">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5f5a0-363">Vervang api-ms-win-core-job-12-1-0.dll door Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-363">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-364">Foute uitvoer voor New-Service in variabele toewijzing en -OutVariable (#10444) (bedankt @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-364">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="5f5a0-365">Problemen met globale hulpprogramma's met betrekking tot de afsluitende code, opdrachtregelparameters en het pad met spaties (#10461)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-365">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="5f5a0-366">Recursie in OneDrive herstellen: wijzig FindFirstFileEx() in safeFindHandle-type (#10405)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-366">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="5f5a0-367">Het automatisch laden van PSReadLine in Windows overslaan als de NVDA-schermlezer actief is (#10385)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-367">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="5f5a0-368">Ingebouwde met PowerShell-moduleversies verhogen naar 7.0.0.0 (#10356)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-368">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="5f5a0-369">Voeg een foutmelding toe aan Add-Type als er al een type met dezelfde naam bestaat (#9609) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-369">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="5f5a0-370">Prestaties</span><span class="sxs-lookup"><span data-stu-id="5f5a0-370">Performance</span></span>

- <span data-ttu-id="5f5a0-371">Vermijd het gebruik van sluiting in Parser.SaveError (#11006)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-371">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="5f5a0-372">De caching verbeteren bij het maken van nieuwe Regex-exemplaren (#10657) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-372">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-373">De verwerking van de ingebouwde PowerShell-typegegevens van types.ps1xml, typesV3.ps1xml en GetEvent.types.ps1xml (#10898) verbeteren</span><span class="sxs-lookup"><span data-stu-id="5f5a0-373">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="5f5a0-374">WERK PSConfiguration.ReadValueFromFile bij om het sneller en efficiënter te maken (#10839)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-374">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="5f5a0-375">Kleine prestatieverbeteringen toevoegen voor runspace-initialisatie (#10569) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-375">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-376">Maak ForEach-Object sneller voor de veelgebruikte scenario's (#10454) en los ForEach-Object -Parallel-prestatieprobleem op met veel runspaces (#10455)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-376">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="5f5a0-377">Code opschonen</span><span class="sxs-lookup"><span data-stu-id="5f5a0-377">Code Cleanup</span></span>

- <span data-ttu-id="5f5a0-378">Opmerking en elementtekst wijzigen om te voldoen aan microsoft-standaarden (#11304)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-378">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="5f5a0-379">Problemen met opschoningsstijl in Compiler.cs (#10368) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-379">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-380">Verwijder de niet-gebruikte typeconverter voor CommaDelimitedStringCollection (#11000) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-380">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-381">Opschoningsstijl in InitialSessionState.cs (#10865) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-381">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-382">Code ops schonen voor pssession-klasse (#11001)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-382">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="5f5a0-383">Verwijder de niet-werkende functie 'run Update-Help uit Get-Help wanneer Get-Help voor het eerst wordt uitgevoerd' (#10974)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-383">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="5f5a0-384">Stijlproblemen oplossen (#10998) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-384">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-385">Opschonen: gebruik de ingebouwde typealias (#10882) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-385">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-386">Verwijder de niet-gebruikte instellingssleutel ConsolePrompting en vermijd onnodig maken van tekenreeksen bij het uitvoeren van query's op executionpolicy-instelling (#10985)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-386">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="5f5a0-387">Controle van updatemeldingen uitschakelen voor dagelijkse builds (#10903) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-387">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="5f5a0-388">De API voor het herstellen van debuggen in #10338 (#10808)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-388">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="5f5a0-389">Verwijder de referentie WorkflowJobSourceAdapter die niet meer wordt gebruikt (#10326) (Bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-389">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5f5a0-390">COM-interfaces in jumplist-code opschonen door PreserveSig-kenmerken (#9899) op te schonen (bedankt @weltkante !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-390">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="5f5a0-391">Voeg een opmerking toe waarin wordt beschreven waarom -ia niet de alias is voor de algemene parameter -InformationAction (#10703) (Bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-391">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5f5a0-392">Wijzig de naam invokeCommandCmdlet.cs in InvokeExpressionCommand.cs (#10659) (bedankt @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-392">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="5f5a0-393">Kleine code-opschoningen toevoegen met betrekking tot updatemeldingen (#10698)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-393">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="5f5a0-394">Afgeschafte werkstroomlogica verwijderen uit de installatiescripts voor remoting (#10320) (Bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-394">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5f5a0-395">Help-indeling bijwerken voor het gebruik van de juiste case (#10678) (Bedankt @tnieto88 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-395">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="5f5a0-396">Problemen met de CodeFactor-stijl opseen die in de afgelopen maand zijn #10591 (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-396">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-397">Typfout in beschrijving van experimentele functie PSTernaryOperator (#10586) opgelost (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-397">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="5f5a0-398">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-398">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5f5a0-399">Vervang ArrayList door List om beter leesbare en betrouwbare code te krijgen zonder de functionaliteit \<T> (#10333) te wijzigen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-399">Replace ArrayList with List\<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-400">Maak codestijlfixes voor TestConnectionCommand (#10439) (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-400">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5f5a0-401">AutomationEngine opschonen en extra methode-aanroep setSessionStateDrive (#10416) verwijderen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-401">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-402">Wijzig de naam van de standaardParameterSetName weer in Scheidingsteken voor ConvertTo-Csv en ConvertFrom-Csv (#10425)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-402">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="5f5a0-403">Hulpprogramma's</span><span class="sxs-lookup"><span data-stu-id="5f5a0-403">Tools</span></span>

- <span data-ttu-id="5f5a0-404">Voeg de standaardinstelling toe voor de eigenschap SDKToUse, zodat deze wordt opgebouwd in VS (#11085)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-404">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="5f5a0-405">Install-Powershell.ps1: Parameter toevoegen voor het gebruik van MSI-installatie (#10921) (Bedankt @MJECloud !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-405">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="5f5a0-406">Eenvoudige voorbeelden toevoegen voor install-powershell.ps1 (#10914) (bedankt @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-406">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="5f5a0-407">Maak Install-PowerShellRemoting.ps1 lege tekenreeks in de parameter PowerShellHome (#10526) (Bedankt @Orca88 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-407">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="5f5a0-408">Schakel over van /etc/lsb-release naar /etc/os-release in install-powershell.sh (#10773) (Bedankt @Himura2la !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-408">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="5f5a0-409">Controleer pwsh.exe en pwsh in de dagelijkse versie in Windows (#10738) (Bedankt @centreboard !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-409">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="5f5a0-410">Verwijder onnodig tikken in installpsh-osx.sh (#10752)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-410">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="5f5a0-411">Werk install-powershell.ps1 bij om te controleren of de dagelijkse build al is geïnstalleerd (#10489)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-411">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="5f5a0-412">Testen</span><span class="sxs-lookup"><span data-stu-id="5f5a0-412">Tests</span></span>

- <span data-ttu-id="5f5a0-413">Onbetrouwbare DSC-test in behandeling maken (#11131)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-413">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="5f5a0-414">Probleem met stringdata-test opgelost om sleutels van hashtabels correct te valideren (#10810)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-414">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="5f5a0-415">Testmodules (#11061) uit het geheugen verwijderd (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-415">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-416">Tijd tussen nieuwe test-URL's (#11015)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-416">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="5f5a0-417">Werk tests bij om testacties nauwkeurig te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-417">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="5f5a0-418">(#10928) (Bedankt @romero126 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-418">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="5f5a0-419">Sla de test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827) tijdelijk over</span><span class="sxs-lookup"><span data-stu-id="5f5a0-419">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="5f5a0-420">De gebeurtenis-handler stabiel laten lekken (#10790)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-420">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="5f5a0-421">Synchronisatie-hoofdletters in CI YAML (#10767) (Bedankt @RDIL !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-421">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="5f5a0-422">Test toevoegen voor het lekken van de gebeurtenis-handler (#10768)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-422">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="5f5a0-423">Een Get-ChildItem test (#10507) toevoegen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-423">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-424">Vervang ambigue taal voor tests van overschakelen naar parameter voor nauwkeurigheid (#10666) (Bedankt @romero126 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-424">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="5f5a0-425">Experimentele controle toevoegen aan ForEach-Object -Parallelle tests (#10354) (Bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-425">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="5f5a0-426">Updatetests voor Alpine-validatie (#10428)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-426">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="5f5a0-427">Verbeteringen in de build en het pakket</span><span class="sxs-lookup"><span data-stu-id="5f5a0-427">Build and Package Improvements</span></span>

- <span data-ttu-id="5f5a0-428">Probleem opgelost met nuget-pakket-ondertekening voor Coordinated Package build (#11316)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-428">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="5f5a0-429">Afhankelijkheden van PowerShell Gallery en NuGet (#11323)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-429">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="5f5a0-430">Microsoft.ApplicationInsights van 2.11.0 naar 2.12.0 (#11305)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-430">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="5f5a0-431">Microsoft.CodeAnalysis.CSharp van 3.3.1 naar 3.4.0 (#11265)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-431">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="5f5a0-432">Updates-pakketten voor Debian 10 en 11 (#11236)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-432">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="5f5a0-433">Schakel experimentele functies alleen in vóór RC (#11162)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-433">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="5f5a0-434">Minimale macOS-versie bijwerken (#11163)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-434">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="5f5a0-435">Bump NJsonSchema van 10.0.27 naar 10.0.28 (#11170)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-435">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="5f5a0-436">Koppelingen bijwerken in README.md en metadata.jspreview.5 (#10854)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-436">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="5f5a0-437">Selecteer de bestanden voor nalevingstests die eigendom zijn van PowerShell (#10837)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-437">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="5f5a0-438">Sta toe dat het win7x86 msix-pakket wordt gebouwd.</span><span class="sxs-lookup"><span data-stu-id="5f5a0-438">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="5f5a0-439">(Intern 10515)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-439">(Internal 10515)</span></span>
- <span data-ttu-id="5f5a0-440">Toestaan dat semantische versies worden doorgegeven aan de functie NormalizeVersion (#11087)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-440">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="5f5a0-441">Bump .NET Core Framework naar 3.1-preview.3 (#11079)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-441">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="5f5a0-442">Bump PSReadLine van 2.0.0-beta5 naar 2.0.0-beta6 in /src/Modules (#11078)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-442">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="5f5a0-443">Bump Newtonsoft.Jsvan 12.0.2 tot 12.0.3 (#11037) (#11038)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-443">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="5f5a0-444">Debian 10-, 11- en CentOS 8-pakketten (#11028)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-444">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="5f5a0-445">Upload Build-Info Json-bestand met het veld ReleaseDate (#10986)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-445">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="5f5a0-446">Bump .NET Core Framework naar 3.1-preview.2 (#10993)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-446">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="5f5a0-447">Build van x86 MSIX-pakket inschakelen (#10934)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-447">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="5f5a0-448">Werk de url voor het dotnet-SDK-installatiescript bij in build.psm1 (#10927)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-448">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="5f5a0-449">Bump Markdig.Signed van 0.17.1 tot 0.18.0 (#10887)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-449">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="5f5a0-450">Bump ThreadJob van 2.0.1 tot 2.0.2 (#10886)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-450">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="5f5a0-451">Module AppX-manifest en -verpakking bijwerken om te voldoen aan de MS Store-vereisten (#10878)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-451">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="5f5a0-452">Update package reference for PowerShell SDK to preview.5 (Internal 10295) (Pakketverwijzing voor PowerShell SDK bijwerken naar preview.5 (Internal 10295)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-452">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="5f5a0-453">Update ThirdPartyNotices.txt (#10834)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-453">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="5f5a0-454">Bump Microsoft.PowerShell.Native naar 7.0.0-preview.3 (#10826)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-454">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="5f5a0-455">Microsoft.ApplicationInsights van 2.10.0 naar 2.11.0 (#10608)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-455">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="5f5a0-456">Bump NJsonSchema van 10.0.24 naar 10.0.27 (#10756)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-456">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="5f5a0-457">MacPorts-ondersteuning toevoegen aan het buildsysteem (#10736) (Bedankt @Lucius-Q-User !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-457">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="5f5a0-458">Bump PackageManagement van 1.4.4 tot 1.4.5 (#10728)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-458">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="5f5a0-459">Bump NJsonSchema van 10.0.23 naar 10.0.24 (#10635)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-459">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="5f5a0-460">Omgevingsvariabele toevoegen om onderscheid te maken tussen client-/server-telemetrie in MSI (#10612)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-460">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="5f5a0-461">Bump PSDesiredStateConfiguration van 2.0.3 naar 2.0.4 (#10603)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-461">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="5f5a0-462">Bump Microsoft.CodeAnalysis.CSharp van 3.2.1 naar 3.3.1 (#10607)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-462">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="5f5a0-463">Bijwerken naar .Net Core 3.0 RTM (#10604) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-463">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="5f5a0-464">MSIX-verpakking bijwerken zodat de versie voldoet aan de Windows Store-vereisten (#10588)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-464">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="5f5a0-465">Bump PowerShellGet-versie van 2.2 naar 2.2.1 (#10382)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-465">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="5f5a0-466">Bump PackageManagement versie van 1.4.3 tot 1.4.4 (#10383)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-466">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="5f5a0-467">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-467">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="5f5a0-468">.Net Core 3.0-versie upgraden van Preview 9 naar RC1 (#10552) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-468">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="5f5a0-469">ExperimentalFeature-lijstgeneratie opgelost (interne 9996)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-469">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="5f5a0-470">Bump PSReadLine-versie van 2.0.0-beta4 naar 2.0.0-beta5 (#10536)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-470">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="5f5a0-471">Buildscript van release opgelost om releasetag in te stellen</span><span class="sxs-lookup"><span data-stu-id="5f5a0-471">Fix release build script to set release tag</span></span>
- <span data-ttu-id="5f5a0-472">Versie van Microsoft.PowerShell.Native bijgewerkt naar 7.0.0-preview.2 (#10519)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-472">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="5f5a0-473">Upgrade naar Netcoreapp3.0 preview9 (#10484) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-473">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="5f5a0-474">Zorg ervoor dat de dagelijkse gecoördineerde build weet dat het een dagelijkse build is (#10464)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-474">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="5f5a0-475">Werk de gecombineerde pakket-build bij om de dagelijkse builds (#10449)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-475">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="5f5a0-476">Verwijzing appveyor (#10445) verwijderen (bedankt @RDIL !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-476">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="5f5a0-477">Bump NJsonSchema-versie van 10.0.22 tot 10.0.23 (#10421)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-477">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="5f5a0-478">Verwijder de verwijdering van de buildmap linux-x64 omdat sommige afhankelijkheden voor Alpine deze nodig hebben (#10407)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-478">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="5f5a0-479">Documentatie en Help-inhoud</span><span class="sxs-lookup"><span data-stu-id="5f5a0-479">Documentation and Help Content</span></span>

- <span data-ttu-id="5f5a0-480">Wijzigingslogboeken herfactoren in één logboek per release (#11165)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-480">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="5f5a0-481">Probleem opgelost met online Help-documenten voor FWLinks voor PowerShell 7 (#11071)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-481">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="5f5a0-482">Werk CONTRIBUTING.md (#11096) bij (bedankt @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-482">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="5f5a0-483">Koppelingen naar installatie docs in README.md (#11083)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-483">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="5f5a0-484">Voegt voorbeelden toe aan install-powershell.ps1 script (#11024) (bedankt @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-484">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="5f5a0-485">Oplossing voor Select-String nadruk en Import-DscResource in CHANGELOG.md (#10890)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-485">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="5f5a0-486">Verwijder de verouderde koppeling uit powershell-beginners-guide.md (#10926)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-486">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="5f5a0-487">Stabiele wijzigingslogboeken en onderhoudswijzigingslogboeken samenvoegen (#10527)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-487">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="5f5a0-488">Gebruikte .NET-versie bijgewerkt in build docs (#10775) (Bedankt @Greg-Smulko !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-488">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="5f5a0-489">Koppelingen van MSDN vervangen docs.microsoft.com in powershell-beginners-guide.md (#10778) (Bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-489">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="5f5a0-490">Verbroken DSC-overzichtskoppeling (#10702)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-490">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="5f5a0-491">Werk Support_Question.md bij om een koppeling naar Stack Overflow te maken als een andere communityresource (#10638) (Bedankt @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-491">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="5f5a0-492">Processorarchitectuur toevoegen aan distributieaanvraagsjabloon (#10661)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-492">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="5f5a0-493">Nieuw PowerShell MoL-boek toevoegen om PowerShell-documenten (#10602)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-493">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="5f5a0-494">De README.md en metagegevens bijwerken voor versies van v6.1.6 en v6.2.3 (#10523)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-494">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="5f5a0-495">Typfout in README.md (#10465) opgelost (bedankt @vedhasp !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-495">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="5f5a0-496">Voeg een verwijzing naar de PSKoans-module toe aan de documentatie over Learning Resources (#10369) (Bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-496">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="5f5a0-497">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span><span class="sxs-lookup"><span data-stu-id="5f5a0-497">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
