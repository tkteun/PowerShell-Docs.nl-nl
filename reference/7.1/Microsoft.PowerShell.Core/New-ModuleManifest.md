---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 5fbd197f6c22de0ca50b4d2b6b76a914b85f7120
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93253273"
---
# <span data-ttu-id="93142-103">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="93142-103">New-ModuleManifest</span></span>

## <span data-ttu-id="93142-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="93142-104">SYNOPSIS</span></span>
<span data-ttu-id="93142-105">Hiermee maakt u een nieuw module manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-105">Creates a new module manifest.</span></span>

## <span data-ttu-id="93142-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="93142-106">SYNTAX</span></span>

### <span data-ttu-id="93142-107">Alles</span><span class="sxs-lookup"><span data-stu-id="93142-107">All</span></span>

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

## <span data-ttu-id="93142-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="93142-108">DESCRIPTION</span></span>

<span data-ttu-id="93142-109">De `New-ModuleManifest` cmdlet maakt een nieuw module manifest `.psd1` bestand (), vult de waarden ervan en slaat het manifest bestand op in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="93142-109">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="93142-110">Module auteurs kunnen deze cmdlet gebruiken om een manifest te maken voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-110">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="93142-111">Een module manifest is een `.psd1` bestand dat een hash-tabel bevat.</span><span class="sxs-lookup"><span data-stu-id="93142-111">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="93142-112">De sleutels en waarden in de hash-tabel beschrijven de inhoud en kenmerken van de module, definiëren de vereisten en bepalen hoe de onderdelen worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="93142-112">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="93142-113">Manifesten zijn niet vereist voor een module.</span><span class="sxs-lookup"><span data-stu-id="93142-113">Manifests aren't required for a module.</span></span>

