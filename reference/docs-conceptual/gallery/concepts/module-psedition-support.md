---
ms.date: 03/28/2019
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: Modules met compatibele Power shell-edities
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329188"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="2205d-103">Modules met compatibele Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="2205d-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="2205d-104">Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="2205d-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="2205d-105">**Desktop Edition:** Gebaseerd op .NET Framework, is van toepassing op Windows Power shell v 4.0 en hieronder, evenals Windows Power shell 5,1 op Windows Desktop, Windows Server, Windows Server Core en de meeste andere Windows-edities.</span><span class="sxs-lookup"><span data-stu-id="2205d-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="2205d-106">**Core-editie:** Gebaseerd op .NET core, is van toepassing op Power shell Core 6,0 en hoger, evenals Windows Power shell 5,1 op Windows-edities met verminderde footprint, zoals Windows IoT en Windows nano server.</span><span class="sxs-lookup"><span data-stu-id="2205d-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="2205d-107">Zie [about_PowerShell_Editions][]voor meer informatie over Power shell-edities.</span><span class="sxs-lookup"><span data-stu-id="2205d-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="2205d-108">Compatibele edities declareren</span><span class="sxs-lookup"><span data-stu-id="2205d-108">Declaring compatible editions</span></span>

<span data-ttu-id="2205d-109">Auteurs van modules kunnen hun modules zo opstellen dat deze compatibel zijn met een of meer PowerShell-edities door de sleutel voor het modulemanifestbestand CompatiblePSEditions te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2205d-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="2205d-110">Deze sleutel wordt alleen ondersteund in PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="2205d-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="2205d-111">Zodra een module manifest is opgegeven met de CompatiblePSEditions-sleutel, kan het niet worden geïmporteerd in Power shell-versie 4 en lager.</span><span class="sxs-lookup"><span data-stu-id="2205d-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

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

<span data-ttu-id="2205d-112">Bij het ophalen van een lijst met beschikbare modules kunt u de lijst filteren op PowerShell-editie.</span><span class="sxs-lookup"><span data-stu-id="2205d-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

## <a name="targeting-multiple-editions"></a><span data-ttu-id="2205d-113">Meerdere edities richten</span><span class="sxs-lookup"><span data-stu-id="2205d-113">Targeting multiple editions</span></span>

<span data-ttu-id="2205d-114">Ontwerpers van modules kunnen één module richten op een of beide Power shell-edities (desktop en Core).</span><span class="sxs-lookup"><span data-stu-id="2205d-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="2205d-115">Eén module kan zowel op bureau blad-als op kern-edities worden uitgevoerd. in die module auteur moet de vereiste logica worden toegevoegd in RootModule of in het manifest module met $PSEdition variabele.</span><span class="sxs-lookup"><span data-stu-id="2205d-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="2205d-116">Modules kunnen twee sets gecompileerde Dll's hebben die zijn gericht op zowel CoreCLR als FullCLR.</span><span class="sxs-lookup"><span data-stu-id="2205d-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="2205d-117">Hier vindt u een aantal opties voor het inpakken van uw module met logica voor het laden van de juiste dll's.</span><span class="sxs-lookup"><span data-stu-id="2205d-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="2205d-118">Optie 1: Een module verpakken voor het richten op meerdere versies en meerdere versies van Power shell</span><span class="sxs-lookup"><span data-stu-id="2205d-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="2205d-119">Inhoud van module map</span><span class="sxs-lookup"><span data-stu-id="2205d-119">Module folder contents</span></span>

- <span data-ttu-id="2205d-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="2205d-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="2205d-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="2205d-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="2205d-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="2205d-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="2205d-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="2205d-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="2205d-124">ScriptAnalyzer. Format. ps1xml</span><span class="sxs-lookup"><span data-stu-id="2205d-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="2205d-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="2205d-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="2205d-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="2205d-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="2205d-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="2205d-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="2205d-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="2205d-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="2205d-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="2205d-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="2205d-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="2205d-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="2205d-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="2205d-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="2205d-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="2205d-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="2205d-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="2205d-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="2205d-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="2205d-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="2205d-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="2205d-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="2205d-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="2205d-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="2205d-137">Inhoud van het bestand PSScriptAnalyzer. psd1</span><span class="sxs-lookup"><span data-stu-id="2205d-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

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

<span data-ttu-id="2205d-138">Onder Logic worden de vereiste assembly's geladen, afhankelijk van de huidige editie of versie.</span><span class="sxs-lookup"><span data-stu-id="2205d-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="2205d-139">Inhoud van het bestand PSScriptAnalyzer. psm1:</span><span class="sxs-lookup"><span data-stu-id="2205d-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="2205d-140">Optie 2: Gebruik $PSEdition variabele in het PSD1-bestand om de juiste Dll's en geneste/vereiste modules te laden</span><span class="sxs-lookup"><span data-stu-id="2205d-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="2205d-141">In PS 5,1 of hoger is $PSEdition globale variabele toegestaan in het manifest bestand van de module.</span><span class="sxs-lookup"><span data-stu-id="2205d-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="2205d-142">Met deze variabele kan module Author de voorwaardelijke waarden opgeven in het manifest bestand van de module.</span><span class="sxs-lookup"><span data-stu-id="2205d-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="2205d-143">Naar $PSEdition-variabele kan worden verwezen in de modus voor beperkte talen of in een gegevens gedeelte.</span><span class="sxs-lookup"><span data-stu-id="2205d-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="2205d-144">Zodra een module manifest is opgegeven met de sleutel CompatiblePSEditions of de `$PSEdition` variabele gebruikt, kan het niet worden geïmporteerd in lagere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2205d-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="2205d-145">Voor beeld van module manifest bestand met CompatiblePSEditions-sleutel</span><span class="sxs-lookup"><span data-stu-id="2205d-145">Sample module manifest file with CompatiblePSEditions key</span></span>

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

### <a name="module-contents"></a><span data-ttu-id="2205d-146">Inhoud van module</span><span class="sxs-lookup"><span data-stu-id="2205d-146">Module contents</span></span>

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

<span data-ttu-id="2205d-147">PowerShell Gallery gebruikers kunnen de lijst met modules die worden ondersteund in een specifieke Power shell-editie vinden met behulp van de labels PSEdition_Desktop en PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="2205d-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="2205d-148">Modules zonder PSEdition_Desktop-en PSEdition_Core-Tags worden beschouwd als goed op Power shell-Desktop-edities.</span><span class="sxs-lookup"><span data-stu-id="2205d-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="2205d-149">Meer Details</span><span class="sxs-lookup"><span data-stu-id="2205d-149">More details</span></span>

[<span data-ttu-id="2205d-150">Scripts met PSEditions</span><span class="sxs-lookup"><span data-stu-id="2205d-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="2205d-151">PSEditions-ondersteuning op PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="2205d-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="2205d-152">Modulemanifest bijwerken</span><span class="sxs-lookup"><span data-stu-id="2205d-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="2205d-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="2205d-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
