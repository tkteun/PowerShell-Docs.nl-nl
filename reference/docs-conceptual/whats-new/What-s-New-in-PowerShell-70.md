---
title: Wat is er nieuw in Power shell 7,0
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell 7,0
ms.date: 03/04/2020
ms.openlocfilehash: d52b536efd9d7a1f8e6b01a58952f08ca49016b1
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162457"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="36e9d-103">Wat is er nieuw in Power shell 7,0</span><span class="sxs-lookup"><span data-stu-id="36e9d-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="36e9d-104">Power shell 7,0 is een open-source, platformoverschrijdende versie van het platform (Windows, macOS en Linux) van Power shell, gebouwd voor het beheren van heterogene omgevingen en hybride Cloud.</span><span class="sxs-lookup"><span data-stu-id="36e9d-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="36e9d-105">In deze release introduceren we een aantal nieuwe functies, waaronder:</span><span class="sxs-lookup"><span data-stu-id="36e9d-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="36e9d-106">Pijp lijn parallel Lise ring met `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="36e9d-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="36e9d-107">Nieuwe Opera tors:</span><span class="sxs-lookup"><span data-stu-id="36e9d-107">New operators:</span></span>
  - <span data-ttu-id="36e9d-108">Ternaire operator: `a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="36e9d-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="36e9d-109">Pijplijn keten operators: `||` en `&&`</span><span class="sxs-lookup"><span data-stu-id="36e9d-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="36e9d-110">Null-voorwaardelijke Opera tors: `??` en `??=`</span><span class="sxs-lookup"><span data-stu-id="36e9d-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="36e9d-111">Een vereenvoudigde en dynamische fout weergave en- `Get-Error` cmdlet voor eenvoudiger onderzoek van fouten</span><span class="sxs-lookup"><span data-stu-id="36e9d-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="36e9d-112">Een compatibiliteit slaag waarmee gebruikers modules kunnen importeren in een impliciete Windows Power shell-sessie</span><span class="sxs-lookup"><span data-stu-id="36e9d-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="36e9d-113">Meldingen voor automatische nieuwe versie</span><span class="sxs-lookup"><span data-stu-id="36e9d-113">Automatic new version notifications</span></span>