<span data-ttu-id="93142-114">`New-ModuleManifest` Hiermee maakt u een manifest dat alle veelgebruikte manifest sleutels bevat, zodat u de standaard uitvoer als een manifest sjabloon kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="93142-114">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="93142-115">Om waarden toe te voegen of te wijzigen of om module sleutels toe te voegen die met deze cmdlet niet worden toegevoegd, opent u het resulterende bestand in een tekst editor.</span><span class="sxs-lookup"><span data-stu-id="93142-115">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="93142-116">Elke para meter, met uitzonde ring van **pad** en **PassThru** , maakt een module manifest sleutel en de bijbehorende waarde.</span><span class="sxs-lookup"><span data-stu-id="93142-116">Each parameter, except for **Path** and **PassThru** , creates a module manifest key and its value.</span></span>
<span data-ttu-id="93142-117">In een module manifest is alleen de sleutel **ModuleVersion** vereist.</span><span class="sxs-lookup"><span data-stu-id="93142-117">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="93142-118">Tenzij u de para meter in de parameter beschrijving opgeeft, `New-ModuleManifest` maakt een teken reeks voor de bijbehorende waarde die geen effect heeft.</span><span class="sxs-lookup"><span data-stu-id="93142-118">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="93142-119">In Power Shell 2,0 `New-ModuleManifest` vraagt u om de waarden van vaak gebruikte para meters die niet zijn opgegeven in de opdracht, naast de vereiste parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="93142-119">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="93142-120">Vanaf Power Shell 3,0 `New-ModuleManifest` worden alleen vragen wanneer de vereiste parameter waarden niet zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="93142-120">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="93142-121">Als u van plan bent uw module te publiceren in de PowerShell Gallery, moet het manifest waarden voor bepaalde eigenschappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="93142-121">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="93142-122">Zie [vereiste meta gegevens voor items die zijn gepubliceerd op de PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in de galerie documentatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="93142-122">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="93142-123">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="93142-123">EXAMPLES</span></span>

### <span data-ttu-id="93142-124">Voor beeld 1: een nieuw module manifest maken</span><span class="sxs-lookup"><span data-stu-id="93142-124">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="93142-125">In dit voor beeld wordt een nieuw module manifest gemaakt in het bestand dat is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="93142-125">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="93142-126">De para meter **PassThru** verzendt de uitvoer naar de pijp lijn en naar het bestand.</span><span class="sxs-lookup"><span data-stu-id="93142-126">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="93142-127">De uitvoer toont de standaard waarden van alle sleutels in het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-127">The output shows the default values of all keys in the manifest.</span></span>

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

### <span data-ttu-id="93142-128">Voor beeld 2: een nieuw manifest maken met enkele vooraf ingevulde instellingen</span><span class="sxs-lookup"><span data-stu-id="93142-128">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="93142-129">In dit voor beeld wordt een nieuw module manifest gemaakt.</span><span class="sxs-lookup"><span data-stu-id="93142-129">This example creates a new module manifest.</span></span> <span data-ttu-id="93142-130">De para meters **PowerShellVersion** en **AliasesToExport** worden gebruikt om waarden toe te voegen aan de corresponderende manifest sleutels.</span><span class="sxs-lookup"><span data-stu-id="93142-130">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="93142-131">Voor beeld 3: een manifest maken waarvoor andere modules zijn vereist</span><span class="sxs-lookup"><span data-stu-id="93142-131">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="93142-132">In dit voor beeld wordt een teken reeks notatie gebruikt voor het opgeven van de naam van de **BitsTransfer** -module en de indeling van de hash-tabel om de naam, een **GUID** en een versie van de **PSScheduledJob** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="93142-132">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID** , and a version of the **PSScheduledJob** module.</span></span>

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

<span data-ttu-id="93142-133">In dit voor beeld ziet u hoe u de notatie teken reeks en hash-tabel gebruikt van de para meter **ModuleList** , **RequiredModules** en **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="93142-133">This example shows how to use the string and hash table formats of the **ModuleList** , **RequiredModules** , and **NestedModules** parameter.</span></span> <span data-ttu-id="93142-134">U kunt teken reeksen en hash-tabellen combi neren in dezelfde parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="93142-134">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="93142-135">Voor beeld 4: een manifest maken dat kan worden bijgewerkt met ondersteuning</span><span class="sxs-lookup"><span data-stu-id="93142-135">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="93142-136">In dit voor beeld wordt de para meter **HelpInfoUri** gebruikt om een **HelpInfoUri** -sleutel te maken in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-136">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="93142-137">De waarde van de para meter en de sleutel moeten beginnen met **http** of **https**.</span><span class="sxs-lookup"><span data-stu-id="93142-137">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="93142-138">Deze waarde vertelt het bijwerk bare Help-systeem waar u het HelpInfo XML-bestand met Help-informatie voor de module kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="93142-138">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="93142-139">Zie [about_Updatable_Help](./About/about_Updatable_Help.md)voor meer informatie over de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="93142-139">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="93142-140">Zie voor meer informatie over het HelpInfo XML-bestand [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="93142-140">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="93142-141">Voor beeld 5: informatie over module ophalen</span><span class="sxs-lookup"><span data-stu-id="93142-141">Example 5 - Getting module information</span></span>

<span data-ttu-id="93142-142">In dit voor beeld ziet u hoe u de configuratie waarden van een module ophaalt.</span><span class="sxs-lookup"><span data-stu-id="93142-142">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="93142-143">De waarden in het module manifest worden weer spie geld in de waarden van eigenschappen van het module-object.</span><span class="sxs-lookup"><span data-stu-id="93142-143">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="93142-144">De `Get-Module` cmdlet wordt gebruikt om de module **micro soft. Power shell. Diagnostics** te verkrijgen met de para meter **List** .</span><span class="sxs-lookup"><span data-stu-id="93142-144">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="93142-145">De opdracht verzendt de module naar de `Format-List` cmdlet om alle eigenschappen en waarden van het module-object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="93142-145">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

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

## <span data-ttu-id="93142-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93142-146">PARAMETERS</span></span>

### <span data-ttu-id="93142-147">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="93142-147">-AliasesToExport</span></span>

<span data-ttu-id="93142-148">Hiermee geeft u de aliassen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="93142-148">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="93142-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="93142-149">Wildcards are permitted.</span></span>

<span data-ttu-id="93142-150">U kunt deze para meter gebruiken om de aliassen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-150">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="93142-151">Het kan aliassen verwijderen uit de lijst met geëxporteerde aliassen, maar kan geen aliassen toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="93142-151">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="93142-152">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **AliasesToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle aliassen die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-152">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="93142-153">-Author</span><span class="sxs-lookup"><span data-stu-id="93142-153">-Author</span></span>

<span data-ttu-id="93142-154">Hiermee geeft u de auteur van de module.</span><span class="sxs-lookup"><span data-stu-id="93142-154">Specifies the module author.</span></span>

<span data-ttu-id="93142-155">Als u deze para meter weglaat, `New-ModuleManifest` wordt een **auteurs** sleutel gemaakt met de naam van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="93142-155">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

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

### <span data-ttu-id="93142-156">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="93142-156">-CmdletsToExport</span></span>

<span data-ttu-id="93142-157">Hiermee geeft u de cmdlets op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="93142-157">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="93142-158">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="93142-158">Wildcards are permitted.</span></span>

<span data-ttu-id="93142-159">U kunt deze para meter gebruiken om de cmdlets te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-159">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="93142-160">Hiermee kunnen cmdlets worden verwijderd uit de lijst met geëxporteerde cmdlets, maar kunnen geen cmdlets worden toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="93142-160">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="93142-161">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **CmdletsToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle cmdlets die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-161">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="93142-162">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="93142-162">-CompanyName</span></span>

<span data-ttu-id="93142-163">Identificeert het bedrijf of de leverancier die de module heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="93142-163">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="93142-164">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een sleutel van de **bedrijf** met de waarde ' Unknown '.</span><span class="sxs-lookup"><span data-stu-id="93142-164">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

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

### <span data-ttu-id="93142-165">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="93142-165">-CompatiblePSEditions</span></span>

<span data-ttu-id="93142-166">Hiermee geeft u de compatibele PSEditions van de module op.</span><span class="sxs-lookup"><span data-stu-id="93142-166">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="93142-167">Zie [modules met compatibele Power shell-edities](/powershell/scripting/gallery/concepts/module-psedition-support)voor meer informatie over PSEdition.</span><span class="sxs-lookup"><span data-stu-id="93142-167">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="93142-168">-Copyright</span><span class="sxs-lookup"><span data-stu-id="93142-168">-Copyright</span></span>

<span data-ttu-id="93142-169">Hiermee geeft u een copyright verklaring voor de module op.</span><span class="sxs-lookup"><span data-stu-id="93142-169">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="93142-170">Als u deze para meter weglaat, `New-ModuleManifest` maakt een **copyright** sleutel met `(c) <year> <username>. All rights reserved.` de waarde waar `<year>` het huidige jaar is en `<username>` is de waarde van de sleutel **Auteur** .</span><span class="sxs-lookup"><span data-stu-id="93142-170">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

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

### <span data-ttu-id="93142-171">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="93142-171">-DefaultCommandPrefix</span></span>

<span data-ttu-id="93142-172">Hiermee geeft u een voor voegsel op dat wordt geplaatst voor de naam woorden van alle opdrachten in de module wanneer deze in een sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-172">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="93142-173">Voer een voorvoegsel teken reeks in.</span><span class="sxs-lookup"><span data-stu-id="93142-173">Enter a prefix string.</span></span> <span data-ttu-id="93142-174">Voor voegsels voor komen conflicten met opdracht namen in de sessie van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="93142-174">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="93142-175">Module gebruikers kunnen dit voor voegsel overschrijven door de para meter **voor het voor voegsel** van de cmdlet op te geven `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="93142-175">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="93142-176">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="93142-176">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="93142-177">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="93142-177">-Description</span></span>

<span data-ttu-id="93142-178">Beschrijft de inhoud van de module.</span><span class="sxs-lookup"><span data-stu-id="93142-178">Describes the contents of the module.</span></span>

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

### <span data-ttu-id="93142-179">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="93142-179">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="93142-180">Hiermee geeft u de minimale versie van het Microsoft .NET Framework op dat voor de module nodig is.</span><span class="sxs-lookup"><span data-stu-id="93142-180">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="93142-181">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="93142-181">-DscResourcesToExport</span></span>

<span data-ttu-id="93142-182">Hiermee geeft u de resources voor desired state Configuration (DSC) op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="93142-182">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="93142-183">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="93142-183">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="93142-184">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="93142-184">-ExternalModuleDependencies</span></span>

<span data-ttu-id="93142-185">Een lijst met externe modules waarvan deze module afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="93142-185">A list of external modules that this module is depends on.</span></span>

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

### <span data-ttu-id="93142-186">-File List</span><span class="sxs-lookup"><span data-stu-id="93142-186">-FileList</span></span>

<span data-ttu-id="93142-187">Hiermee geeft u alle items die zijn opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="93142-187">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="93142-188">Deze sleutel is ontworpen om te fungeren als een module-inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="93142-188">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="93142-189">De bestanden die in de sleutel worden vermeld, worden opgenomen als de module wordt gepubliceerd, maar alle functies worden niet automatisch geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-189">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

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

### <span data-ttu-id="93142-190">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="93142-190">-FormatsToProcess</span></span>

<span data-ttu-id="93142-191">Hiermee geeft u de indelings bestanden ( `.ps1xml` ) op die worden uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-191">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="93142-192">Wanneer u een module importeert, voert Power shell de `Update-FormatData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="93142-192">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="93142-193">Omdat de indelings bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="93142-193">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="93142-194">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="93142-194">-FunctionsToExport</span></span>

<span data-ttu-id="93142-195">Hiermee geeft u de functies op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="93142-195">Specifies the functions that the module exports.</span></span> <span data-ttu-id="93142-196">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="93142-196">Wildcards are permitted.</span></span>

<span data-ttu-id="93142-197">U kunt deze para meter gebruiken om de functies te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-197">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="93142-198">De functie kan functies uit de lijst geëxporteerde aliassen verwijderen, maar kan geen functies toevoegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="93142-198">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="93142-199">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **FunctionsToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle functies die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-199">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="93142-200">-GUID</span><span class="sxs-lookup"><span data-stu-id="93142-200">-Guid</span></span>

<span data-ttu-id="93142-201">Hiermee geeft u een unieke id op voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-201">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="93142-202">De **GUID** kan worden gebruikt om onderscheid te maken tussen modules met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="93142-202">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="93142-203">Als u deze para meter weglaat, `New-ModuleManifest` wordt een **GUID** -sleutel gemaakt in het manifest en wordt een **GUID** voor de waarde gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="93142-203">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="93142-204">Als u een nieuwe **GUID** wilt maken in Power shell, typt u `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="93142-204">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

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

### <span data-ttu-id="93142-205">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="93142-205">-HelpInfoUri</span></span>

<span data-ttu-id="93142-206">Hiermee geeft u het Internet adres op van het HelpInfo XML-bestand voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-206">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="93142-207">Voer een URI (Uniform Resource Identifier) in die begint met **http** of **https**.</span><span class="sxs-lookup"><span data-stu-id="93142-207">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="93142-208">Het XML-bestand HelpInfo ondersteunt de bijwerk bare Help-functie die is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="93142-208">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="93142-209">Het bevat informatie over de locatie van de Download bare Help bestanden voor de module en de versie nummers van de nieuwste Help-bestanden voor elke ondersteunde land instelling.</span><span class="sxs-lookup"><span data-stu-id="93142-209">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="93142-210">Zie [about_Updatable_Help](./About/about_Updatable_Help.md)voor meer informatie over de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="93142-210">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="93142-211">Zie voor meer informatie over het HelpInfo XML-bestand [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="93142-211">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="93142-212">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="93142-212">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="93142-213">-IconUri</span><span class="sxs-lookup"><span data-stu-id="93142-213">-IconUri</span></span>

<span data-ttu-id="93142-214">Hiermee geeft u de URL op van een pictogram voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-214">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="93142-215">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-215">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="93142-216">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="93142-216">-LicenseUri</span></span>

<span data-ttu-id="93142-217">Hiermee geeft u de URL op van de licentie voorwaarden voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-217">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="93142-218">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="93142-218">-ModuleList</span></span>

<span data-ttu-id="93142-219">Een lijst met alle modules die in deze module zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="93142-219">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="93142-220">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="93142-220">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="93142-221">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="93142-221">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="93142-222">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="93142-222">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="93142-223">Deze sleutel is ontworpen om te fungeren als een module-inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="93142-223">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="93142-224">De modules die in de waarde van deze sleutel worden vermeld, worden niet automatisch verwerkt.</span><span class="sxs-lookup"><span data-stu-id="93142-224">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="93142-225">-ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="93142-225">-ModuleVersion</span></span>

<span data-ttu-id="93142-226">Hiermee geeft u de versie van de module.</span><span class="sxs-lookup"><span data-stu-id="93142-226">Specifies the module's version.</span></span>

<span data-ttu-id="93142-227">Deze para meter is niet vereist, maar er is een **ModuleVersion** -sleutel vereist in het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-227">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="93142-228">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **ModuleVersion** -sleutel met de waarde 1,0.</span><span class="sxs-lookup"><span data-stu-id="93142-228">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

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

### <span data-ttu-id="93142-229">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="93142-229">-NestedModules</span></span>

<span data-ttu-id="93142-230">Hiermee geeft u script modules ( `.psm1` ) en binaire modules ( `.dll` ) op die worden geïmporteerd in de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="93142-230">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="93142-231">De bestanden in de **NestedModules** -sleutel worden uitgevoerd in de volg orde waarin ze worden weer gegeven in de waarde.</span><span class="sxs-lookup"><span data-stu-id="93142-231">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="93142-232">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="93142-232">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="93142-233">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="93142-233">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="93142-234">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="93142-234">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="93142-235">Normaal gesp roken bevatten geneste modules opdrachten die de hoofd module nodig heeft voor de interne verwerking.</span><span class="sxs-lookup"><span data-stu-id="93142-235">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="93142-236">Standaard worden de opdrachten in geneste modules geëxporteerd van de sessie status van de module naar de sessie status van de beller, maar de hoofd module kan de opdrachten die worden geëxporteerd, beperken.</span><span class="sxs-lookup"><span data-stu-id="93142-236">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="93142-237">Bijvoorbeeld met behulp van een `Export-ModuleMember` opdracht.</span><span class="sxs-lookup"><span data-stu-id="93142-237">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="93142-238">Geneste modules in de module sessie status zijn beschikbaar voor de hoofd module, maar ze worden niet geretourneerd door een `Get-Module` opdracht in de sessie status van de beller.</span><span class="sxs-lookup"><span data-stu-id="93142-238">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="93142-239">Scripts ( `.ps1` ) die worden vermeld in de sleutel **NestedModules** , worden uitgevoerd in de sessie status van de module, niet in de sessie status van de beller.</span><span class="sxs-lookup"><span data-stu-id="93142-239">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="93142-240">Als u een script wilt uitvoeren in de sessie status van de aanroeper, vermeldt u de naam van het script bestand in de waarde van de sleutel **ScriptsToProcess** in het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-240">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

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

### <span data-ttu-id="93142-241">-PassThru</span><span class="sxs-lookup"><span data-stu-id="93142-241">-PassThru</span></span>

<span data-ttu-id="93142-242">Hiermee schrijft u het resulterende module manifest naar de-console en maakt u een `.psd1` bestand.</span><span class="sxs-lookup"><span data-stu-id="93142-242">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="93142-243">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="93142-243">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="93142-244">-Path</span><span class="sxs-lookup"><span data-stu-id="93142-244">-Path</span></span>

<span data-ttu-id="93142-245">Hiermee geeft u het pad en de bestands naam van het nieuwe module manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-245">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="93142-246">Voer een pad en een bestands naam in met een `.psd1` bestands extensie, zoals `$pshome\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="93142-246">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="93142-247">De para meter **Path** is vereist.</span><span class="sxs-lookup"><span data-stu-id="93142-247">The **Path** parameter is required.</span></span>

<span data-ttu-id="93142-248">Als u het pad naar een bestaand bestand opgeeft, wordt `New-ModuleManifest` het bestand vervangen zonder waarschuwing tenzij het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="93142-248">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="93142-249">Het manifest moet zich in de map van de module bevinden en de naam van het manifest bestand moet hetzelfde zijn als de naam van de module directory, maar met een `.psd1` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="93142-249">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="93142-250">U kunt geen variabelen, zoals `$PSHOME` of, gebruiken als `$HOME` antwoord op een prompt voor een **pad** parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="93142-250">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="93142-251">Als u een variabele wilt gebruiken, neemt u de para meter **Path** op in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="93142-251">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="93142-252">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="93142-252">-PowerShellHostName</span></span>

<span data-ttu-id="93142-253">Hiermee geeft u de naam op van het Power shell-hostprogramma dat is vereist voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-253">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="93142-254">Voer de naam van het hostprogramma in, zoals **Windows PowerShell ISE host** of **ConsoleHost**.</span><span class="sxs-lookup"><span data-stu-id="93142-254">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="93142-255">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="93142-255">Wildcards aren't permitted.</span></span>

<span data-ttu-id="93142-256">Als u de naam van een hostprogramma wilt zoeken, typt u in het programma `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="93142-256">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="93142-257">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="93142-257">-PowerShellHostVersion</span></span>

<span data-ttu-id="93142-258">Hiermee geeft u de minimale versie van het Power shell-hostprogramma op dat met de module werkt.</span><span class="sxs-lookup"><span data-stu-id="93142-258">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="93142-259">Voer een versie nummer in, bijvoorbeeld 1,1.</span><span class="sxs-lookup"><span data-stu-id="93142-259">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="93142-260">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="93142-260">-PowerShellVersion</span></span>

<span data-ttu-id="93142-261">Hiermee geeft u de minimale versie van Power shell op die met deze module werkt.</span><span class="sxs-lookup"><span data-stu-id="93142-261">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="93142-262">U kunt bijvoorbeeld 1,0, 2,0 of 3,0 invoeren als waarde voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="93142-262">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span>

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

### <span data-ttu-id="93142-263">-Prerelease</span><span class="sxs-lookup"><span data-stu-id="93142-263">-Prerelease</span></span>

<span data-ttu-id="93142-264">De teken reeks voor de voorlopige versie van deze module.</span><span class="sxs-lookup"><span data-stu-id="93142-264">Prerelease string of this module.</span></span> <span data-ttu-id="93142-265">Als u een prerelease-teken reeks toevoegt, wordt de module geïdentificeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="93142-265">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="93142-266">Wanneer de module is gepubliceerd naar de PowerShell Gallery, worden deze gegevens gebruikt om voorlopige pakketten te identificeren.</span><span class="sxs-lookup"><span data-stu-id="93142-266">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="93142-267">Als u voorlopige pakketten wilt ophalen uit de galerie, moet u de para meter **AllowPrerelease** gebruiken met de PowerShellGet-opdrachten `Find-Module` ,, `Install-Module` `Update-Module` en `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="93142-267">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

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

### <span data-ttu-id="93142-268">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="93142-268">-PrivateData</span></span>

<span data-ttu-id="93142-269">Hiermee geeft u de gegevens op die worden door gegeven aan de module wanneer deze wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-269">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="93142-270">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="93142-270">-ProcessorArchitecture</span></span>

<span data-ttu-id="93142-271">Hiermee geeft u de processor architectuur op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="93142-271">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="93142-272">Geldige waarden zijn x86, AMD64, IA64, MSIL en geen (onbekend of niet opgegeven).</span><span class="sxs-lookup"><span data-stu-id="93142-272">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

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

### <span data-ttu-id="93142-273">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="93142-273">-ProjectUri</span></span>

<span data-ttu-id="93142-274">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="93142-274">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="93142-275">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="93142-275">-ReleaseNotes</span></span>

<span data-ttu-id="93142-276">Geeft opmerkingen bij de release.</span><span class="sxs-lookup"><span data-stu-id="93142-276">Specifies release notes.</span></span>

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

### <span data-ttu-id="93142-277">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="93142-277">-RequiredAssemblies</span></span>

<span data-ttu-id="93142-278">Hiermee geeft u de assembly ( `.dll` )-bestanden op die de module vereist.</span><span class="sxs-lookup"><span data-stu-id="93142-278">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="93142-279">Voer de namen van de assembly bestanden in.</span><span class="sxs-lookup"><span data-stu-id="93142-279">Enter the assembly file names.</span></span>
<span data-ttu-id="93142-280">Power shell laadt de opgegeven assembly's vóór het bijwerken van typen of indelingen, het importeren van geneste modules of het importeren van het module bestand dat is opgegeven in de waarde van de sleutel **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="93142-280">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="93142-281">Gebruik deze para meter om alle assembly's weer te geven die voor de module vereist zijn, inclusief de assembly's die moeten worden geladen voor het bijwerken van de opmaak of het type van bestanden die worden vermeld in de sleutels **FormatsToProcess** of **TypesToProcess** , zelfs als deze assembly's ook worden vermeld als binaire modules in de **NestedModules** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="93142-281">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="93142-282">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="93142-282">-RequiredModules</span></span>

<span data-ttu-id="93142-283">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="93142-283">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="93142-284">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-284">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="93142-285">Als de vereiste modules niet beschikbaar zijn, `Import-Module` mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="93142-285">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="93142-286">Voer elke module naam in als een teken reeks of als een hash- **tabel met de** **ModuleVersion** -sleutels.</span><span class="sxs-lookup"><span data-stu-id="93142-286">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="93142-287">De hash-tabel kan ook een optionele **GUID** -sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="93142-287">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="93142-288">U kunt teken reeksen en hash-tabellen combi neren in de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="93142-288">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="93142-289">In Power Shell 2,0 worden de `Import-Module` vereiste modules niet automatisch geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-289">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="93142-290">Er wordt alleen gecontroleerd of de vereiste modules zich in de status van de globale sessie bevinden.</span><span class="sxs-lookup"><span data-stu-id="93142-290">It just verifies that the required modules are in the global session state.</span></span>

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

### <span data-ttu-id="93142-291">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="93142-291">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="93142-292">Markering om aan te geven of voor de module expliciete gebruikers acceptatie is vereist voor install, update, orsave.</span><span class="sxs-lookup"><span data-stu-id="93142-292">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

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

### <span data-ttu-id="93142-293">-RootModule</span><span class="sxs-lookup"><span data-stu-id="93142-293">-RootModule</span></span>

<span data-ttu-id="93142-294">Hiermee geeft u het primaire of hoofd bestand van de module op.</span><span class="sxs-lookup"><span data-stu-id="93142-294">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="93142-295">Voer de bestands naam van een script ( `.ps1` ), een script module ( `.psm1` ), een module manifest ( `.psd1` ), een assembly ( `.dll` ), een XML-bestand voor de cmdlet-definitie ( `.cdxml` ) of een werk stroom ( `.xaml` ) in.</span><span class="sxs-lookup"><span data-stu-id="93142-295">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="93142-296">Wanneer de module wordt geïmporteerd, worden de leden die worden geëxporteerd uit het hoofd module bestand geïmporteerd in de sessie status van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="93142-296">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="93142-297">Als een module een manifest bestand heeft en er geen hoofd bestand is opgegeven in de **RootModule** -sleutel, wordt het manifest het primaire bestand voor de module en wordt de module een manifest module (module type = manifest).</span><span class="sxs-lookup"><span data-stu-id="93142-297">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="93142-298">Als u leden wilt exporteren uit `.psm1` of `.dll` bestanden in een module met een manifest, moeten de namen van die bestanden worden opgegeven in de waarden van de sleutels **RootModule** of **NestedModules** in het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-298">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="93142-299">Anders worden de leden niet geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-299">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="93142-300">In Power Shell 2,0 is deze sleutel **ModuleToProcess** genoemd.</span><span class="sxs-lookup"><span data-stu-id="93142-300">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="93142-301">U kunt de parameter naam van de **RootModule** of de **ModuleToProcess** -alias gebruiken.</span><span class="sxs-lookup"><span data-stu-id="93142-301">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

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

### <span data-ttu-id="93142-302">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="93142-302">-ScriptsToProcess</span></span>

<span data-ttu-id="93142-303">Hiermee geeft u script ( `.ps1` )-bestanden op die worden uitgevoerd in de sessie status van de aanroeper wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-303">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="93142-304">U kunt deze scripts gebruiken om een omgeving voor te bereiden, net zoals u een aanmeldings script zou kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="93142-304">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="93142-305">Als u scripts wilt opgeven die worden uitgevoerd in de sessie status van de module, gebruikt u de sleutel **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="93142-305">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="93142-306">-Tags</span><span class="sxs-lookup"><span data-stu-id="93142-306">-Tags</span></span>

<span data-ttu-id="93142-307">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="93142-307">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="93142-308">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="93142-308">-TypesToProcess</span></span>

<span data-ttu-id="93142-309">Hiermee geeft u het type bestanden ( `.ps1xml` ) op dat wordt uitgevoerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-309">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="93142-310">Wanneer u de module importeert, voert Power shell de `Update-TypeData` cmdlet uit met de opgegeven bestanden.</span><span class="sxs-lookup"><span data-stu-id="93142-310">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="93142-311">Omdat type bestanden geen bereik hebben, hebben ze invloed op alle sessie statussen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="93142-311">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="93142-312">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="93142-312">-VariablesToExport</span></span>

<span data-ttu-id="93142-313">Hiermee geeft u de variabelen op die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="93142-313">Specifies the variables that the module exports.</span></span> <span data-ttu-id="93142-314">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="93142-314">Wildcards are permitted.</span></span>

<span data-ttu-id="93142-315">U kunt deze para meter gebruiken om de variabelen te beperken die door de module worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-315">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="93142-316">Hiermee kunnen variabelen worden verwijderd uit de lijst met geëxporteerde variabelen, maar er kunnen geen variabelen worden toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="93142-316">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="93142-317">Als u deze para meter weglaat, `New-ModuleManifest` maakt u een **VariablesToExport** -sleutel met de waarde `*` (alle), wat betekent dat alle variabelen die in de module zijn gedefinieerd, worden geëxporteerd door het manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-317">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

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

### <span data-ttu-id="93142-318">-Confirm</span><span class="sxs-lookup"><span data-stu-id="93142-318">-Confirm</span></span>

<span data-ttu-id="93142-319">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="93142-319">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="93142-320">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="93142-320">-WhatIf</span></span>

<span data-ttu-id="93142-321">Hier wordt weer gegeven wat er gebeurt als er `New-ModuleManifest` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="93142-321">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="93142-322">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="93142-322">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="93142-323">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="93142-323">-ClrVersion</span></span>

<span data-ttu-id="93142-324">Hiermee geeft u de minimale versie van common language runtime (CLR) op van het Microsoft .NET Framework dat vereist is voor de module.</span><span class="sxs-lookup"><span data-stu-id="93142-324">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="93142-325">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93142-325">CommonParameters</span></span>
<span data-ttu-id="93142-326">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="93142-326">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93142-327">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="93142-327">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="93142-328">INVOER</span><span class="sxs-lookup"><span data-stu-id="93142-328">INPUTS</span></span>

### <span data-ttu-id="93142-329">Geen</span><span class="sxs-lookup"><span data-stu-id="93142-329">None</span></span>

<span data-ttu-id="93142-330">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="93142-330">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="93142-331">UITVOER</span><span class="sxs-lookup"><span data-stu-id="93142-331">OUTPUTS</span></span>

### <span data-ttu-id="93142-332">Geen of System. String</span><span class="sxs-lookup"><span data-stu-id="93142-332">None or System.String</span></span>

<span data-ttu-id="93142-333">Standaard genereert geen `New-ModuleManifest` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="93142-333">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="93142-334">Als u echter de para meter **PassThru** gebruikt, wordt er een **System. String** -object gegenereerd dat het module manifest vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="93142-334">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="93142-335">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="93142-335">NOTES</span></span>

<span data-ttu-id="93142-336">`New-ModuleManifest` Als u werkt met Windows-en niet-Windows-platforms, worden module manifest- `.psd1` bestanden gemaakt die zijn gecodeerd als **UTF8NoBOM**.</span><span class="sxs-lookup"><span data-stu-id="93142-336">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="93142-337">Module manifesten zijn meestal optioneel.</span><span class="sxs-lookup"><span data-stu-id="93142-337">Module manifests are usually optional.</span></span> <span data-ttu-id="93142-338">Er is echter een module manifest vereist voor het exporteren van een assembly die is geïnstalleerd in de Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="93142-338">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="93142-339">Als u bestanden in de map wilt toevoegen of wijzigen `$pshome\Modules` , start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="93142-339">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="93142-340">Vanaf Power shell 6,2 probeert Power shell alle DLL-bestanden te laden die worden vermeld in de eigenschap **File List** van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-340">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="93142-341">Systeem eigen Dll's bevindt zich in de **Bestands List** en worden niet geladen in het proces en de fout wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="93142-341">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="93142-342">Alle beheerde dll-bestanden worden in het proces geladen.</span><span class="sxs-lookup"><span data-stu-id="93142-342">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="93142-343">Dit gedrag is verwijderd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="93142-343">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="93142-344">In Power Shell 2,0 zijn veel para meters van `New-ModuleManifest` verplicht, ook al zijn ze niet vereist in een module manifest.</span><span class="sxs-lookup"><span data-stu-id="93142-344">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="93142-345">Vanaf Power Shell 3,0 is alleen de para meter **Path** verplicht.</span><span class="sxs-lookup"><span data-stu-id="93142-345">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="93142-346">Een sessie is een exemplaar van de Power shell-uitvoerings omgeving.</span><span class="sxs-lookup"><span data-stu-id="93142-346">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="93142-347">Een sessie kan een of meer sessie statussen hebben.</span><span class="sxs-lookup"><span data-stu-id="93142-347">A session can have one or more session states.</span></span> <span data-ttu-id="93142-348">Een sessie heeft standaard alleen een algemene sessie status, maar elke geïmporteerde module heeft een eigen sessie status.</span><span class="sxs-lookup"><span data-stu-id="93142-348">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="93142-349">Met sessie status kunnen de opdrachten in een module worden uitgevoerd zonder dat dit van invloed is op de globale sessie status.</span><span class="sxs-lookup"><span data-stu-id="93142-349">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="93142-350">De sessie status van de oproepende functie is de sessie status waarin een module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="93142-350">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="93142-351">Normaal gesp roken verwijst deze naar de status van de globale sessie, maar wanneer een module geneste modules importeert, is de aanroeper de module en de sessie status van de beller is de sessie status van de module.</span><span class="sxs-lookup"><span data-stu-id="93142-351">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="93142-352">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="93142-352">RELATED LINKS</span></span>

[<span data-ttu-id="93142-353">Exporteren-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="93142-353">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="93142-354">Get-module</span><span class="sxs-lookup"><span data-stu-id="93142-354">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="93142-355">Import-module</span><span class="sxs-lookup"><span data-stu-id="93142-355">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="93142-356">New-module</span><span class="sxs-lookup"><span data-stu-id="93142-356">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="93142-357">Remove-module</span><span class="sxs-lookup"><span data-stu-id="93142-357">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="93142-358">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="93142-358">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="93142-359">about_Modules</span><span class="sxs-lookup"><span data-stu-id="93142-359">about_Modules</span></span>](./About/about_Modules.md)
