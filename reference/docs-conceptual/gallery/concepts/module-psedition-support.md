---
ms.date: 06/10/2020
title: Modules met compatibele Power shell-edities
description: In dit artikel wordt uitgelegd hoe de PowerShellGet-cmdlets het bureau blad en de kern edities van Power shell-modules ondersteunen.
ms.openlocfilehash: 530101590cf83a1f43cbb9ce32d07a7e0ec79253
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661488"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="09e44-103">Modules met compatibele Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="09e44-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="09e44-104">Vanaf versie 5,1 is Power shell beschikbaar in verschillende edities, waarbij verschillende functie sets en platform compatibiliteit worden aangegeven.</span><span class="sxs-lookup"><span data-stu-id="09e44-104">Starting with version 5.1, PowerShell is available in different editions, which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="09e44-105">**Desktop Edition:** Gebaseerd op .NET Framework, is van toepassing op Windows Power shell v 4.0 en hieronder, evenals Windows Power shell 5,1 op Windows Desktop, Windows Server, Windows Server Core en de meeste andere Windows-edities.</span><span class="sxs-lookup"><span data-stu-id="09e44-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="09e44-106">**Core-editie:** Gebaseerd op .NET core, is van toepassing op Power shell Core 6,0 en hoger, evenals Windows Power shell 5,1 op Windows-edities met verminderde footprint, zoals Windows IoT en Windows nano server.</span><span class="sxs-lookup"><span data-stu-id="09e44-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="09e44-107">Zie [about_PowerShell_Editions][]voor meer informatie over Power shell-edities.</span><span class="sxs-lookup"><span data-stu-id="09e44-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="09e44-108">Compatibele edities declareren</span><span class="sxs-lookup"><span data-stu-id="09e44-108">Declaring compatible editions</span></span>

<span data-ttu-id="09e44-109">Module auteurs kunnen hun modules declareren om compatibel te zijn met een of meer Power shell-edities met behulp van de `CompatiblePSEditions` manifest sleutel van de module.</span><span class="sxs-lookup"><span data-stu-id="09e44-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the `CompatiblePSEditions` module manifest key.</span></span> <span data-ttu-id="09e44-110">Deze sleutel wordt alleen ondersteund in PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="09e44-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="09e44-111">Zodra een module manifest is opgegeven met de `CompatiblePSEditions` sleutel of gebruikmaakt `$PSEdition` van de variabele, kan het niet worden geïmporteerd in Power shell v4 of lager.</span><span class="sxs-lookup"><span data-stu-id="09e44-111">Once a module manifest is specified with the `CompatiblePSEditions` key or uses the `$PSEdition` variable, it can not be imported on PowerShell v4 or lower.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="09e44-112">Bij het ophalen van een lijst met beschikbare modules kunt u de lijst filteren op PowerShell-editie.</span><span class="sxs-lookup"><span data-stu-id="09e44-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules

ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

<span data-ttu-id="09e44-113">Vanaf Power shell 6 wordt de `CompatiblePSEditions` waarde gebruikt om te bepalen of een module compatibel is wanneer er modules worden geïmporteerd `$env:windir\System32\WindowsPowerShell\v1.0\Modules` .</span><span class="sxs-lookup"><span data-stu-id="09e44-113">Beginning in PowerShell 6, the `CompatiblePSEditions` value is used to decide if a module is compatible when modules are imported from `$env:windir\System32\WindowsPowerShell\v1.0\Modules`.</span></span>
<span data-ttu-id="09e44-114">Dit gedrag geldt alleen voor Windows.</span><span class="sxs-lookup"><span data-stu-id="09e44-114">This behavior only applies to Windows.</span></span> <span data-ttu-id="09e44-115">Buiten dit scenario wordt de waarde alleen gebruikt als meta gegevens.</span><span class="sxs-lookup"><span data-stu-id="09e44-115">Outside of this scenario, the value is only used as metadata.</span></span>

## <a name="finding-compatible-modules"></a><span data-ttu-id="09e44-116">Compatibele modules zoeken</span><span class="sxs-lookup"><span data-stu-id="09e44-116">Finding compatible modules</span></span>

<span data-ttu-id="09e44-117">PowerShell Gallery gebruikers kunnen de lijst met modules die worden ondersteund in een specifieke Power shell-editie vinden met behulp van labels **PSEdition_Desktop** en **PSEdition_Core** .</span><span class="sxs-lookup"><span data-stu-id="09e44-117">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags **PSEdition_Desktop** and **PSEdition_Core** .</span></span>

<span data-ttu-id="09e44-118">Modules zonder **PSEdition_Desktop** en **PSEdition_Core** -Tags worden beschouwd als goed op Power shell-Desktop-edities.</span><span class="sxs-lookup"><span data-stu-id="09e44-118">Modules without **PSEdition_Desktop** and **PSEdition_Core** tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="09e44-119">Meerdere edities richten</span><span class="sxs-lookup"><span data-stu-id="09e44-119">Targeting multiple editions</span></span>

