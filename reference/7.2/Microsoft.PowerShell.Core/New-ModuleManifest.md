---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 6705cc5a7fdd2e2db87d35d262b04d088237ff7d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706192"
---
# <span data-ttu-id="a628d-102">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="a628d-102">New-ModuleManifest</span></span>

## <span data-ttu-id="a628d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a628d-103">SYNOPSIS</span></span>
<span data-ttu-id="a628d-104">Hiermee maakt u een nieuw module manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-104">Creates a new module manifest.</span></span>

## <span data-ttu-id="a628d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a628d-105">SYNTAX</span></span>

### <span data-ttu-id="a628d-106">Alles</span><span class="sxs-lookup"><span data-stu-id="a628d-106">All</span></span>

```
New-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <Version>] [-CLRVersion <Version>] [-DotNetFrameworkVersion <Version>]
 [-PowerShellHostName <String>] [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>]
 [-RequiredAssemblies <String[]>] [-FileList <String[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <String[]>] [-AliasesToExport <String[]>] [-VariablesToExport <String[]>]
 [-CmdletsToExport <String[]>] [-DscResourcesToExport <String[]>] [-CompatiblePSEditions <String[]>]
 [-PrivateData <Object>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ReleaseNotes <String>] [-Prerelease <String>] [-RequireLicenseAcceptance]
 [-ExternalModuleDependencies <String[]>] [-HelpInfoUri <String>] [-PassThru]
 [-DefaultCommandPrefix <String>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="a628d-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a628d-107">DESCRIPTION</span></span>

<span data-ttu-id="a628d-108">De `New-ModuleManifest` cmdlet maakt een nieuw module manifest `.psd1` bestand (), vult de waarden ervan en slaat het manifest bestand op in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="a628d-108">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="a628d-109">Module auteurs kunnen deze cmdlet gebruiken om een manifest te maken voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-109">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="a628d-110">Een module manifest is een `.psd1` bestand dat een hash-tabel bevat.</span><span class="sxs-lookup"><span data-stu-id="a628d-110">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="a628d-111">De sleutels en waarden in de hash-tabel beschrijven de inhoud en kenmerken van de module, definiëren de vereisten en bepalen hoe de onderdelen worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="a628d-111">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="a628d-112">Manifesten zijn niet vereist voor een module.</span><span class="sxs-lookup"><span data-stu-id="a628d-112">Manifests aren't required for a module.</span></span>

<span data-ttu-id="a628d-113">`New-ModuleManifest` Hiermee maakt u een manifest dat alle veelgebruikte manifest sleutels bevat, zodat u de standaard uitvoer als een manifest sjabloon kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a628d-113">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="a628d-114">Om waarden toe te voegen of te wijzigen of om module sleutels toe te voegen die met deze cmdlet niet worden toegevoegd, opent u het resulterende bestand in een tekst editor.</span><span class="sxs-lookup"><span data-stu-id="a628d-114">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="a628d-115">Elke para meter, met uitzonde ring van **pad** en **PassThru**, maakt een module manifest sleutel en de bijbehorende waarde.</span><span class="sxs-lookup"><span data-stu-id="a628d-115">Each parameter, except for **Path** and **PassThru**, creates a module manifest key and its value.</span></span>
<span data-ttu-id="a628d-116">In een module manifest is alleen de sleutel **ModuleVersion** vereist.</span><span class="sxs-lookup"><span data-stu-id="a628d-116">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="a628d-117">Tenzij u de para meter in de parameter beschrijving opgeeft, `New-ModuleManifest` maakt een teken reeks voor de bijbehorende waarde die geen effect heeft.</span><span class="sxs-lookup"><span data-stu-id="a628d-117">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="a628d-118">In Power Shell 2,0 `New-ModuleManifest` vraagt u om de waarden van vaak gebruikte para meters die niet zijn opgegeven in de opdracht, naast de vereiste parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="a628d-118">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="a628d-119">Vanaf Power Shell 3,0 `New-ModuleManifest` worden alleen vragen wanneer de vereiste parameter waarden niet zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a628d-119">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="a628d-120">Als u van plan bent uw module te publiceren in de PowerShell Gallery, moet het manifest waarden voor bepaalde eigenschappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="a628d-120">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="a628d-121">Zie [vereiste meta gegevens voor items die zijn gepubliceerd op de PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in de galerie documentatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a628d-121">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="a628d-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a628d-122">EXAMPLES</span></span>

### <span data-ttu-id="a628d-123">Voor beeld 1: een nieuw module manifest maken</span><span class="sxs-lookup"><span data-stu-id="a628d-123">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="a628d-124">In dit voor beeld wordt een nieuw module manifest gemaakt in het bestand dat is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="a628d-124">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="a628d-125">De para meter **PassThru** verzendt de uitvoer naar de pijp lijn en naar het bestand.</span><span class="sxs-lookup"><span data-stu-id="a628d-125">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="a628d-126">De uitvoer toont de standaard waarden van alle sleutels in het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-126">The output shows the default values of all keys in the manifest.</span></span>

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 7/12/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'e1826c6e-c420-4eef-9ac8-185e3669ca6a'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) ContosoAdmin. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        # RequireLicenseAcceptance = $false

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

### <span data-ttu-id="a628d-127">Voor beeld 2: een nieuw manifest maken met enkele vooraf ingevulde instellingen</span><span class="sxs-lookup"><span data-stu-id="a628d-127">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="a628d-128">In dit voor beeld wordt een nieuw module manifest gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a628d-128">This example creates a new module manifest.</span></span> <span data-ttu-id="a628d-129">De para meters **PowerShellVersion** en **AliasesToExport** worden gebruikt om waarden toe te voegen aan de corresponderende manifest sleutels.</span><span class="sxs-lookup"><span data-stu-id="a628d-129">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="a628d-130">Voor beeld 3: een manifest maken waarvoor andere modules zijn vereist</span><span class="sxs-lookup"><span data-stu-id="a628d-130">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="a628d-131">In dit voor beeld wordt een teken reeks notatie gebruikt voor het opgeven van de naam van de **BitsTransfer** -module en de indeling van de hash-tabel om de naam, een **GUID** en een versie van de **PSScheduledJob** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="a628d-131">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID**, and a version of the **PSScheduledJob** module.</span></span>

```powershell
$moduleSettings = @{
  RequiredModules = ("BitsTransfer", @{
    ModuleName="PSScheduledJob"
    ModuleVersion="1.0.0.0";
    GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"
  })
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="a628d-132">In dit voor beeld ziet u hoe u de notatie teken reeks en hash-tabel gebruikt van de para meter **ModuleList**, **RequiredModules** en **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="a628d-132">This example shows how to use the string and hash table formats of the **ModuleList**, **RequiredModules**, and **NestedModules** parameter.</span></span> <span data-ttu-id="a628d-133">U kunt teken reeksen en hash-tabellen combi neren in dezelfde parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="a628d-133">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="a628d-134">Voor beeld 4: een manifest maken dat kan worden bijgewerkt met ondersteuning</span><span class="sxs-lookup"><span data-stu-id="a628d-134">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="a628d-135">In dit voor beeld wordt de para meter **HelpInfoUri** gebruikt om een **HelpInfoUri** -sleutel te maken in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-135">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="a628d-136">De waarde van de para meter en de sleutel moeten beginnen met **http** of **https**.</span><span class="sxs-lookup"><span data-stu-id="a628d-136">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="a628d-137">Deze waarde vertelt het bijwerk bare Help-systeem waar u het HelpInfo XML-bestand met Help-informatie voor de module kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="a628d-137">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="a628d-138">Zie [about_Updatable_Help](./About/about_Updatable_Help.md)voor meer informatie over de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="a628d-138">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="a628d-139">Zie voor meer informatie over het HelpInfo XML-bestand [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="a628d-139">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="a628d-140">Voor beeld 5: informatie over module ophalen</span><span class="sxs-lookup"><span data-stu-id="a628d-140">Example 5 - Getting module information</span></span>

<span data-ttu-id="a628d-141">In dit voor beeld ziet u hoe u de configuratie waarden van een module ophaalt.</span><span class="sxs-lookup"><span data-stu-id="a628d-141">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="a628d-142">De waarden in het module manifest worden weer spie geld in de waarden van eigenschappen van het module-object.</span><span class="sxs-lookup"><span data-stu-id="a628d-142">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="a628d-143">De `Get-Module` cmdlet wordt gebruikt om de module **micro soft. Power shell. Diagnostics** te verkrijgen met de para meter **List** .</span><span class="sxs-lookup"><span data-stu-id="a628d-143">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="a628d-144">De opdracht verzendt de module naar de `Format-List` cmdlet om alle eigenschappen en waarden van het module-object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a628d-144">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

```powershell
Get-Module Microsoft.PowerShell.Diagnostics -List | Format-List -Property *
```

```Output
LogPipelineExecutionDetails : False
Name                        : Microsoft.PowerShell.Diagnostics
Path                        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics\Micro
                              soft.PowerShell.Diagnostics.psd1
Definition                  :
Description                 :
Guid                        : ca046f10-ca64-4740-8ff9-2565dba61a4f
HelpInfoUri                 : https://go.microsoft.com/fwlink/?LinkID=210596
ModuleBase                  : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics
PrivateData                 :
Version                     : 3.0.0.0
ModuleType                  : Manifest
Author                      : Microsoft Corporation
AccessMode                  : ReadWrite
ClrVersion                  : 4.0
CompanyName                 : Microsoft Corporation
Copyright                   : Microsoft Corporation. All rights reserved.
DotNetFrameworkVersion      :
ExportedFunctions           : {}
ExportedCmdlets             : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
ExportedCommands            : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
FileList                    : {}
ModuleList                  : {}
NestedModules               : {}
PowerShellHostName          :
PowerShellHostVersion       :
PowerShellVersion           : 3.0
ProcessorArchitecture       : None
Scripts                     : {}
RequiredAssemblies          : {}
RequiredModules             : {}
RootModule                  :
ExportedVariables           : {}
ExportedAliases             : {}
ExportedWorkflows           : {}
SessionState                :
OnRemove                    :
ExportedFormatFiles         : {C:\Windows\system32\WindowsPowerShell\v1.0\Event.format.ps1xml,
                              C:\Windows\system32\WindowsPowerShell\v1.0\Diagnostics.format.ps1xml}
ExportedTypeFiles           : {C:\Windows\system32\WindowsPowerShell\v1.0\GetEvent.types.ps1xml}
```

## <span data-ttu-id="a628d-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a628d-145">PARAMETERS</span></span>

### <span data-ttu-id="a628d-146">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="a628d-146">-AliasesToExport</span></span>

<span data-ttu-id="a628d-147">Hiermee geeft u de aliassen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="a628d-147">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="a628d-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a628d-148">Wildcards are permitted.</span></span>

<span data-ttu-id="a628d-149">U kunt deze para meter gebruiken om de aliassen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-149">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="a628d-150">Het kan aliassen verwijderen uit de lijst met geëxporteerde aliassen, maar kan geen aliassen toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="a628d-150">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="a628d-151">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **AliasesToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle aliassen die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-151">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a628d-152">-Author</span><span class="sxs-lookup"><span data-stu-id="a628d-152">-Author</span></span>

<span data-ttu-id="a628d-153">Hiermee geeft u de auteur van de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-153">Specifies the module author.</span></span>

<span data-ttu-id="a628d-154">Als u deze para meter weglaat, `New-ModuleManifest` wordt een **auteurs** sleutel gemaakt met de naam van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a628d-154">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Name of the current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-155">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="a628d-155">-CmdletsToExport</span></span>

<span data-ttu-id="a628d-156">Hiermee geeft u de cmdlets op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="a628d-156">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="a628d-157">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a628d-157">Wildcards are permitted.</span></span>

<span data-ttu-id="a628d-158">U kunt deze para meter gebruiken om de cmdlets te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-158">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="a628d-159">Hiermee kunnen cmdlets worden verwijderd uit de lijst met geëxporteerde cmdlets, maar kunnen geen cmdlets worden toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="a628d-159">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="a628d-160">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **CmdletsToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle cmdlets die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-160">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a628d-161">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="a628d-161">-CompanyName</span></span>

<span data-ttu-id="a628d-162">Identificeert het bedrijf of de leverancier die de module heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a628d-162">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="a628d-163">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een sleutel van de **bedrijf** met de waarde ' Unknown '.</span><span class="sxs-lookup"><span data-stu-id="a628d-163">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: "Unknown"
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-164">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="a628d-164">-CompatiblePSEditions</span></span>

<span data-ttu-id="a628d-165">Hiermee geeft u de compatibele PSEditions van de module op.</span><span class="sxs-lookup"><span data-stu-id="a628d-165">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="a628d-166">Zie [modules met compatibele Power shell-edities](/powershell/scripting/gallery/concepts/module-psedition-support)voor meer informatie over PSEdition.</span><span class="sxs-lookup"><span data-stu-id="a628d-166">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-167">-Copyright</span><span class="sxs-lookup"><span data-stu-id="a628d-167">-Copyright</span></span>

<span data-ttu-id="a628d-168">Hiermee geeft u een copyright verklaring voor de module op.</span><span class="sxs-lookup"><span data-stu-id="a628d-168">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="a628d-169">Als u deze para meter weglaat, `New-ModuleManifest` maakt een **copyright** sleutel met `(c) <year> <username>. All rights reserved.` de waarde waar `<year>` het huidige jaar is en `<username>` is de waarde van de sleutel **Auteur** .</span><span class="sxs-lookup"><span data-stu-id="a628d-169">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (c) <year> <username>. All rights reserved.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-170">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="a628d-170">-DefaultCommandPrefix</span></span>

<span data-ttu-id="a628d-171">Hiermee geeft u een voor voegsel op dat wordt geplaatst voor de naam woorden van alle opdrachten in de module wanneer deze in een sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-171">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="a628d-172">Voer een voorvoegsel teken reeks in.</span><span class="sxs-lookup"><span data-stu-id="a628d-172">Enter a prefix string.</span></span> <span data-ttu-id="a628d-173">Voor voegsels voor komen conflicten met opdracht namen in de sessie van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a628d-173">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="a628d-174">Module gebruikers kunnen dit voor voegsel overschrijven door de para meter **voor het voor voegsel** van de cmdlet op te geven `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="a628d-174">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="a628d-175">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a628d-175">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-176">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a628d-176">-Description</span></span>

<span data-ttu-id="a628d-177">Beschrijft de inhoud van de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-177">Describes the contents of the module.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-178">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="a628d-178">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="a628d-179">Hiermee geeft u de minimale versie van het Microsoft .NET Framework op dat voor de module nodig is.</span><span class="sxs-lookup"><span data-stu-id="a628d-179">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-180">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="a628d-180">-DscResourcesToExport</span></span>

<span data-ttu-id="a628d-181">Hiermee geeft u de resources voor desired state Configuration (DSC) op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="a628d-181">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="a628d-182">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a628d-182">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a628d-183">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="a628d-183">-ExternalModuleDependencies</span></span>

<span data-ttu-id="a628d-184">Een lijst met externe modules waarvan deze module afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="a628d-184">A list of external modules that this module is depends on.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-185">-File List</span><span class="sxs-lookup"><span data-stu-id="a628d-185">-FileList</span></span>

<span data-ttu-id="a628d-186">Hiermee geeft u alle items die zijn opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-186">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="a628d-187">Deze sleutel is ontworpen om te fungeren als een module-inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="a628d-187">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="a628d-188">De bestanden die in de sleutel worden vermeld, worden opgenomen als de module wordt gepubliceerd, maar alle functies worden niet automatisch geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-188">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-189">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="a628d-189">-FormatsToProcess</span></span>

<span data-ttu-id="a628d-190">Hiermee geeft u de indelings bestanden ( `.ps1xml` ) op die worden uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-190">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="a628d-191">Wanneer u een module importeert, voert Power shell de `Update-FormatData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="a628d-191">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="a628d-192">Omdat de indelings bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="a628d-192">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-193">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="a628d-193">-FunctionsToExport</span></span>

<span data-ttu-id="a628d-194">Hiermee geeft u de functies op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="a628d-194">Specifies the functions that the module exports.</span></span> <span data-ttu-id="a628d-195">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a628d-195">Wildcards are permitted.</span></span>

<span data-ttu-id="a628d-196">U kunt deze para meter gebruiken om de functies te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-196">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="a628d-197">De functie kan functies uit de lijst geëxporteerde aliassen verwijderen, maar kan geen functies toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="a628d-197">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="a628d-198">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **FunctionsToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle functies die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-198">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a628d-199">-GUID</span><span class="sxs-lookup"><span data-stu-id="a628d-199">-Guid</span></span>

<span data-ttu-id="a628d-200">Hiermee geeft u een unieke id op voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-200">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="a628d-201">De **GUID** kan worden gebruikt om onderscheid te maken tussen modules met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="a628d-201">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="a628d-202">Als u deze para meter weglaat, `New-ModuleManifest` wordt een **GUID** -sleutel gemaakt in het manifest en wordt een **GUID** voor de waarde gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-202">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="a628d-203">Als u een nieuwe **GUID** wilt maken in Power shell, typt u `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="a628d-203">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A GUID generated for the module
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-204">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="a628d-204">-HelpInfoUri</span></span>

<span data-ttu-id="a628d-205">Hiermee geeft u het Internet adres op van het HelpInfo XML-bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-205">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="a628d-206">Voer een URI (Uniform Resource Identifier) in die begint met **http** of **https**.</span><span class="sxs-lookup"><span data-stu-id="a628d-206">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="a628d-207">Het XML-bestand HelpInfo ondersteunt de bijwerk bare Help-functie die is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a628d-207">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="a628d-208">Het bevat informatie over de locatie van de Download bare Help bestanden voor de module en de versie nummers van de nieuwste Help-bestanden voor elke ondersteunde land instelling.</span><span class="sxs-lookup"><span data-stu-id="a628d-208">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="a628d-209">Zie [about_Updatable_Help](./About/about_Updatable_Help.md)voor meer informatie over de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="a628d-209">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="a628d-210">Zie voor meer informatie over het HelpInfo XML-bestand [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="a628d-210">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="a628d-211">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a628d-211">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-212">-IconUri</span><span class="sxs-lookup"><span data-stu-id="a628d-212">-IconUri</span></span>

<span data-ttu-id="a628d-213">Hiermee geeft u de URL op van een pictogram voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-213">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="a628d-214">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-214">The specified icon is displayed on the gallery web page for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-215">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="a628d-215">-LicenseUri</span></span>

<span data-ttu-id="a628d-216">Hiermee geeft u de URL op van de licentie voorwaarden voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-216">Specifies the URL of licensing terms for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-217">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="a628d-217">-ModuleList</span></span>

<span data-ttu-id="a628d-218">Een lijst met alle modules die in deze module zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="a628d-218">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="a628d-219">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="a628d-219">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="a628d-220">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="a628d-220">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="a628d-221">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="a628d-221">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="a628d-222">Deze sleutel is ontworpen om te fungeren als een module-inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="a628d-222">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="a628d-223">De modules die in de waarde van deze sleutel worden vermeld, worden niet automatisch verwerkt.</span><span class="sxs-lookup"><span data-stu-id="a628d-223">The modules that are listed in the value of this key aren't automatically processed.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-224">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="a628d-224">-ModuleVersion</span></span>

<span data-ttu-id="a628d-225">Hiermee geeft u de versie van de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-225">Specifies the module's version.</span></span>

<span data-ttu-id="a628d-226">Deze para meter is niet vereist, maar er is een **ModuleVersion** -sleutel vereist in het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-226">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="a628d-227">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **ModuleVersion** -sleutel met de waarde 1,0.</span><span class="sxs-lookup"><span data-stu-id="a628d-227">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1.0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-228">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="a628d-228">-NestedModules</span></span>

<span data-ttu-id="a628d-229">Hiermee geeft u script modules ( `.psm1` ) en binaire modules ( `.dll` ) op die worden geïmporteerd in de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-229">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="a628d-230">De bestanden in de **NestedModules** -sleutel worden uitgevoerd in de volg orde waarin ze worden weer gegeven in de waarde.</span><span class="sxs-lookup"><span data-stu-id="a628d-230">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="a628d-231">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="a628d-231">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="a628d-232">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="a628d-232">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="a628d-233">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="a628d-233">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="a628d-234">Normaal gesp roken bevatten geneste modules opdrachten die de hoofd module nodig heeft voor de interne verwerking.</span><span class="sxs-lookup"><span data-stu-id="a628d-234">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="a628d-235">Standaard worden de opdrachten in geneste modules geëxporteerd van de sessie status van de module naar de sessie status van de beller, maar de hoofd module kan de opdrachten die worden geëxporteerd, beperken.</span><span class="sxs-lookup"><span data-stu-id="a628d-235">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="a628d-236">Bijvoorbeeld met behulp van een `Export-ModuleMember` opdracht.</span><span class="sxs-lookup"><span data-stu-id="a628d-236">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="a628d-237">Geneste modules in de module sessie status zijn beschikbaar voor de hoofd module, maar ze worden niet geretourneerd door een `Get-Module` opdracht in de sessie status van de beller.</span><span class="sxs-lookup"><span data-stu-id="a628d-237">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="a628d-238">Scripts ( `.ps1` ) die worden vermeld in de sleutel **NestedModules** , worden uitgevoerd in de sessie status van de module, niet in de sessie status van de beller.</span><span class="sxs-lookup"><span data-stu-id="a628d-238">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="a628d-239">Als u een script wilt uitvoeren in de sessie status van de aanroeper, vermeldt u de naam van het script bestand in de waarde van de sleutel **ScriptsToProcess** in het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-239">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-240">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a628d-240">-PassThru</span></span>

<span data-ttu-id="a628d-241">Hiermee schrijft u het resulterende module manifest naar de-console en maakt u een `.psd1` bestand.</span><span class="sxs-lookup"><span data-stu-id="a628d-241">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="a628d-242">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a628d-242">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-243">-Path</span><span class="sxs-lookup"><span data-stu-id="a628d-243">-Path</span></span>

<span data-ttu-id="a628d-244">Hiermee geeft u het pad en de bestands naam van het nieuwe module manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-244">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="a628d-245">Voer een pad en een bestands naam in met een `.psd1` bestands extensie, zoals `$pshome\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="a628d-245">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="a628d-246">De para meter **Path** is vereist.</span><span class="sxs-lookup"><span data-stu-id="a628d-246">The **Path** parameter is required.</span></span>

<span data-ttu-id="a628d-247">Als u het pad naar een bestaand bestand opgeeft, wordt `New-ModuleManifest` het bestand vervangen zonder waarschuwing tenzij het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="a628d-247">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="a628d-248">Het manifest moet zich in de map van de module bevinden en de naam van het manifest bestand moet hetzelfde zijn als de naam van de module directory, maar met een `.psd1` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="a628d-248">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="a628d-249">U kunt geen variabelen, zoals `$PSHOME` of, gebruiken als `$HOME` antwoord op een prompt voor een **pad** parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="a628d-249">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="a628d-250">Als u een variabele wilt gebruiken, neemt u de para meter **Path** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a628d-250">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-251">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="a628d-251">-PowerShellHostName</span></span>

<span data-ttu-id="a628d-252">Hiermee geeft u de naam op van het Power shell-hostprogramma dat is vereist voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-252">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="a628d-253">Voer de naam van het hostprogramma in, zoals **Windows PowerShell ISE host** of **ConsoleHost**.</span><span class="sxs-lookup"><span data-stu-id="a628d-253">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="a628d-254">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a628d-254">Wildcards aren't permitted.</span></span>

<span data-ttu-id="a628d-255">Als u de naam van een hostprogramma wilt zoeken, typt u in het programma `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="a628d-255">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-256">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="a628d-256">-PowerShellHostVersion</span></span>

<span data-ttu-id="a628d-257">Hiermee geeft u de minimale versie van het Power shell-hostprogramma op dat met de module werkt.</span><span class="sxs-lookup"><span data-stu-id="a628d-257">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="a628d-258">Voer een versie nummer in, bijvoorbeeld 1,1.</span><span class="sxs-lookup"><span data-stu-id="a628d-258">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-259">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="a628d-259">-PowerShellVersion</span></span>

<span data-ttu-id="a628d-260">Hiermee geeft u de minimale versie van Power shell op die met deze module werkt.</span><span class="sxs-lookup"><span data-stu-id="a628d-260">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="a628d-261">U kunt bijvoorbeeld 1,0, 2,0 of 3,0 invoeren als waarde voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="a628d-261">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-262">-Prerelease</span><span class="sxs-lookup"><span data-stu-id="a628d-262">-Prerelease</span></span>

<span data-ttu-id="a628d-263">De teken reeks voor de voorlopige versie van deze module.</span><span class="sxs-lookup"><span data-stu-id="a628d-263">Prerelease string of this module.</span></span> <span data-ttu-id="a628d-264">Als u een prerelease-teken reeks toevoegt, wordt de module geïdentificeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="a628d-264">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="a628d-265">Wanneer de module is gepubliceerd naar de PowerShell Gallery, worden deze gegevens gebruikt om voorlopige pakketten te identificeren.</span><span class="sxs-lookup"><span data-stu-id="a628d-265">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="a628d-266">Als u voorlopige pakketten wilt ophalen uit de galerie, moet u de para meter **AllowPrerelease** gebruiken met de PowerShellGet-opdrachten `Find-Module` ,, `Install-Module` `Update-Module` en `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="a628d-266">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-267">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="a628d-267">-PrivateData</span></span>

<span data-ttu-id="a628d-268">Hiermee geeft u de gegevens op die worden door gegeven aan de module wanneer deze wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-268">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-269">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="a628d-269">-ProcessorArchitecture</span></span>

<span data-ttu-id="a628d-270">Hiermee geeft u de processor architectuur op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="a628d-270">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="a628d-271">Geldige waarden zijn x86, AMD64, IA64, MSIL en geen (onbekend of niet opgegeven).</span><span class="sxs-lookup"><span data-stu-id="a628d-271">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-272">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="a628d-272">-ProjectUri</span></span>

<span data-ttu-id="a628d-273">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="a628d-273">Specifies the URL of a web page about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-274">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="a628d-274">-ReleaseNotes</span></span>

<span data-ttu-id="a628d-275">Geeft opmerkingen bij de release.</span><span class="sxs-lookup"><span data-stu-id="a628d-275">Specifies release notes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-276">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="a628d-276">-RequiredAssemblies</span></span>

<span data-ttu-id="a628d-277">Hiermee geeft u de assembly ( `.dll` )-bestanden op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="a628d-277">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="a628d-278">Voer de namen van de assembly bestanden in.</span><span class="sxs-lookup"><span data-stu-id="a628d-278">Enter the assembly file names.</span></span>
<span data-ttu-id="a628d-279">Power shell laadt de opgegeven assembly's vóór het bijwerken van typen of indelingen, het importeren van geneste modules of het importeren van het module bestand dat is opgegeven in de waarde van de sleutel **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="a628d-279">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="a628d-280">Gebruik deze para meter om alle assembly's weer te geven die voor de module vereist zijn, inclusief de assembly's die moeten worden geladen voor het bijwerken van de opmaak of het type van bestanden die worden vermeld in de sleutels **FormatsToProcess** of **TypesToProcess** , zelfs als deze assembly's ook worden vermeld als binaire modules in de **NestedModules** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="a628d-280">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-281">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="a628d-281">-RequiredModules</span></span>

<span data-ttu-id="a628d-282">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="a628d-282">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="a628d-283">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-283">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="a628d-284">Als de vereiste modules niet beschikbaar zijn, `Import-Module` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a628d-284">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="a628d-285">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="a628d-285">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="a628d-286">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="a628d-286">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="a628d-287">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="a628d-287">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="a628d-288">In Power Shell 2,0 worden de `Import-Module` vereiste modules niet automatisch geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-288">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="a628d-289">Er wordt alleen gecontroleerd of de vereiste modules zich in de status van de globale sessie bevinden.</span><span class="sxs-lookup"><span data-stu-id="a628d-289">It just verifies that the required modules are in the global session state.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-290">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="a628d-290">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="a628d-291">Markering om aan te geven of voor de module expliciete gebruikers acceptatie is vereist voor install, update, orsave.</span><span class="sxs-lookup"><span data-stu-id="a628d-291">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-292">-RootModule</span><span class="sxs-lookup"><span data-stu-id="a628d-292">-RootModule</span></span>

<span data-ttu-id="a628d-293">Hiermee geeft u het primaire of hoofd bestand van de module op.</span><span class="sxs-lookup"><span data-stu-id="a628d-293">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="a628d-294">Voer de bestands naam van een script ( `.ps1` ), een script module ( `.psm1` ), een module manifest ( `.psd1` ), een assembly ( `.dll` ), een XML-bestand voor de cmdlet-definitie ( `.cdxml` ) of een werk stroom ( `.xaml` ) in.</span><span class="sxs-lookup"><span data-stu-id="a628d-294">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="a628d-295">Wanneer de module wordt geïmporteerd, worden de leden die worden geëxporteerd uit het hoofd module bestand geïmporteerd in de sessie status van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="a628d-295">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="a628d-296">Als een module een manifest bestand heeft en er geen hoofd bestand is opgegeven in de **RootModule** -sleutel, wordt het manifest het primaire bestand voor de module en wordt de module een manifest module (module type = manifest).</span><span class="sxs-lookup"><span data-stu-id="a628d-296">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="a628d-297">Als u leden wilt exporteren uit `.psm1` of `.dll` bestanden in een module met een manifest, moeten de namen van die bestanden worden opgegeven in de waarden van de sleutels **RootModule** of **NestedModules** in het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-297">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="a628d-298">Anders worden de leden niet geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-298">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="a628d-299">In Power Shell 2,0 is deze sleutel **ModuleToProcess** genoemd.</span><span class="sxs-lookup"><span data-stu-id="a628d-299">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="a628d-300">U kunt de parameter naam van de **RootModule** of de **ModuleToProcess** -alias gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a628d-300">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ModuleToProcess

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-301">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="a628d-301">-ScriptsToProcess</span></span>

<span data-ttu-id="a628d-302">Hiermee geeft u script ( `.ps1` )-bestanden op die worden uitgevoerd in de sessie status van de aanroeper wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-302">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="a628d-303">U kunt deze scripts gebruiken om een omgeving voor te bereiden, net zoals u een aanmeldings script zou kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a628d-303">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="a628d-304">Als u scripts wilt opgeven die worden uitgevoerd in de sessie status van de module, gebruikt u de sleutel **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="a628d-304">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-305">-Tags</span><span class="sxs-lookup"><span data-stu-id="a628d-305">-Tags</span></span>

<span data-ttu-id="a628d-306">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="a628d-306">Specifies an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-307">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="a628d-307">-TypesToProcess</span></span>

<span data-ttu-id="a628d-308">Hiermee geeft u het type bestanden ( `.ps1xml` ) op dat wordt uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-308">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="a628d-309">Wanneer u de module importeert, voert Power shell de `Update-TypeData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="a628d-309">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="a628d-310">Omdat type bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="a628d-310">Because type files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-311">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="a628d-311">-VariablesToExport</span></span>

<span data-ttu-id="a628d-312">Hiermee geeft u de variabelen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="a628d-312">Specifies the variables that the module exports.</span></span> <span data-ttu-id="a628d-313">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a628d-313">Wildcards are permitted.</span></span>

<span data-ttu-id="a628d-314">U kunt deze para meter gebruiken om de variabelen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-314">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="a628d-315">Hiermee kunnen variabelen worden verwijderd uit de lijst met geëxporteerde variabelen, maar er kunnen geen variabelen worden toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="a628d-315">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="a628d-316">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **VariablesToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle variabelen die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-316">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a628d-317">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a628d-317">-Confirm</span></span>

<span data-ttu-id="a628d-318">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a628d-318">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-319">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a628d-319">-WhatIf</span></span>

<span data-ttu-id="a628d-320">Hier wordt weer gegeven wat er gebeurt als er `New-ModuleManifest` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-320">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="a628d-321">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-321">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-322">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="a628d-322">-ClrVersion</span></span>

<span data-ttu-id="a628d-323">Hiermee geeft u de minimale versie van common language runtime (CLR) op van het Microsoft .NET Framework dat vereist is voor de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-323">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a628d-324">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a628d-324">CommonParameters</span></span>
<span data-ttu-id="a628d-325">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a628d-325">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a628d-326">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a628d-326">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a628d-327">INVOER</span><span class="sxs-lookup"><span data-stu-id="a628d-327">INPUTS</span></span>

### <span data-ttu-id="a628d-328">Geen</span><span class="sxs-lookup"><span data-stu-id="a628d-328">None</span></span>

<span data-ttu-id="a628d-329">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="a628d-329">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a628d-330">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a628d-330">OUTPUTS</span></span>

### <span data-ttu-id="a628d-331">Geen of System. String</span><span class="sxs-lookup"><span data-stu-id="a628d-331">None or System.String</span></span>

<span data-ttu-id="a628d-332">Standaard genereert geen `New-ModuleManifest` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a628d-332">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="a628d-333">Als u echter de para meter **PassThru** gebruikt, wordt er een **System. String** -object gegenereerd dat het module manifest vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a628d-333">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="a628d-334">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a628d-334">NOTES</span></span>

<span data-ttu-id="a628d-335">`New-ModuleManifest` Als u werkt met Windows-en niet-Windows-platforms, worden module manifest- `.psd1` bestanden gemaakt die zijn gecodeerd als **UTF8NoBOM**.</span><span class="sxs-lookup"><span data-stu-id="a628d-335">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="a628d-336">Module manifesten zijn meestal optioneel.</span><span class="sxs-lookup"><span data-stu-id="a628d-336">Module manifests are usually optional.</span></span> <span data-ttu-id="a628d-337">Er is echter een module manifest vereist voor het exporteren van een assembly die is geïnstalleerd in de Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="a628d-337">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="a628d-338">Als u bestanden in de map wilt toevoegen of wijzigen `$pshome\Modules` , start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="a628d-338">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="a628d-339">Vanaf Power shell 6,2 probeert Power shell alle DLL-bestanden te laden die worden vermeld in de eigenschap **File List** van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-339">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="a628d-340">Systeem eigen Dll's bevindt zich in de **Bestands List** en worden niet geladen in het proces en de fout wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-340">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="a628d-341">Alle beheerde dll-bestanden worden in het proces geladen.</span><span class="sxs-lookup"><span data-stu-id="a628d-341">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="a628d-342">Dit gedrag is verwijderd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="a628d-342">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="a628d-343">In Power Shell 2,0 zijn veel para meters van `New-ModuleManifest` verplicht, ook al zijn ze niet vereist in een module manifest.</span><span class="sxs-lookup"><span data-stu-id="a628d-343">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="a628d-344">Vanaf Power Shell 3,0 is alleen de para meter **Path** verplicht.</span><span class="sxs-lookup"><span data-stu-id="a628d-344">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="a628d-345">Een sessie is een exemplaar van de Power shell-uitvoerings omgeving.</span><span class="sxs-lookup"><span data-stu-id="a628d-345">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="a628d-346">Een sessie kan een of meer sessie statussen hebben.</span><span class="sxs-lookup"><span data-stu-id="a628d-346">A session can have one or more session states.</span></span> <span data-ttu-id="a628d-347">Een sessie heeft standaard alleen een algemene sessie status, maar elke geïmporteerde module heeft een eigen sessie status.</span><span class="sxs-lookup"><span data-stu-id="a628d-347">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="a628d-348">Met sessie status kunnen de opdrachten in een module worden uitgevoerd zonder dat dit van invloed is op de globale sessie status.</span><span class="sxs-lookup"><span data-stu-id="a628d-348">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="a628d-349">De sessie status van de oproepende functie is de sessie status waarin een module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="a628d-349">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="a628d-350">Normaal gesp roken verwijst deze naar de status van de globale sessie, maar wanneer een module geneste modules importeert, is de aanroeper de module en de sessie status van de beller is de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="a628d-350">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="a628d-351">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a628d-351">RELATED LINKS</span></span>

[<span data-ttu-id="a628d-352">Exporteren-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="a628d-352">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="a628d-353">Get-module</span><span class="sxs-lookup"><span data-stu-id="a628d-353">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="a628d-354">Import-module</span><span class="sxs-lookup"><span data-stu-id="a628d-354">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="a628d-355">New-module</span><span class="sxs-lookup"><span data-stu-id="a628d-355">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="a628d-356">Remove-module</span><span class="sxs-lookup"><span data-stu-id="a628d-356">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="a628d-357">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="a628d-357">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="a628d-358">about_Modules</span><span class="sxs-lookup"><span data-stu-id="a628d-358">about_Modules</span></span>](./About/about_Modules.md)
