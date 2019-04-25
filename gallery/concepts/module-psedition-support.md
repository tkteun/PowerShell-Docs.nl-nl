---
ms.date: 03/28/2019
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Modules met compatibele PowerShell-edities
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084722"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="942cf-103">Modules met compatibele PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="942cf-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="942cf-104">Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="942cf-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="942cf-105">**Desktop-editie:** Gebaseerd op .NET Framework, geldt voor Windows PowerShell v4.0 en hieronder en de Windows PowerShell 5.1 op Windows-bureaublad, Windows Server, Windows Server Core en de meeste andere edities van Windows.</span><span class="sxs-lookup"><span data-stu-id="942cf-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="942cf-106">**Core-editie:** Gebaseerd op .NET Core, is van toepassing op PowerShell Core 6.0 en hoger en Windows PowerShell 5.1 op verminderde footprint edities van Windows, zoals IoT voor Windows en Windows Nanoserver.</span><span class="sxs-lookup"><span data-stu-id="942cf-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="942cf-107">Zie voor meer informatie over PowerShell-edities [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="942cf-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="942cf-108">Compatibel edities declareren</span><span class="sxs-lookup"><span data-stu-id="942cf-108">Declaring compatible editions</span></span>

<span data-ttu-id="942cf-109">Auteurs van modules kunnen hun modules zo opstellen dat deze compatibel zijn met een of meer PowerShell-edities door de sleutel voor het modulemanifestbestand CompatiblePSEditions te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="942cf-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="942cf-110">Deze sleutel wordt alleen ondersteund in PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="942cf-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="942cf-111">Nadat een module-manifest is opgegeven met de sleutel CompatiblePSEditions, kan het niet worden geïmporteerd op de PowerShell-versie 4 en lager.</span><span class="sxs-lookup"><span data-stu-id="942cf-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

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

<span data-ttu-id="942cf-112">Bij het ophalen van een lijst met beschikbare modules kunt u de lijst filteren op PowerShell-editie.</span><span class="sxs-lookup"><span data-stu-id="942cf-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

## <a name="targeting-multiple-editions"></a><span data-ttu-id="942cf-113">Die gericht is op meerdere edities</span><span class="sxs-lookup"><span data-stu-id="942cf-113">Targeting multiple editions</span></span>

<span data-ttu-id="942cf-114">Auteurs kunnen publiceren een één module die gericht is op een van beide of beide PowerShell edities (Desktop en Core).</span><span class="sxs-lookup"><span data-stu-id="942cf-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="942cf-115">Een één-module kan worden gebruikt voor Desktop- en Core-edities, die de module auteur heeft om toe te voegen vereist logica in beide velden RootModule of in de module-manifest $PSEdition-variabele.</span><span class="sxs-lookup"><span data-stu-id="942cf-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="942cf-116">Modules kunnen twee sets gecompileerde dll-bestanden die gericht is op CoreCLR zowel FullCLR hebben.</span><span class="sxs-lookup"><span data-stu-id="942cf-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="942cf-117">Hier volgen de verschillende opties voor het verpakken van uw module met de logica voor het laden van de juiste DLL-bestanden.</span><span class="sxs-lookup"><span data-stu-id="942cf-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="942cf-118">Optie 1: Verpakking van een module die zijn gericht op meerdere versies en meerdere edities van PowerShell</span><span class="sxs-lookup"><span data-stu-id="942cf-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="942cf-119">De inhoud van de module-map</span><span class="sxs-lookup"><span data-stu-id="942cf-119">Module folder contents</span></span>

- <span data-ttu-id="942cf-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="942cf-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="942cf-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="942cf-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="942cf-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="942cf-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="942cf-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="942cf-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="942cf-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="942cf-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="942cf-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="942cf-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="942cf-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="942cf-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="942cf-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="942cf-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="942cf-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="942cf-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="942cf-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="942cf-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="942cf-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="942cf-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="942cf-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="942cf-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="942cf-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="942cf-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="942cf-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="942cf-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="942cf-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="942cf-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="942cf-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="942cf-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="942cf-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="942cf-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="942cf-137">Contents of PSScriptAnalyzer.psd1 file</span><span class="sxs-lookup"><span data-stu-id="942cf-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

<span data-ttu-id="942cf-138">Hieronder logische laadt de vereiste assembly's, afhankelijk van de huidige editie of versie.</span><span class="sxs-lookup"><span data-stu-id="942cf-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="942cf-139">De inhoud van PSScriptAnalyzer.psm1 bestand:</span><span class="sxs-lookup"><span data-stu-id="942cf-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="942cf-140">Optie 2: $PSEdition variabele in het PSD1-bestand gebruiken om de juiste DLL's en geneste/vereiste modules te laden</span><span class="sxs-lookup"><span data-stu-id="942cf-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="942cf-141">In PS 5.1 of hoger, wordt de globale variabele $PSEdition is toegestaan in het manifestbestand van de module.</span><span class="sxs-lookup"><span data-stu-id="942cf-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="942cf-142">Met deze variabele, opgeven module-auteur de voorwaardelijke waarden in het manifestbestand van de module.</span><span class="sxs-lookup"><span data-stu-id="942cf-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="942cf-143">$PSEdition variabele kan worden verwezen in de beperkte taalmodus of een gegevenssectie.</span><span class="sxs-lookup"><span data-stu-id="942cf-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="942cf-144">Nadat u een module-manifest is opgegeven met de sleutel CompatiblePSEditions of gebruikmaakt van `$PSEdition` variabele, het kan niet worden geïmporteerd op lagere versies van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="942cf-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="942cf-145">Voorbeeld-module-manifestbestand met CompatiblePSEditions sleutel</span><span class="sxs-lookup"><span data-stu-id="942cf-145">Sample module manifest file with CompatiblePSEditions key</span></span>

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

### <a name="module-contents"></a><span data-ttu-id="942cf-146">Module-inhoud</span><span class="sxs-lookup"><span data-stu-id="942cf-146">Module contents</span></span>

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

<span data-ttu-id="942cf-147">Gebruikers van de PowerShell Gallery vindt de lijst met modules die worden ondersteund op een specifieke editie van PowerShell met behulp van labels PSEdition_Desktop en PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="942cf-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="942cf-148">Modules zonder PSEdition_Desktop en PSEdition_Core tags worden beschouwd als goed werken op het bureaublad van de PowerShell-edities.</span><span class="sxs-lookup"><span data-stu-id="942cf-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="942cf-149">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="942cf-149">More details</span></span>

[<span data-ttu-id="942cf-150">Scripts met PSEditions</span><span class="sxs-lookup"><span data-stu-id="942cf-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="942cf-151">Ondersteuning op PowerShellGallery PSEditions</span><span class="sxs-lookup"><span data-stu-id="942cf-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="942cf-152">Modulemanifest bijwerken</span><span class="sxs-lookup"><span data-stu-id="942cf-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="942cf-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="942cf-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