- <span data-ttu-id="36e9d-114">De mogelijkheid om DSC-resources rechtstreeks vanuit Power shell 7 aan te roepen (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="36e9d-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="36e9d-115">Zie de [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)voor een volledige lijst met functies en oplossingen.</span><span class="sxs-lookup"><span data-stu-id="36e9d-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="36e9d-116">Waar kan ik Power Shell installeren?</span><span class="sxs-lookup"><span data-stu-id="36e9d-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="36e9d-117">Power shell 7 biedt momenteel ondersteuning voor de volgende besturings systemen op x64, waaronder:</span><span class="sxs-lookup"><span data-stu-id="36e9d-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="36e9d-118">Windows 8,1 en 10</span><span class="sxs-lookup"><span data-stu-id="36e9d-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="36e9d-119">Windows Server 2012, 2012 R2, 2016 en 2019</span><span class="sxs-lookup"><span data-stu-id="36e9d-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="36e9d-120">macOS 10.13 +</span><span class="sxs-lookup"><span data-stu-id="36e9d-120">macOS 10.13+</span></span>
- <span data-ttu-id="36e9d-121">Red Hat Enterprise Linux (RHEL)/CentOS 7</span><span class="sxs-lookup"><span data-stu-id="36e9d-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="36e9d-122">Fedora 30 +</span><span class="sxs-lookup"><span data-stu-id="36e9d-122">Fedora 30+</span></span>
- <span data-ttu-id="36e9d-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="36e9d-123">Debian 9</span></span>
- <span data-ttu-id="36e9d-124">Ubuntu LTS 16.04 +</span><span class="sxs-lookup"><span data-stu-id="36e9d-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="36e9d-125">Alpine Linux 3.8 +</span><span class="sxs-lookup"><span data-stu-id="36e9d-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="36e9d-126">Daarnaast ondersteunt Power shell 7,0 ARM32-en ARM64-smaakten van Debian, Ubuntu en ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="36e9d-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="36e9d-127">Controleer de installatie-instructies voor uw favoriete besturings systeem [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7)of [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span></span>

<span data-ttu-id="36e9d-128">Hoewel niet officieel wordt ondersteund, heeft de community ook pakketten voor [Arch](https://aur.archlinux.org/packages/powershell/) en Kali Linux verschaft.</span><span class="sxs-lookup"><span data-stu-id="36e9d-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-129">Debian 10 en CentOS 8 bieden momenteel geen ondersteuning voor externe toegang via WinRM.</span><span class="sxs-lookup"><span data-stu-id="36e9d-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="36e9d-130">Zie voor meer informatie over het instellen van op SSH gebaseerde externe communicatie [Power shell voor externe toegang via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span></span>

<span data-ttu-id="36e9d-131">Zie de [Power shell-ondersteunings levenscyclus](/powershell/scripting/powershell-support-lifecycle?view=powershell-7)voor meer actuele informatie over de ondersteunde besturings systemen en de levens cyclus van de ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="36e9d-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="36e9d-132">Power shell 7 wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="36e9d-132">Running PowerShell 7</span></span>

<span data-ttu-id="36e9d-133">Power shell 7 installeert in een map, gescheiden van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="36e9d-133">PowerShell 7 installs to a directory seperately from Windows PowerShell.</span></span>
<span data-ttu-id="36e9d-134">Hierdoor kunt u Power shell 7 naast Windows Power shell 5,1 uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="36e9d-134">This enables you to run PowerShell 7 side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="36e9d-135">Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="36e9d-135">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="36e9d-136">Power shell 7 is geïnstalleerd op `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="36e9d-136">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="36e9d-137">De `%programfiles%\PowerShell\7` map wordt toegevoegd aan `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="36e9d-137">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="36e9d-138">Het Power shell 7 Installer-pakket upgradet eerdere versies van Power shell Core 6. x:</span><span class="sxs-lookup"><span data-stu-id="36e9d-138">The PowerShell 7 installer package upgrades previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="36e9d-139">Power shell Core 6. x op Windows: `%programfiles%\PowerShell\6` wordt vervangen door `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="36e9d-139">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="36e9d-140">Linux: `/opt/microsoft/powershell/6` is vervangen door `/opt/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="36e9d-140">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="36e9d-141">macOS: `/usr/local/microsoft/powershell/6` wordt vervangen door `/usr/local/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="36e9d-141">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-142">In Windows Power shell heet het uitvoer bare bestand voor het starten van Power shell `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-142">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="36e9d-143">In versie 6 en hoger wordt de naam van het uitvoer bare bestand gewijzigd voor ondersteuning van gelijktijdige uitvoering.</span><span class="sxs-lookup"><span data-stu-id="36e9d-143">In version 6 and above, the executable name is changed to support side-by-side execution.</span></span> <span data-ttu-id="36e9d-144">De nieuwe naam van het uitvoer bare bestand voor het starten van Power shell 7 is `pwsh.exe` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-144">The new executable name to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="36e9d-145">Preview-builds blijven in-place, net als in `pwsh-preview` `pwsh` de map 7-Preview.</span><span class="sxs-lookup"><span data-stu-id="36e9d-145">Preview builds remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="36e9d-146">Verbeterde achterwaartse compatibiliteit met Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="36e9d-146">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="36e9d-147">Power shell 7,0 markeert een verplaatsing van a naar .NET Core 3,1, waardoor aanzienlijk neerwaartse compatibiliteit met bestaande Windows Power shell-modules mogelijk wordt.</span><span class="sxs-lookup"><span data-stu-id="36e9d-147">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="36e9d-148">Dit omvat veel modules in Windows waarvoor GUI-functionaliteit is vereist, evenals een `Out-GridView` `Show-Command` groot aantal rollen beheer modules die worden geleverd als onderdeel van Windows.</span><span class="sxs-lookup"><span data-stu-id="36e9d-148">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="36e9d-149">Voor Windows wordt een nieuwe switch parameter **UseWindowsPowerShell** toegevoegd aan `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-149">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="36e9d-150">Met deze switch maakt u een proxy module in Power shell 7 die gebruikmaakt van een lokaal Windows Power Shell-proces om impliciet alle cmdlets in die module uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="36e9d-150">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="36e9d-151">Voor meer informatie over [import-module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-151">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span></span>

<span data-ttu-id="36e9d-152">Zie de [module Compatibility Table](https://aka.ms/PSModuleCompat)voor meer informatie over welke micro soft-modules met power shell 7,0 werken.</span><span class="sxs-lookup"><span data-stu-id="36e9d-152">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="36e9d-153">Parallelle uitvoering toegevoegd aan ForEach-object</span><span class="sxs-lookup"><span data-stu-id="36e9d-153">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="36e9d-154">De `ForEach-Object` cmdlet, waarmee items in een verzameling worden herhaald, heeft nu een ingebouwde parallellisme met de nieuwe **parallelle** para meter.</span><span class="sxs-lookup"><span data-stu-id="36e9d-154">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="36e9d-155">Parallelle script blokken gebruiken standaard de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="36e9d-155">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="36e9d-156">In dit voor beeld worden 50.000 logboek vermeldingen van 5 systeem logboeken op een lokale Windows-computer opgehaald:</span><span class="sxs-lookup"><span data-stu-id="36e9d-156">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="36e9d-157">Met de **parallelle** para meter wordt het script blok opgegeven dat parallel wordt uitgevoerd voor elke invoer logboek naam.</span><span class="sxs-lookup"><span data-stu-id="36e9d-157">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="36e9d-158">De nieuwe **ThrottleLimit** -para meter beperkt het aantal script blokken dat gelijktijdig wordt uitgevoerd op een bepaald moment.</span><span class="sxs-lookup"><span data-stu-id="36e9d-158">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="36e9d-159">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="36e9d-159">The default is 5.</span></span>

<span data-ttu-id="36e9d-160">Gebruik de `$_` variabele om het huidige invoer object in het-script blok weer te geven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-160">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="36e9d-161">Gebruik het `$using:` bereik om variabele verwijzingen naar het uitgevoerde script blok door te geven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-161">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="36e9d-162">Voor meer informatie over [foreach-object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-162">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="36e9d-163">Ternaire operator</span><span class="sxs-lookup"><span data-stu-id="36e9d-163">Ternary operator</span></span>

<span data-ttu-id="36e9d-164">Power shell 7,0 introduceert een ternaire operator die zich als een vereenvoudigde `if-else` instructie gedraagt.</span><span class="sxs-lookup"><span data-stu-id="36e9d-164">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="36e9d-165">De ternaire operator van Power shell is nauw keurig gemodelleerd vanuit de syntaxis van de C# ternaire operator:</span><span class="sxs-lookup"><span data-stu-id="36e9d-165">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="36e9d-166">De voor waarde-expressie wordt altijd geëvalueerd en het resultaat wordt omgezet in een **Booleaanse** waarde om te bepalen welke vertakking vervolgens wordt geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-166">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="36e9d-167">De `<if-true>` expressie wordt uitgevoerd als de `<condition>` expressie True is</span><span class="sxs-lookup"><span data-stu-id="36e9d-167">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="36e9d-168">De `<if-false>` expressie wordt uitgevoerd als de `<condition>` expressie onwaar is</span><span class="sxs-lookup"><span data-stu-id="36e9d-168">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="36e9d-169">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="36e9d-169">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="36e9d-170">In dit voor beeld als het pad bestaat, wordt het **pad** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-170">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="36e9d-171">Als het pad niet bestaat, wordt het **pad niet gevonden** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-171">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="36e9d-172">Voor meer informatie [over als](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-172">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="36e9d-173">Opera tors voor pijplijn keten</span><span class="sxs-lookup"><span data-stu-id="36e9d-173">Pipeline chain operators</span></span>

<span data-ttu-id="36e9d-174">Power shell 7 implementeert `&&` de `||` Opera tors en om pijp lijnen voorwaardelijk te koppelen.</span><span class="sxs-lookup"><span data-stu-id="36e9d-174">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="36e9d-175">Deze opera tors zijn bekend in Power shell als Opera tors voor pipeline-ketens en zijn vergelijkbaar met en en of lijsten in schalen zoals **bash** en **zsh**, evenals voorwaardelijke verwerkings symbolen in de Windows-opdracht shell (**cmd.exe**).</span><span class="sxs-lookup"><span data-stu-id="36e9d-175">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="36e9d-176">De `&&` operator voert de rechter pijplijn uit, als de pijplijn is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="36e9d-176">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="36e9d-177">De operator voert daarentegen `||` de rechter pijp lijn uit als de linker pijp lijn is mislukt.</span><span class="sxs-lookup"><span data-stu-id="36e9d-177">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-178">Deze opera tors gebruiken `$?` de `$LASTEXITCODE` variabelen en om te bepalen of een pijp lijn is mislukt.</span><span class="sxs-lookup"><span data-stu-id="36e9d-178">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="36e9d-179">Hierdoor kunt u ze gebruiken met systeem eigen opdrachten en niet alleen met cmdlets of functies.</span><span class="sxs-lookup"><span data-stu-id="36e9d-179">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="36e9d-180">Hier is de eerste opdracht geslaagd en de tweede opdracht wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-180">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="36e9d-181">De eerste opdracht mislukt, de tweede wordt niet uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-181">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="36e9d-182">De eerste opdracht slaagt, de tweede opdracht wordt niet uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-182">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="36e9d-183">De eerste opdracht mislukt, dus de tweede opdracht wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-183">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="36e9d-184">Voor meer informatie [over pijplijn keten operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-184">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="36e9d-185">Null-samen voegen, toewijzings-en voorwaardelijke Opera tors</span><span class="sxs-lookup"><span data-stu-id="36e9d-185">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="36e9d-186">Power shell 7 bevat een null-samenvoegings operator `??` , voorwaardelijke toewijzing van Null `??=` en null-toegangs operatoren van het voorwaardelijke lid, en `?.` `?[]` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-186">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="36e9d-187">Null-samenvoegings operator?</span><span class="sxs-lookup"><span data-stu-id="36e9d-187">Null-coalescing Operator ??</span></span>

<span data-ttu-id="36e9d-188">De operator null-samenvoeging `??` retourneert de waarde van de linkeroperand als deze niet null is.</span><span class="sxs-lookup"><span data-stu-id="36e9d-188">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="36e9d-189">Anders wordt de rechter operand geëvalueerd en wordt het resultaat geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36e9d-189">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="36e9d-190">De `??` operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="36e9d-190">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="36e9d-191">In het volgende voor beeld wordt de rechter operand niet geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-191">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="36e9d-192">Operator voor voorwaardelijke toewijzing van Null? =</span><span class="sxs-lookup"><span data-stu-id="36e9d-192">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="36e9d-193">De operator voor voorwaardelijke toewijzing met Null `??=` wijst de waarde van de rechter operand toe aan de linkeroperand alleen als de linkeroperand wordt geëvalueerd als null.</span><span class="sxs-lookup"><span data-stu-id="36e9d-193">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="36e9d-194">De `??=` operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.</span><span class="sxs-lookup"><span data-stu-id="36e9d-194">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="36e9d-195">In het volgende voor beeld wordt de rechter operand niet geëvalueerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-195">In the following example, the right-hand operand is not evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="36e9d-196">Null-Opera tors voor voorwaardelijk leden?.</span><span class="sxs-lookup"><span data-stu-id="36e9d-196">Null conditional member access operators ?.</span></span> <span data-ttu-id="36e9d-197">maar? [] (Experimenteel)</span><span class="sxs-lookup"><span data-stu-id="36e9d-197">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-198">Dit is een experimentele functie met de naam **PSNullConditionalOperators**.</span><span class="sxs-lookup"><span data-stu-id="36e9d-198">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="36e9d-199">Meer informatie [over experimentele functies](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-199">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="36e9d-200">Een voorwaardelijke operator met een null-waarde heeft leden toegang, `?.` , of element toegang, `?[]` alleen toegestaan voor de operand als die operand resulteert in niet-null; anders wordt Null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36e9d-200">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-201">Aangezien Power shell `?` een deel van de naam van de variabele toestaat, is formele specificatie van de naam van de variabele vereist voor het gebruik van deze opera tors.</span><span class="sxs-lookup"><span data-stu-id="36e9d-201">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="36e9d-202">Het is dus nood zakelijk om `{}` de namen van variabelen te gebruiken, zoals `${a}` of wanneer `?` het een deel van de naam van de variabele is `${a?}` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-202">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="36e9d-203">In het volgende voor beeld wordt de waarde van **de lideigenschap geretourneerd** :</span><span class="sxs-lookup"><span data-stu-id="36e9d-203">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="36e9d-204">In het volgende voor beeld wordt Null geretourneerd zonder dat u toegang probeert te krijgen tot de **status**van de lidnaam:</span><span class="sxs-lookup"><span data-stu-id="36e9d-204">The following example returns null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="36e9d-205">Op dezelfde manier `?[]` wordt met de waarde van het element geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-205">Similarly, using `?[]`, the value of the element is returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="36e9d-206">En als de operand null is, wordt het element niet geopend en wordt Null geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="36e9d-206">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="36e9d-207">[About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36e9d-207">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="36e9d-208">Nieuwe weer gave-ConciseView en cmdlet Get-fout</span><span class="sxs-lookup"><span data-stu-id="36e9d-208">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="36e9d-209">Power shell 7,0 verbetert de weer gave van fout berichten om de Lees baarheid van interactieve en script fouten te verbeteren met een nieuwe standaard weergave **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="36e9d-209">PowerShell 7.0 enhances the display of error messages to improve the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="36e9d-210">De weer gaven kunnen door de gebruiker worden geselecteerd via de voorkeurs variabele `$ErrorView` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-210">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="36e9d-211">Als een fout niet is opgetreden in een script of parserfout, wordt met **ConciseView**een fout bericht met één regel weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="36e9d-211">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="36e9d-212">Als de fout optreedt tijdens het uitvoeren van een script of als het een Parseerfout is, retourneert Power shell een fout bericht met meerdere regels met de fout, een wijzer en een fout bericht waarin wordt aangegeven waar de fout zich op die regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="36e9d-212">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="36e9d-213">Als de Terminal geen ANSI-escape reeksen (VT100) ondersteunt, worden er geen kleuren weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-213">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![Fout bij het weer geven van een script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="36e9d-215">De standaard weergave in Power shell 7 is **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="36e9d-215">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="36e9d-216">De vorige standaard weergave is **NormalView** en u kunt de voorkeurs variabele thisby instellen `$ErrorView` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-216">The previous default view was **NormalView** and you can select thisby setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="36e9d-217">Er wordt een nieuwe eigenschap **ErrorAccentColor** toegevoegd ter `$Host.PrivateData` ondersteuning van het wijzigen van de accent kleur van het fout bericht.</span><span class="sxs-lookup"><span data-stu-id="36e9d-217">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="36e9d-218">Een nieuwe cmdlet `Get-Error` biedt een volledig gedetailleerde weer gave van de volledig gekwalificeerde fout, indien gewenst.</span><span class="sxs-lookup"><span data-stu-id="36e9d-218">A new cmdlet `Get-Error` provides a complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="36e9d-219">Standaard worden de volledige details van de cmdlet weer gegeven, met inbegrip van interne uitzonde ringen, van de laatste fout die is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="36e9d-219">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![Weer geven bij Get-error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="36e9d-221">De `Get-Error` cmdlet ondersteunt invoer van de pijp lijn met behulp van de ingebouwde variabele `$Error` .</span><span class="sxs-lookup"><span data-stu-id="36e9d-221">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="36e9d-222">`Get-Error` alle gesluisde fouten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-222">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="36e9d-223">De `Get-Error` cmdlet ondersteunt de **nieuwste** para meter, zodat u kunt opgeven hoeveel fouten van de huidige sessie u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-223">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="36e9d-224">Voor meer informatie over [Get-error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-224">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="36e9d-225">Melding voor nieuwe versie</span><span class="sxs-lookup"><span data-stu-id="36e9d-225">New version notification</span></span>

<span data-ttu-id="36e9d-226">Power shell 7 gebruikt update meldingen om gebruikers te waarschuwen dat er updates zijn voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="36e9d-226">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="36e9d-227">Eenmaal per dag vraagt Power shell een online service aan om te bepalen of er een nieuwere versie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="36e9d-227">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-228">De update controle wordt uitgevoerd tijdens de eerste sessie binnen een bepaalde periode van 24 uur.</span><span class="sxs-lookup"><span data-stu-id="36e9d-228">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="36e9d-229">Om prestatie redenen wordt de update controle drie seconden na het starten van de sessie gestart.</span><span class="sxs-lookup"><span data-stu-id="36e9d-229">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="36e9d-230">De melding wordt alleen weer gegeven aan het begin van volgende sessies.</span><span class="sxs-lookup"><span data-stu-id="36e9d-230">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="36e9d-231">Power shell abonneert standaard op een van twee verschillende meldings kanalen, afhankelijk van de versie/vertakking.</span><span class="sxs-lookup"><span data-stu-id="36e9d-231">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="36e9d-232">Ondersteunde, algemeen beschik bare (GA) versies van Power shell retour neren alleen meldingen voor bijgewerkte GA-releases.</span><span class="sxs-lookup"><span data-stu-id="36e9d-232">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="36e9d-233">Preview en release Candi date (RC) geven een melding van updates voor preview-, RC-en GA-releases.</span><span class="sxs-lookup"><span data-stu-id="36e9d-233">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="36e9d-234">Het gedrag van de update melding kan worden gewijzigd met behulp van de `$Env:POWERSHELL_UPDATECHECK` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="36e9d-234">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="36e9d-235">De volgende waarden worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="36e9d-235">The following values are supported:</span></span>

- <span data-ttu-id="36e9d-236">De **standaard waarde** is hetzelfde als niet definiëren`$Env:POWERSHELL_UPDATECHECK`</span><span class="sxs-lookup"><span data-stu-id="36e9d-236">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="36e9d-237">GA releases op de hoogte van updates voor GA releases</span><span class="sxs-lookup"><span data-stu-id="36e9d-237">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="36e9d-238">Preview/RC geeft melding van updates voor GA-en Preview-versies</span><span class="sxs-lookup"><span data-stu-id="36e9d-238">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="36e9d-239">Met **uitschakelen** wordt de functie voor update meldingen uitgeschakeld</span><span class="sxs-lookup"><span data-stu-id="36e9d-239">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="36e9d-240">**LTS** brengt alleen berichten op de hoogte van updates voor LTS-ga (Long-term-Servicing)</span><span class="sxs-lookup"><span data-stu-id="36e9d-240">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-241">De omgevings variabele `$Env:POWERSHELL_UPDATECHECK` bestaat niet totdat deze voor de eerste keer is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="36e9d-241">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="36e9d-242">Als u de versie melding alleen voor releases wilt instellen `LTS` :</span><span class="sxs-lookup"><span data-stu-id="36e9d-242">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="36e9d-243">De versie melding instellen op het `Default` gedrag:</span><span class="sxs-lookup"><span data-stu-id="36e9d-243">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="36e9d-244">Voor meer informatie [over meldingen over updates](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-244">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="36e9d-245">Nieuwe ondersteuning voor DSC-resources met invoke-Dscresource bieden (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="36e9d-245">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="36e9d-246">Dit is een experimentele functie met de naam **PSDesiredStateConfiguration. InvokeDscResource**.</span><span class="sxs-lookup"><span data-stu-id="36e9d-246">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="36e9d-247">Meer informatie [over experimentele functies](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-247">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="36e9d-248">`Invoke-DscResource`Met de cmdlet wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.</span><span class="sxs-lookup"><span data-stu-id="36e9d-248">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="36e9d-249">Met deze cmdlet wordt een DSC-resource rechtstreeks aangeroepen zonder dat er een configuratie document wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="36e9d-249">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="36e9d-250">Met deze cmdlet kunnen Configuration Management-producten Windows of Linux beheren met behulp van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="36e9d-250">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="36e9d-251">Met deze cmdlet schakelt u ook fout opsporing van resources in wanneer de DSC-engine wordt uitgevoerd met fout opsporing ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="36e9d-251">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="36e9d-252">Met deze opdracht wordt de **set** -methode van een resource met de naam **WindowsProcess** aangeroepen en worden de eigenschappen van het verplichte **pad** en de **argumenten** opgegeven om het gespecificeerde Windows-proces te starten.</span><span class="sxs-lookup"><span data-stu-id="36e9d-252">This command invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

<span data-ttu-id="36e9d-253">Voor meer informatie over [invoke-dscresource bieden](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="36e9d-253">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="36e9d-254">Wijzigingen en verbeteringen te verbreken</span><span class="sxs-lookup"><span data-stu-id="36e9d-254">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="36e9d-255">Wijzigingen die fouten veroorzaken</span><span class="sxs-lookup"><span data-stu-id="36e9d-255">Breaking Changes</span></span>

- <span data-ttu-id="36e9d-256">Update melding maken ondersteuning voor LTS en standaard kanalen (#11132)</span><span class="sxs-lookup"><span data-stu-id="36e9d-256">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="36e9d-257">Test-verbinding bijwerken zodat deze meer werkt zoals in Windows Power shell (#10697) (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-257">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="36e9d-258">$ Behouden?</span><span class="sxs-lookup"><span data-stu-id="36e9d-258">Preserve $?</span></span> <span data-ttu-id="36e9d-259">voor ParenExpression, subexpressie en ArrayExpression (#11040)</span><span class="sxs-lookup"><span data-stu-id="36e9d-259">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="36e9d-260">Werkmap instellen op huidige map in start-Job (#10920) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-260">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-261">$PSCulture consistent weer geven in wijzigingen in de sessie cultuur (#10138) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-261">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="36e9d-262">Engine-updates en-oplossingen</span><span class="sxs-lookup"><span data-stu-id="36e9d-262">Engine Updates and Fixes</span></span>

- <span data-ttu-id="36e9d-263">Verbeteringen in Break Point-Api's voor externe scenario's (#11312)</span><span class="sxs-lookup"><span data-stu-id="36e9d-263">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="36e9d-264">Een lekkende definitie van een Power shell-klasse oplossen in een andere runs Pace (#11273)</span><span class="sxs-lookup"><span data-stu-id="36e9d-264">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="36e9d-265">Een regressie in de opmaak herstellen, veroorzaakt door de FirstOrDefault-primitieve die is toegevoegd in 7.0.0-Preview1 (#11258)</span><span class="sxs-lookup"><span data-stu-id="36e9d-265">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="36e9d-266">Aanvullende micro soft-modules voor het bijhouden van PS7-telemetrie (#10751)</span><span class="sxs-lookup"><span data-stu-id="36e9d-266">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="36e9d-267">Goedgekeurde functies maken zonder experimentele (#11303)</span><span class="sxs-lookup"><span data-stu-id="36e9d-267">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="36e9d-268">ConciseView bijwerken voor het gebruik van target object, indien van toepassing (#11075)</span><span class="sxs-lookup"><span data-stu-id="36e9d-268">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="36e9d-269">NullReferenceException in CompletionCompleters Public-methoden oplossen (#11274)</span><span class="sxs-lookup"><span data-stu-id="36e9d-269">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="36e9d-270">Status controle van apartment-thread op niet-Windows-platforms herstellen (#11301)</span><span class="sxs-lookup"><span data-stu-id="36e9d-270">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="36e9d-271">Update-instelling PSModulePath om de variabelen process en machine Environment samen te voegen (#11276)</span><span class="sxs-lookup"><span data-stu-id="36e9d-271">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="36e9d-272">Beduw .NET core naar 3.1.0 (#11260)</span><span class="sxs-lookup"><span data-stu-id="36e9d-272">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="36e9d-273">Detectie van $PSHOME voor $env:P AD (#11141) oplossen</span><span class="sxs-lookup"><span data-stu-id="36e9d-273">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="36e9d-274">Toestaan dat pwsh overneemt $env:P SModulePath en dat powershell.exe correct wordt gestart (#11057)</span><span class="sxs-lookup"><span data-stu-id="36e9d-274">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="36e9d-275">Naar .NET Core 3,1 Preview 1 (#10798)</span><span class="sxs-lookup"><span data-stu-id="36e9d-275">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="36e9d-276">Controles van reparse-Tags in de bestandssysteem provider (#10431) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-276">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-277">Vervang CR en New line door een 0x23CE-teken in script logging (#10616)</span><span class="sxs-lookup"><span data-stu-id="36e9d-277">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="36e9d-278">Los een bron lekkage op door de registratie van de gebeurtenis-handler van AppDomain. CurrentDomain. ProcessExit (#10626) ongedaan te maken.</span><span class="sxs-lookup"><span data-stu-id="36e9d-278">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="36e9d-279">Voeg ondersteuning toe aan ActionPreference. Store om in het fout opsporingsprogramma te kraken wanneer fout opsporing, fout, informatie, voortgang, uitgebreide of waarschuwings berichten worden gegenereerd (#8205) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-279">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="36e9d-280">Schakel het starten van invoeg toepassingen in het configuratie scherm in Power shell core in zonder op te geven. CPL-extensie.</span><span class="sxs-lookup"><span data-stu-id="36e9d-280">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="36e9d-281">(#9828)</span><span class="sxs-lookup"><span data-stu-id="36e9d-281">(#9828)</span></span>
- <span data-ttu-id="36e9d-282">Ondersteuning voor negatieve getallen in de Splits operator (#8960) (bedankt @ece-jacob-scott !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-282">Support negative numbers in -split operator (#8960) (Thanks @ece-jacob-scott!)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="36e9d-283">Algemene cmdlet-updates en-oplossingen</span><span class="sxs-lookup"><span data-stu-id="36e9d-283">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="36e9d-284">Oplossing voor probleem op Raspbian voor het instellen van de datum van bestands wijzigingen in de UnixStat experimentele functie (#11313)</span><span class="sxs-lookup"><span data-stu-id="36e9d-284">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="36e9d-285">Add-AsPlainText voor ConvertFrom-SecureString (#11142)</span><span class="sxs-lookup"><span data-stu-id="36e9d-285">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="36e9d-286">Controle van WindowsPS-versie toegevoegd voor WinCompat (#11148)</span><span class="sxs-lookup"><span data-stu-id="36e9d-286">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="36e9d-287">Fout rapportage oplossen in sommige WinCompat-scenario's (#11259)</span><span class="sxs-lookup"><span data-stu-id="36e9d-287">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="36e9d-288">Systeem eigen binaire resolver (#11032) toevoegen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-288">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-289">De berekening van de teken breedte bijwerken om de CJK-tekens correct te respecteren (#11262)</span><span class="sxs-lookup"><span data-stu-id="36e9d-289">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="36e9d-290">Deblokkeren toevoegen-bestand voor macOS (#11137)</span><span class="sxs-lookup"><span data-stu-id="36e9d-290">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="36e9d-291">Regressie in Get-PSCallStack (#11210) oplossen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-291">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-292">Autoloading van de ScheduledJob-module verwijderen bij het gebruik van taak-cmdlets (#11194)</span><span class="sxs-lookup"><span data-stu-id="36e9d-292">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="36e9d-293">Output type toevoegen aan de cmdlet Get-error en de oorspronkelijke TypeName (#10856) behouden</span><span class="sxs-lookup"><span data-stu-id="36e9d-293">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="36e9d-294">Herstel de null-verwijzing in de eigenschap SupportsVirtualTerminal (#11105)</span><span class="sxs-lookup"><span data-stu-id="36e9d-294">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="36e9d-295">Limiet controle toevoegen in Get-Wine vent (#10648) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-295">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-296">Opdracht runtime corrigeren zodat StopUpstreamCommandsException niet wordt gevuld in-ErrorVariable (#10840)</span><span class="sxs-lookup"><span data-stu-id="36e9d-296">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="36e9d-297">Stel de uitvoer codering in op [console]:: OutputEncoding for native commands (#10824)</span><span class="sxs-lookup"><span data-stu-id="36e9d-297">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="36e9d-298">Ondersteuning voor code blokken met meerdere regels in voor beelden (#10776) (bedankt @Greg-Smulko !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-298">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="36e9d-299">Para meter Culture toevoegen aan de Select-string-cmdlet (#10943) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-299">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-300">Pad naar de werkmap van de start taak oplossen met een afsluitende back slash (#11041)</span><span class="sxs-lookup"><span data-stu-id="36e9d-300">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="36e9d-301">ConvertFrom-JSON: verzamelingen standaard uitpakken (#10861) (bedankt @danstur !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-301">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="36e9d-302">Gebruik een hoofdletter gevoelige hashtabel voor de cmdlet Group-object met-CaseSensitive en-AsHashtable switches (#11030) (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-302">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="36e9d-303">Uitzonde ring afhandelen wanneer het opsommen van bestanden mislukt bij het opnieuw opbouwen van het pad naar de juiste behuizing (#11014)</span><span class="sxs-lookup"><span data-stu-id="36e9d-303">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="36e9d-304">Herstel ConciseView om activiteit weer te geven in plaats van myCommand (#11007)</span><span class="sxs-lookup"><span data-stu-id="36e9d-304">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="36e9d-305">Web-cmdlets toestaan om HTTP-fout statussen te negeren (#10466) (bedankt @vdamewood !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-305">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="36e9d-306">De installatie van meer dan één CommandInfo op Get-opdracht (#10929) herstellen</span><span class="sxs-lookup"><span data-stu-id="36e9d-306">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="36e9d-307">De cmdlet Get-Counter voor Windows (#10933) toevoegen</span><span class="sxs-lookup"><span data-stu-id="36e9d-307">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="36e9d-308">Maak ConvertTo-JSON behandel [AutomationNull]:: waarde en [NullString]:: waarde als $null (#10957)</span><span class="sxs-lookup"><span data-stu-id="36e9d-308">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="36e9d-309">Haken verwijderen van IPv6-adres voor externe SSHing (#10968)</span><span class="sxs-lookup"><span data-stu-id="36e9d-309">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="36e9d-310">Een crash herstellen als de opdracht die wordt verzonden naar pwsh, alleen witruimte is (#10977)</span><span class="sxs-lookup"><span data-stu-id="36e9d-310">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="36e9d-311">Meerdere platforms Get-Klembord en set-klem bord (#10340) toegevoegd</span><span class="sxs-lookup"><span data-stu-id="36e9d-311">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="36e9d-312">De instelling van het oorspronkelijke pad van het bestandssysteem object herstellen zonder extra afsluitende slash (#10959)</span><span class="sxs-lookup"><span data-stu-id="36e9d-312">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="36e9d-313">Ondersteunings $null voor ConvertTo-JSON (#10947)</span><span class="sxs-lookup"><span data-stu-id="36e9d-313">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="36e9d-314">Opdracht voor uitgaand-printer toevoegen in Windows (#10906)</span><span class="sxs-lookup"><span data-stu-id="36e9d-314">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="36e9d-315">Start-job-variabele workingdirectory oplossen met witruimte (#10951)</span><span class="sxs-lookup"><span data-stu-id="36e9d-315">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="36e9d-316">De standaard waarde Retour neren bij het ophalen van Null voor een instelling in PSConfiguration.cs (#10963) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-316">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-317">I/o-uitzonde ring afhandelen als niet-beëindigd (#10950)</span><span class="sxs-lookup"><span data-stu-id="36e9d-317">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="36e9d-318">Voeg de GraphicalHost-assembly toe voor het inschakelen van out-GridView, show-Command en Get-Help-ShowWindow (#10899)</span><span class="sxs-lookup"><span data-stu-id="36e9d-318">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="36e9d-319">Computer naam nemen via pijp lijn in Get-HotFix (#10852) (bedankt @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-319">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="36e9d-320">De aanvulling van het tabblad voor para meters herstellen, zodat de algemene para meters als beschikbaar worden weer gegeven (#10850)</span><span class="sxs-lookup"><span data-stu-id="36e9d-320">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="36e9d-321">Herstel GetCorrectCasedPath () om eerst te controleren of er systeem bestands vermeldingen worden geretourneerd voordat de eerste () (#10930) wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="36e9d-321">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="36e9d-322">Werkmap instellen op huidige map in start-Job (#10920) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-322">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-323">Wijzig TabExpansion2 in niet vereist-CursorColumn en behandel als $InputScript. length (#10849)</span><span class="sxs-lookup"><span data-stu-id="36e9d-323">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="36e9d-324">Case afhandelen waarbij host geen rijen of kolommen van het scherm mag retour neren (#10938)</span><span class="sxs-lookup"><span data-stu-id="36e9d-324">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="36e9d-325">Het gebruik van accent kleuren herstellen voor hosts die deze niet ondersteunen (#10937)</span><span class="sxs-lookup"><span data-stu-id="36e9d-325">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="36e9d-326">Een update toevoegen-lijst opdracht (#10922)</span><span class="sxs-lookup"><span data-stu-id="36e9d-326">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="36e9d-327">FWLink-id bijwerken voor Clear-RecycleBin (#10925)</span><span class="sxs-lookup"><span data-stu-id="36e9d-327">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="36e9d-328">Bij het volt ooien van het tabblad bestand overs Laan als bestands kenmerken niet kunnen worden gelezen (#10910)</span><span class="sxs-lookup"><span data-stu-id="36e9d-328">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="36e9d-329">Clear-RecycleBin voor Windows toevoegen (#10909)</span><span class="sxs-lookup"><span data-stu-id="36e9d-329">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="36e9d-330">Voeg toe `$env:__SuppressAnsiEscapeSequences` om te bepalen of er een escape-teken reeks moet worden uitgevoerd (#10814)</span><span class="sxs-lookup"><span data-stu-id="36e9d-330">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="36e9d-331">De para meter add-all voor het inkleuren van de Select-string uitvoer (#8963) (bedankt @derek-xia !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-331">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="36e9d-332">De cmdlet Get-HotFix (#10740) toevoegen</span><span class="sxs-lookup"><span data-stu-id="36e9d-332">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="36e9d-333">Het toevoegen van het type bruikbaar maken in toepassingen die als host optreden voor Power shell (#10587)</span><span class="sxs-lookup"><span data-stu-id="36e9d-333">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="36e9d-334">Gebruik een effectievere evaluatie volgorde in LanguagePrimitives. IsNullLike () (#10781) (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-334">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="36e9d-335">De verwerking van gepipede invoer van gemengde verzamelingen en gestreamde stromen van invoer in Format-hex (#8674) verbeteren (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-335">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="36e9d-336">Gebruik type Conversion in SSHConnection hashtabellen wanneer de waarde niet overeenkomt met het verwachte type (#10720) (bedankt @SeeminglyScience !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-336">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="36e9d-337">Herstel Get-content-ReadCount 0 Behavior wanneer-TotalCount is ingesteld (#10749) (bedankt @eugenesmlv !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-337">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="36e9d-338">Fout bericht over het geweigerde toegang van het object in Get-Wine vent (#10639) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-338">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-339">Het inschakelen van het tabblad voor de toewijzing van een variabele met Enum of type beperkt (#10646)</span><span class="sxs-lookup"><span data-stu-id="36e9d-339">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="36e9d-340">Ongebruikte eigenschap SourceLength Remoting verwijderen waardoor opmaak problemen ontstaan (#10765)</span><span class="sxs-lookup"><span data-stu-id="36e9d-340">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="36e9d-341">De para meter add-scheidings teken voor ConvertFrom-StringData (#10665) (bedankt @steviecoaster !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-341">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="36e9d-342">Positionele para meter voor script Block toevoegen bij het gebruik van invoke-opdracht met SSH (#10721) (bedankt @machgo !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-342">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="36e9d-343">Regel context gegevens weer geven als er meerdere regels maar geen script naam voor ConciseView (#10746)</span><span class="sxs-lookup"><span data-stu-id="36e9d-343">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="36e9d-344">Voeg ondersteuning voor \\ WSL $ \-paden toe aan de File System Provider (#10674)</span><span class="sxs-lookup"><span data-stu-id="36e9d-344">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="36e9d-345">Voeg de ontbrekende token tekst toe voor TokenKind. QuestionMark in parser (#10706)</span><span class="sxs-lookup"><span data-stu-id="36e9d-345">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="36e9d-346">Stel de huidige werkmap van elk ForEach-object-parallel uitgevoerd script in op dezelfde locatie als het aanroepende script.</span><span class="sxs-lookup"><span data-stu-id="36e9d-346">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="36e9d-347">(#10672)</span><span class="sxs-lookup"><span data-stu-id="36e9d-347">(#10672)</span></span>
- <span data-ttu-id="36e9d-348">Vervang api-ms-win-core-file-l1-2-2.dll door Kernell32.dll voor FindFirstStreamW-en FindNextStreamW-Api's (#10680) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-348">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-349">Tweak Help opmaak script om StrictMode tolerant te maken (#10563)</span><span class="sxs-lookup"><span data-stu-id="36e9d-349">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="36e9d-350">De para meter SecurityDescriptorSDDL toevoegen aan New-Service (#10483) (bedankt @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-350">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="36e9d-351">Informatieve uitvoer verwijderen, het gebruik van ping in Test-Connection consolideren (#10478) (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-351">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="36e9d-352">Speciale reparsepunten lezen zonder ze te openen (#10662) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-352">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-353">Direct uitgeschakelde uitvoer van de host naar Terminal (#10681) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-353">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-354">Opnieuw een nieuwe regel toevoegen met de indeling-Table en-Property (#10653)</span><span class="sxs-lookup"><span data-stu-id="36e9d-354">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="36e9d-355">Verwijder [ValidateNotNullOrEmpty] uit-input object op Get-Random om lege teken reeks toe te staan (#10644)</span><span class="sxs-lookup"><span data-stu-id="36e9d-355">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="36e9d-356">Niet-hoofdletter gevoelig (#10549) voor suggestie systeem teken reeks @iSazonov</span><span class="sxs-lookup"><span data-stu-id="36e9d-356">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-357">Uitzonde ring voor Null-verwijzingen herstellen in ForEach-Object-parallelle invoer verwerking (#10577)</span><span class="sxs-lookup"><span data-stu-id="36e9d-357">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="36e9d-358">Definities van Power shell core-groeps beleid toevoegen (#10468)</span><span class="sxs-lookup"><span data-stu-id="36e9d-358">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="36e9d-359">Update de console-host ter ondersteuning van XTPUSHSGR/XTPOPSGR VT-controle reeksen die worden gebruikt in scenario's voor het opstellen van een scenario.</span><span class="sxs-lookup"><span data-stu-id="36e9d-359">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="36e9d-360">(#10208)</span><span class="sxs-lookup"><span data-stu-id="36e9d-360">(#10208)</span></span>
- <span data-ttu-id="36e9d-361">De para meter variabele workingdirectory toevoegen aan de start-Job (#10324) (bedankt @davinci26 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-361">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="36e9d-362">Verwijder de gebeurtenis-handler waardoor wijzigingen in onderbrekings punten onjuist worden gerepliceerd naar de host runs Pace Debugger (#10503) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-362">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="36e9d-363">Vervang api-ms-win-core-job-12-1-0.dll door Kernell32.dll in micro soft. Power shell. commands. NativeMethods P/Invoke API (#10417) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-363">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-364">De verkeerde uitvoer voor een nieuwe service in een variabele toewijzing en-outvariabele (#10444) oplossen (bedankt @kvprasoon !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-364">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="36e9d-365">Algemene problemen met het hulp programma oplossen rond de afsluit code, opdracht regel parameters en pad met spaties (#10461)</span><span class="sxs-lookup"><span data-stu-id="36e9d-365">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="36e9d-366">Herstel recursie in OneDrive-Change FindFirstFileEx () voor het gebruik van SafeFindHandle type (#10405)</span><span class="sxs-lookup"><span data-stu-id="36e9d-366">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="36e9d-367">Het automatisch laden van PSReadLine in Windows overs Laan als de scherm lezer NVDA actief is (#10385)</span><span class="sxs-lookup"><span data-stu-id="36e9d-367">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="36e9d-368">Verg root de ingebouwde module versie van Power shell naar 7.0.0.0 (#10356)</span><span class="sxs-lookup"><span data-stu-id="36e9d-368">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="36e9d-369">Er is een fout opgetreden in de invoeg toepassing als er al een type met dezelfde naam bestaat (#9609) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-369">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="36e9d-370">Prestaties</span><span class="sxs-lookup"><span data-stu-id="36e9d-370">Performance</span></span>

- <span data-ttu-id="36e9d-371">Vermijd het gebruik van closure in parser. saving (#11006)</span><span class="sxs-lookup"><span data-stu-id="36e9d-371">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="36e9d-372">De cache verbeteren bij het maken van nieuwe regex-instanties (#10657) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-372">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-373">De verwerking van het ingebouwde Power shell-type gegevens van types.ps1XML, typesV3.ps1XML en GetEvent.types.ps1XML (#10898) verbeteren</span><span class="sxs-lookup"><span data-stu-id="36e9d-373">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="36e9d-374">Werk PSConfiguration. ReadValueFromFile bij om het sneller en meer geheugen efficiënt te maken (#10839)</span><span class="sxs-lookup"><span data-stu-id="36e9d-374">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="36e9d-375">Voeg kleine prestatie verbeteringen toe voor runs Pace-initialisatie (#10569) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-375">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-376">Maak ForEach-object sneller voor de meestgebruikte scenario's (#10454) en los het probleem van ForEach-object-parallel op met veel runspaces (#10455)</span><span class="sxs-lookup"><span data-stu-id="36e9d-376">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="36e9d-377">Code opschonen</span><span class="sxs-lookup"><span data-stu-id="36e9d-377">Code Cleanup</span></span>

- <span data-ttu-id="36e9d-378">Tekst van opmerking en element wijzigen om te voldoen aan de micro soft-normen (#11304)</span><span class="sxs-lookup"><span data-stu-id="36e9d-378">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="36e9d-379">Problemen met opschonings stijl in Compiler.cs (#10368) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-379">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-380">Verwijder het niet-gebruikte type Converter voor CommaDelimitedStringCollection (#11000) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-380">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-381">Stijl opschonen in InitialSessionState.cs (#10865) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-381">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-382">Code opschonen voor PSSession-klasse (#11001)</span><span class="sxs-lookup"><span data-stu-id="36e9d-382">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="36e9d-383">Verwijder de niet-werkende update uitvoeren-Help van Get-Help wanneer Get-Help wordt uitgevoerd voor de eerste functie (#10974)</span><span class="sxs-lookup"><span data-stu-id="36e9d-383">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="36e9d-384">Stijl problemen oplossen (#10998) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-384">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-385">Opschonen: gebruik de ingebouwde alias (#10882) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-385">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-386">Verwijder de ongebruikte instelling sleutel ConsolePrompting en Vermijd overbodige teken reeks maken bij het uitvoeren van een query naar de ExecutionPolicy-instelling (#10985)</span><span class="sxs-lookup"><span data-stu-id="36e9d-386">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="36e9d-387">Update meldings controle uitschakelen voor dagelijkse builds (#10903) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-387">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="36e9d-388">Het herstellen van de API voor fout opsporing in #10338 is verloren gegaan (#10808)</span><span class="sxs-lookup"><span data-stu-id="36e9d-388">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="36e9d-389">Verwijder de WorkflowJobSourceAdapter-verwijzing die niet meer wordt gebruikt (#10326) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-389">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="36e9d-390">De COM-interfaces in Jump List code opschonen door de PreserveSig-kenmerken (#9899) te corrigeren (bedankt @weltkante !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-390">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="36e9d-391">Voeg een opmerking toe waarin wordt beschreven waarom-IA niet de alias voor de algemene para meter-Information Action (#10703) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-391">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="36e9d-392">Wijzig de naam van InvokeCommandCmdlet.cs in InvokeExpressionCommand.cs (#10659) (bedankt @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-392">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="36e9d-393">Secundaire code-opschoningen gerelateerd aan update meldingen toevoegen (#10698)</span><span class="sxs-lookup"><span data-stu-id="36e9d-393">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="36e9d-394">Afgeschafte werk stroom logica verwijderen uit de scripts voor externe installatie (#10320) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-394">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="36e9d-395">Help-indeling bijwerken voor het gebruik van de juiste case (#10678) (bedankt @tnieto88 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-395">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="36e9d-396">Opschonen van CodeFactor stijl problemen die in de afgelopen maand worden doorgevoerd (#10591) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-396">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-397">Een type fout in beschrijving van de PSTernaryOperator experimentele functie (#10586) oplossen (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-397">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="36e9d-398">ActionPreference omzetten in een niet-ondersteunde, gereserveerde status en de beperking voor het gebruik van ActionPreference. ignore negeren in voorkeurs variabelen (#10317) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-398">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="36e9d-399">Vervang de array list with list \<T> om meer Lees bare en betrouw bare code te verkrijgen zonder de functionaliteit te wijzigen (#10333) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-399">Replace ArrayList with List\<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-400">Code stijl oplossingen maken voor TestConnectionCommand (#10439) (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-400">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="36e9d-401">AutomationEngine opschonen en extra SetSessionStateDrive-methode aanroep (#10416) verwijderen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-401">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-402">Wijzig de naam van de standaard ParameterSetName weer in scheidings teken voor ConvertTo-CSV en ConvertFrom-CSV (#10425)</span><span class="sxs-lookup"><span data-stu-id="36e9d-402">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="36e9d-403">Hulpprogramma's</span><span class="sxs-lookup"><span data-stu-id="36e9d-403">Tools</span></span>

- <span data-ttu-id="36e9d-404">Voeg de standaard instelling voor de eigenschap SDKToUse toe zodat deze wordt gebouwd in VS (#11085)</span><span class="sxs-lookup"><span data-stu-id="36e9d-404">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="36e9d-405">Install-Powershell.ps1: para meter toevoegen voor het gebruik van MSI-installatie (#10921) (bedankt @MJECloud !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-405">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="36e9d-406">Eenvoudige voor beelden voor install-powershell.ps1 (#10914) toevoegen (bedankt @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-406">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="36e9d-407">Een lege teken reeks in de PowerShellHome-para meter (#10526) laten verwerken Install-PowerShellRemoting.ps1 (hartelijk dank @Orca88 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-407">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="36e9d-408">Schakel over van/etc/lsb-release naar/etc/OS-release in install-powershell.sh #10773 (bedankt @Himura2la !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-408">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="36e9d-409">Controleer pwsh.exe en pwsh in een dagelijkse versie op Windows (#10738) (bedankt @centreboard !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-409">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="36e9d-410">Verwijder overbodige tikken in installpsh-osx.sh (#10752)</span><span class="sxs-lookup"><span data-stu-id="36e9d-410">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="36e9d-411">install-powershell.ps1 bijwerken om te controleren op reeds geïnstalleerde dagelijkse build (#10489)</span><span class="sxs-lookup"><span data-stu-id="36e9d-411">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="36e9d-412">Testen</span><span class="sxs-lookup"><span data-stu-id="36e9d-412">Tests</span></span>

- <span data-ttu-id="36e9d-413">Onbetrouwbare DSC-test maken in behandeling (#11131)</span><span class="sxs-lookup"><span data-stu-id="36e9d-413">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="36e9d-414">Herstel de stringdata-test om sleutels van hashtabellen correct te valideren (#10810)</span><span class="sxs-lookup"><span data-stu-id="36e9d-414">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="36e9d-415">Test modules verwijderen (#11061) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-415">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-416">De tijd verlengen tussen nieuwe pogingen om de test-URL te testen (#11015)</span><span class="sxs-lookup"><span data-stu-id="36e9d-416">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="36e9d-417">Update tests om test acties nauw keurig te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="36e9d-417">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="36e9d-418">(#10928) (Bedankt @romero126 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-418">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="36e9d-419">De Flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827) tijdelijk overs Laan</span><span class="sxs-lookup"><span data-stu-id="36e9d-419">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="36e9d-420">De test van de gebeurtenis-handler stabiel maken (#10790)</span><span class="sxs-lookup"><span data-stu-id="36e9d-420">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="36e9d-421">Synchronisatie van kapitalisatie in CI YAML (#10767) (bedankt @RDIL !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-421">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="36e9d-422">Test toevoegen voor het oplossen van de gebeurtenis-handler (#10768)</span><span class="sxs-lookup"><span data-stu-id="36e9d-422">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="36e9d-423">Get-Child item-test (#10507) toevoegen (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-423">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-424">Vervang niet-eenduidige taal voor tests van overschakelen naar para meter voor nauw keurigheid (#10666) (bedankt @romero126 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-424">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="36e9d-425">Experimentele controle toevoegen aan ForEach-Object-parallelle tests (#10354) (bedankt @KirkMunro !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-425">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="36e9d-426">Tests voor alpiene validatie bijwerken (#10428)</span><span class="sxs-lookup"><span data-stu-id="36e9d-426">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="36e9d-427">Verbeteringen op het gebied van build en package</span><span class="sxs-lookup"><span data-stu-id="36e9d-427">Build and Package Improvements</span></span>

- <span data-ttu-id="36e9d-428">Nuget pakket ondertekening voor gecoördineerde pakket build (#11316) oplossen</span><span class="sxs-lookup"><span data-stu-id="36e9d-428">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="36e9d-429">Afhankelijkheden van PowerShell Gallery en NuGet (#11323) bijwerken</span><span class="sxs-lookup"><span data-stu-id="36e9d-429">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="36e9d-430">Duw micro soft. ApplicationInsights van 2.11.0 naar 2.12.0 (#11305)</span><span class="sxs-lookup"><span data-stu-id="36e9d-430">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="36e9d-431">Duw micro soft. CodeAnalysis. CSharp van 3.3.1 naar 3.4.0 (#11265)</span><span class="sxs-lookup"><span data-stu-id="36e9d-431">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="36e9d-432">Update pakketten voor Debian 10 en 11 (#11236)</span><span class="sxs-lookup"><span data-stu-id="36e9d-432">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="36e9d-433">Schakel alleen experimentele functies in vóór RC (#11162)</span><span class="sxs-lookup"><span data-stu-id="36e9d-433">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="36e9d-434">Minimum versie van macOS bijwerken (#11163)</span><span class="sxs-lookup"><span data-stu-id="36e9d-434">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="36e9d-435">Duw NJsonSchema van 10.0.27 naar 10.0.28 (#11170)</span><span class="sxs-lookup"><span data-stu-id="36e9d-435">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="36e9d-436">Koppelingen in README.md en metadata.jsworden bijgewerkt op voor beeld. 5 (#10854)</span><span class="sxs-lookup"><span data-stu-id="36e9d-436">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="36e9d-437">Selecteer de bestanden voor nalevings tests die eigendom zijn van Power shell (#10837)</span><span class="sxs-lookup"><span data-stu-id="36e9d-437">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="36e9d-438">Win7x86 msix-pakket mag worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="36e9d-438">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="36e9d-439">(Interne 10515)</span><span class="sxs-lookup"><span data-stu-id="36e9d-439">(Internal 10515)</span></span>
- <span data-ttu-id="36e9d-440">Toestaan dat semantische versies worden door gegeven aan de functie NormalizeVersion (#11087)</span><span class="sxs-lookup"><span data-stu-id="36e9d-440">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="36e9d-441">.NET core Framework omlaag dalen tot 3,1-Preview. 3 (#11079)</span><span class="sxs-lookup"><span data-stu-id="36e9d-441">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="36e9d-442">Duw PSReadLine van 2.0.0-beta5 naar 2.0.0-beta6 in/src/Modules (#11078)</span><span class="sxs-lookup"><span data-stu-id="36e9d-442">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="36e9d-443">Duw Newtonsoft.Jsop van 12.0.2 naar 12.0.3 (#11037) (#11038)</span><span class="sxs-lookup"><span data-stu-id="36e9d-443">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="36e9d-444">Debian-pakketten van 10, 11 en CentOS 8 toevoegen (#11028)</span><span class="sxs-lookup"><span data-stu-id="36e9d-444">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="36e9d-445">Het JSON-bestand voor Build-info uploaden met het veld ReleaseDate (#10986)</span><span class="sxs-lookup"><span data-stu-id="36e9d-445">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="36e9d-446">.NET core Framework omlaag dalen tot 3,1-Preview. 2 (#10993)</span><span class="sxs-lookup"><span data-stu-id="36e9d-446">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="36e9d-447">Build van het x86 MSIX-pakket (#10934) inschakelen</span><span class="sxs-lookup"><span data-stu-id="36e9d-447">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="36e9d-448">De URL van de DotNet SDK-installatie script bijwerken in build. psm1 (#10927)</span><span class="sxs-lookup"><span data-stu-id="36e9d-448">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="36e9d-449">Duw Markdig. ondertekend van 0.17.1 naar 0.18.0 (#10887)</span><span class="sxs-lookup"><span data-stu-id="36e9d-449">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="36e9d-450">Duw ThreadJob van 2.0.1 naar 2.0.2 (#10886)</span><span class="sxs-lookup"><span data-stu-id="36e9d-450">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="36e9d-451">AppX-manifest en verpakkings module bijwerken om te voldoen aan de vereisten voor MS Store (#10878)</span><span class="sxs-lookup"><span data-stu-id="36e9d-451">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="36e9d-452">Pakket verwijzing voor Power shell SDK bijwerken naar preview. 5 (interne 10295)</span><span class="sxs-lookup"><span data-stu-id="36e9d-452">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="36e9d-453">ThirdPartyNotices.txt bijwerken (#10834)</span><span class="sxs-lookup"><span data-stu-id="36e9d-453">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="36e9d-454">Duw micro soft. Power shell. native naar 7.0.0-Preview. 3 (#10826)</span><span class="sxs-lookup"><span data-stu-id="36e9d-454">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="36e9d-455">Duw micro soft. ApplicationInsights van 2.10.0 naar 2.11.0 (#10608)</span><span class="sxs-lookup"><span data-stu-id="36e9d-455">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="36e9d-456">Duw NJsonSchema van 10.0.24 naar 10.0.27 (#10756)</span><span class="sxs-lookup"><span data-stu-id="36e9d-456">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="36e9d-457">MacPorts-ondersteuning toevoegen aan het build-systeem (#10736) (bedankt @Lucius-Q-User !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-457">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="36e9d-458">Duw package management van 1.4.4 naar 1.4.5 (#10728)</span><span class="sxs-lookup"><span data-stu-id="36e9d-458">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="36e9d-459">Duw NJsonSchema van 10.0.23 naar 10.0.24 (#10635)</span><span class="sxs-lookup"><span data-stu-id="36e9d-459">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="36e9d-460">Omgevings variabele toevoegen om onderscheid te maken tussen client/server-telemetrie in MSI (#10612)</span><span class="sxs-lookup"><span data-stu-id="36e9d-460">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="36e9d-461">Duw PSDesiredStateConfiguration van 2.0.3 naar 2.0.4 (#10603)</span><span class="sxs-lookup"><span data-stu-id="36e9d-461">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="36e9d-462">Duw micro soft. CodeAnalysis. CSharp van 3.2.1 naar 3.3.1 (#10607)</span><span class="sxs-lookup"><span data-stu-id="36e9d-462">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="36e9d-463">Bijwerken naar .net Core 3,0 RTM (#10604) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-463">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="36e9d-464">MSIX-verpakking bijwerken zodat de versie van Windows Store-vereisten (#10588)</span><span class="sxs-lookup"><span data-stu-id="36e9d-464">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="36e9d-465">PowerShellGet-versie van 2,2 naar 2.2.1 (#10382)</span><span class="sxs-lookup"><span data-stu-id="36e9d-465">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="36e9d-466">Package Management-versie van 1.4.3 naar 1.4.4 (#10383)</span><span class="sxs-lookup"><span data-stu-id="36e9d-466">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="36e9d-467">README.md en metadata.jsbijwerken op voor 7.0.0-Preview. 4 (interne 10011)</span><span class="sxs-lookup"><span data-stu-id="36e9d-467">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="36e9d-468">Voer een upgrade uit van de .net Core 3,0-versie van preview 9 naar RC1 (#10552) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-468">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="36e9d-469">Genereren van ExperimentalFeature-lijst oplossen (intern 9996)</span><span class="sxs-lookup"><span data-stu-id="36e9d-469">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="36e9d-470">Duw PSReadLine-versie van 2.0.0-beta4 naar 2.0.0-beta5 (#10536)</span><span class="sxs-lookup"><span data-stu-id="36e9d-470">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="36e9d-471">Release build-script voor het instellen van release tag herstellen</span><span class="sxs-lookup"><span data-stu-id="36e9d-471">Fix release build script to set release tag</span></span>
- <span data-ttu-id="36e9d-472">Update versie van micro soft. Power shell. native to 7.0.0-Preview. 2 (#10519)</span><span class="sxs-lookup"><span data-stu-id="36e9d-472">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="36e9d-473">Voer een upgrade uit naar Netcoreapp 3.0 preview9 (#10484) (bedankt @bergmeister !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-473">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="36e9d-474">Zorg ervoor dat de dagelijkse samen stelling kent, weet u zeker dat het een dagelijkse build is (#10464)</span><span class="sxs-lookup"><span data-stu-id="36e9d-474">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="36e9d-475">Werk de gecombineerde pakket versie bij om de dagelijkse builds op te heffen (#10449)</span><span class="sxs-lookup"><span data-stu-id="36e9d-475">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="36e9d-476">Appveyor-verwijzing verwijderen (#10445) (bedankt @RDIL !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-476">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="36e9d-477">NJsonSchema-versie van 10.0.22 naar 10.0.23 (#10421)</span><span class="sxs-lookup"><span data-stu-id="36e9d-477">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="36e9d-478">Verwijder het verwijderen van de map Linux-x64 build omdat sommige afhankelijkheden voor Alpine zijn vereist (#10407)</span><span class="sxs-lookup"><span data-stu-id="36e9d-478">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="36e9d-479">Documentatie en Help-inhoud</span><span class="sxs-lookup"><span data-stu-id="36e9d-479">Documentation and Help Content</span></span>

- <span data-ttu-id="36e9d-480">Wijzigings logboeken voor refeiten in één logboek per release (#11165)</span><span class="sxs-lookup"><span data-stu-id="36e9d-480">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="36e9d-481">FWLinks voor Power shell 7 online-Help-documenten (#11071) herstellen</span><span class="sxs-lookup"><span data-stu-id="36e9d-481">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="36e9d-482">Update CONTRIBUTING.md (#11096) (bedankt @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-482">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="36e9d-483">Koppelingen voor installatie doc herstellen in README.md (#11083)</span><span class="sxs-lookup"><span data-stu-id="36e9d-483">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="36e9d-484">Voor beelden toevoegen aan install-powershell.ps1 script (#11024) (bedankt @kilasuit !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-484">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="36e9d-485">Fix to select-string nadruk en import-Dscresource bieden in CHANGELOG.md (#10890)</span><span class="sxs-lookup"><span data-stu-id="36e9d-485">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="36e9d-486">De verouderde koppeling verwijderen van powershell-beginners-guide.md (#10926)</span><span class="sxs-lookup"><span data-stu-id="36e9d-486">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="36e9d-487">Stabiele en onderhouds logboeken voor wijzigingen samen voegen (#10527)</span><span class="sxs-lookup"><span data-stu-id="36e9d-487">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="36e9d-488">Gebruikte .NET-versie in Build docs (#10775) bijwerken (bedankt @Greg-Smulko !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-488">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="36e9d-489">Vervang links van MSDN naar docs.microsoft.com in powershell-beginners-guide.md (#10778) (bedankt @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-489">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="36e9d-490">Defecte koppeling voor DSC-overzicht oplossen (#10702)</span><span class="sxs-lookup"><span data-stu-id="36e9d-490">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="36e9d-491">Support_Question. MD bijwerken om een koppeling te maken naar Stack Overflow als een andere Community-Resource (#10638) (bedankt @mklement0 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-491">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="36e9d-492">De processor architectuur toevoegen aan de sjabloon voor de distributie aanvraag (#10661)</span><span class="sxs-lookup"><span data-stu-id="36e9d-492">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="36e9d-493">Nieuw Power shell MoL Book toevoegen om Power shell-documenten te leren (#10602)</span><span class="sxs-lookup"><span data-stu-id="36e9d-493">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="36e9d-494">README.md en meta gegevens bijwerken voor v 6.1.6-en v 6.2.3-releases (#10523)</span><span class="sxs-lookup"><span data-stu-id="36e9d-494">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="36e9d-495">Een type fout in README.md (#10465) oplossen (bedankt @vedhasp !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-495">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="36e9d-496">Voeg een verwijzing naar de PSKoans-module toe aan de documentatie voor Learning resources (#10369) (bedankt @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="36e9d-496">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="36e9d-497">README.md en metadata.jsbijwerken op voor 7.0.0-Preview. 3 (#10393)</span><span class="sxs-lookup"><span data-stu-id="36e9d-497">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