<span data-ttu-id="09e44-120">Ontwerpers van modules kunnen één module richten op een of beide Power shell-edities (desktop en Core).</span><span class="sxs-lookup"><span data-stu-id="09e44-120">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="09e44-121">Eén module kan zowel op bureau blad-als op kern-edities worden uitgevoerd. in die module auteur moet de vereiste logica worden toegevoegd in RootModule of in het module manifest met behulp van een `$PSEdition` variabele.</span><span class="sxs-lookup"><span data-stu-id="09e44-121">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using `$PSEdition` variable.</span></span> <span data-ttu-id="09e44-122">Modules kunnen twee sets gecompileerde Dll's hebben die zijn gericht op zowel **CoreCLR** als **FullCLR** .</span><span class="sxs-lookup"><span data-stu-id="09e44-122">Modules can have two sets of compiled DLLs targeting both **CoreCLR** and **FullCLR** .</span></span> <span data-ttu-id="09e44-123">Hier vindt u de verpakkings opties met logica voor het laden van de juiste Dll's.</span><span class="sxs-lookup"><span data-stu-id="09e44-123">Here are the packaging options with logic for loading proper DLLs.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="09e44-124">Optie 1: een module verpakken voor het richten op meerdere versies en meerdere versies van Power shell</span><span class="sxs-lookup"><span data-stu-id="09e44-124">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="09e44-125">Inhoud van module map</span><span class="sxs-lookup"><span data-stu-id="09e44-125">Module folder contents</span></span>

- <span data-ttu-id="09e44-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="09e44-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="09e44-128">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="09e44-128">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="09e44-129">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="09e44-129">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="09e44-130">ScriptAnalyzer.format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="09e44-130">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="09e44-131">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="09e44-131">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="09e44-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="09e44-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="09e44-134">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="09e44-134">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="09e44-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="09e44-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="09e44-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="09e44-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="09e44-138">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="09e44-138">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="09e44-139">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="09e44-139">Settings\DSC.psd1</span></span>
- <span data-ttu-id="09e44-140">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="09e44-140">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="09e44-141">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="09e44-141">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="09e44-142">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="09e44-142">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="09e44-143">Inhoud van `PSScriptAnalyzer.psd1` bestand</span><span class="sxs-lookup"><span data-stu-id="09e44-143">Contents of `PSScriptAnalyzer.psd1` file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<span data-ttu-id="09e44-144">Onder Logic worden de vereiste assembly's geladen, afhankelijk van de huidige editie of versie.</span><span class="sxs-lookup"><span data-stu-id="09e44-144">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="09e44-145">Inhoud van het `PSScriptAnalyzer.psm1` bestand:</span><span class="sxs-lookup"><span data-stu-id="09e44-145">Contents of `PSScriptAnalyzer.psm1` file:</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a><span data-ttu-id="09e44-146">Optie 2: gebruik $PSEdition variabele in het PSD1-bestand om de juiste Dll's te laden</span><span class="sxs-lookup"><span data-stu-id="09e44-146">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs</span></span>

<span data-ttu-id="09e44-147">In PS 5,1 of hoger `$PSEdition` is globale variabele toegestaan in het manifest bestand van de module.</span><span class="sxs-lookup"><span data-stu-id="09e44-147">In PS 5.1 or newer, `$PSEdition` global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="09e44-148">Met deze variabele kan module Author de voorwaardelijke waarden opgeven in het manifest bestand van de module.</span><span class="sxs-lookup"><span data-stu-id="09e44-148">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="09e44-149">`$PSEdition` naar een variabele kan worden verwezen in de modus voor beperkte talen of in een gegevens gedeelte.</span><span class="sxs-lookup"><span data-stu-id="09e44-149">`$PSEdition` variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="09e44-150">Voor beeld van manifest bestand van module met `CompatiblePSEditions` sleutel.</span><span class="sxs-lookup"><span data-stu-id="09e44-150">Sample module manifest file with `CompatiblePSEditions` key.</span></span>

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

<span data-ttu-id="09e44-151">Inhoud van module</span><span class="sxs-lookup"><span data-stu-id="09e44-151">Module contents</span></span>

- <span data-ttu-id="09e44-152">ModuleWithEditions\ModuleWithEditions.psd1</span><span class="sxs-lookup"><span data-stu-id="09e44-152">ModuleWithEditions\ModuleWithEditions.psd1</span></span>
- <span data-ttu-id="09e44-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span></span>
- <span data-ttu-id="09e44-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span></span>
- <span data-ttu-id="09e44-155">ModuleWithEditions\clr\MyFullClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-155">ModuleWithEditions\clr\MyFullClrRM.dll</span></span>
- <span data-ttu-id="09e44-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span></span>
- <span data-ttu-id="09e44-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span></span>
- <span data-ttu-id="09e44-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="09e44-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span></span>

## <a name="more-details"></a><span data-ttu-id="09e44-159">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="09e44-159">More details</span></span>

[<span data-ttu-id="09e44-160">Scripts met PSEditions</span><span class="sxs-lookup"><span data-stu-id="09e44-160">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="09e44-161">PSEditions-ondersteuning op PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="09e44-161">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="09e44-162">Modulemanifest bijwerken</span><span class="sxs-lookup"><span data-stu-id="09e44-162">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="09e44-163">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="09e44-163">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
