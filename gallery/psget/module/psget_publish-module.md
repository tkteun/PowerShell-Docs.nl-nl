---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Publiceren-Module
ms.openlocfilehash: 53fca3d6756ebf698023152ce5b58b45eb0ef757
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="publish-module"></a><span data-ttu-id="1b3b5-103">Publiceren-Module</span><span class="sxs-lookup"><span data-stu-id="1b3b5-103">Publish-Module</span></span>

<span data-ttu-id="1b3b5-104">Een opgegeven module uit de lokale computer aan een online galerie publiceert.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-104">Publishes a specified module from the local computer to an online gallery.</span></span>

## <a name="description"></a><span data-ttu-id="1b3b5-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1b3b5-105">Description</span></span>

<span data-ttu-id="1b3b5-106">De **publiceren-Module** cmdlet een module publiceert naar een online op basis van het NuGet-galerie met behulp van een API-sleutel opgeslagen als onderdeel van een gebruikersprofiel in de galerie.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-106">The **Publish-Module** cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="1b3b5-107">U kunt de module die u wilt publiceren met de naam van de module of door het pad naar de map met de module opgeven.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-107">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="1b3b5-108">Wanneer u een module met de naam opgeeft, **publiceren-Module** publiceert u de eerste module die zou worden gevonden door te voeren `Get-Module -ListAvailable <Name>`.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-108">When you specify a module by name, **Publish-Module** publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="1b3b5-109">Als u een minimale versie van een module die u wilt publiceren, opgeeft **publiceren-Module** publiceert u de eerste module met een versie die is groter dan of gelijk zijn aan de minimale versie die u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-109">If you specify a minimum version of a module to publish, **Publish-Module** publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="1b3b5-110">Publiceren van een module vereist metagegevens die wordt weergegeven op de galeriepagina voor de module.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-110">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="1b3b5-111">Vereiste metagegevens bevat de naam, versie, beschrijving en auteur.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-111">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="1b3b5-112">Hoewel de meeste metagegevens afkomstig is van de module-manifest, bepaalde metagegevens moet worden opgegeven in **publiceren-Module** parameters, zoals *label, ReleaseNote, IconUri, ProjectUri,* en  *LicenseUri*, omdat deze parameters overeenkomen met de velden in op basis van het NuGet-galerie.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-112">Although most metadata is taken from the module manifest, some metadata must be specified in **Publish-Module** parameters, such as *Tag, ReleaseNote, IconUri, ProjectUri,* and *LicenseUri*, because these parameters match fields in a NuGet-based gallery.</span></span>

<span data-ttu-id="1b3b5-113">De parameter RequiredVersion kunt u opgeven dat de exacte versie van een module moet worden gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-113">The RequiredVersion parameter allows you to specify the exact version of a module to be published.</span></span>
<span data-ttu-id="1b3b5-114">De parameter Path ondersteunt ook het basispad voor de module met de versie-map.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-114">The Path parameter also supports the module base path with the version folder.</span></span>
<span data-ttu-id="1b3b5-115">De parameter Force switch op de cmdlet Publish-Module bootstraps de NuGet.exe zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-115">The Force switch parameter on Publish-Module cmdlet bootstraps the NuGet.exe without prompting.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="1b3b5-116">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="1b3b5-116">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Publish-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="1b3b5-117">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="1b3b5-117">Cmdlet online help reference</span></span>

[<span data-ttu-id="1b3b5-118">Publiceren-Module</span><span class="sxs-lookup"><span data-stu-id="1b3b5-118">Publish-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398575)

## <a name="example-commands"></a><span data-ttu-id="1b3b5-119">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="1b3b5-119">Example commands</span></span>

```powershell
ContosoServer module with different versions to be published.
PS C:\\windows\\system32> Get-Module -Name ContosoServer -ListAvailable
Directory: C:\\Program Files\\WindowsPowerShell\\Modules
ModuleType Version Name ExportedCommands
---------- ------- ---- ----------------
Manifest 2.8 ContosoServer Get-ContosoServer
Manifest 2.0 ContosoServer Get-ContosoServer
Manifest 1.5 ContosoServer Get-ContosoServer
Manifest 1.0 ContosoServer Get-ContosoServer
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.0 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Name ContosoServer -RequiredVersion 1.5 -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
PS C:\\windows\\system32> Publish-Module -Path "C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0" -Repository LocalRepo -NuGetApiKey Local-Repo-NuGet-ApiKey
PS C:\\windows\\system32> Find-Module -Name ContosoServer -Repository LocalRepo
Version Name Repository Description
_------ ---- ---------- -----------
1.0 ContosoServer LocalRepo ContosoServer module
1.5 ContosoServer LocalRepo ContosoServer module
2.0 ContosoServer LocalRepo ContosoServer module
```

## <a name="publishing-a-module-with-dependencies"></a><span data-ttu-id="1b3b5-120">Publiceren van een module met afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="1b3b5-120">Publishing a module with dependencies</span></span>

### <a name="create-a-module-with-dependencies-and-version-range-specified-in-requiredmodules-property-of-its-module-manifest"></a><span data-ttu-id="1b3b5-121">Maakt een module met afhankelijkheden en bereik van de versie opgegeven in de eigenschap RequiredModules van de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-121">Create a module with dependencies and version range specified in RequiredModules property of its module manifest.</span></span>

<span data-ttu-id="1b3b5-122">**Opmerking:**</span><span class="sxs-lookup"><span data-stu-id="1b3b5-122">**Note:**</span></span>
  - <span data-ttu-id="1b3b5-123">\*wordt alleen ondersteund in MaximumVersion en ook moet aan het einde van de versietekenreeks.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-123">\* is supported only in MaximumVersion and also it should be at the end of version string.</span></span> 
  - <span data-ttu-id="1b3b5-124">\*vervangen door 999999999 in de version-object.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-124">\* is replaced with 999999999 in the version object.</span></span>

```powershell
PS C:\windows\system32> $requiredModules = @( @{ModuleName = 'RequiredModule1'; ModuleVersion = '0.1'; MaximumVersion = '1.9'; }, @{ModuleName = 'RequiredModule2'; MaximumVersion = '1.*'; })

PS C:\windows\system32> cd C:\MyModules\ModuleWithDependencies

PS C:\MyModules\ModuleWithDependencies> New-ModuleManifest -Path .\ModuleWithDependencies.psd1 -ModuleVersion 1.0 -RequiredModules $requiredModules -Description 'ModuleWithDependencies demo module'
```

### <a name="publish-modulewithdependencies-module-with-dependencies-to-the-repository"></a><span data-ttu-id="1b3b5-125">Module ModuleWithDependencies met afhankelijkheden publiceren naar de opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-125">Publish ModuleWithDependencies module with dependencies to the repository.</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Publish-Module -Path C:\MyModules\ModuleWithDependencies -Repository LocalRepo
```

### <a name="find-modulewithdependencies-module-with-its-dependencies-by-specifying--includedependencies"></a><span data-ttu-id="1b3b5-126">ModuleWithDependencies module met de bijbehorende afhankelijkheden vinden door op te geven - IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="1b3b5-126">Find ModuleWithDependencies module with its dependencies by specifying -IncludeDependencies</span></span>

```powershell
PS C:\MyModules\ModuleWithDependencies> Find-Module -Name ModuleWithDependencies -Repository LocalRepo -IncludeDependencies

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="install-the-modulewithdependencies-module-with-dependencies"></a><span data-ttu-id="1b3b5-127">De module ModuleWithDependencies met afhankelijkheden installeren.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-127">Install the ModuleWithDependencies module with dependencies.</span></span>
<span data-ttu-id="1b3b5-128">Houd er rekening mee dat versie bereiken worden gehonoreerd tijdens de installatie van de afhankelijkheid.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-128">Note that version ranges are honored during the dependency installation.</span></span>

```powershell
PS C:\windows\system32> Get-InstalledModule
PS C:\windows\system32>
PS C:\windows\system32> Install-Module -Name ModuleWithDependencies -Repository LocalRepo
PS C:\windows\system32>
PS C:\windows\system32> Get-InstalledModule

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        ModuleWithDependencies              Module     localrepo            ModuleWithDependencies demo module
1.5        RequiredModule1                     Module     localrepo            RequiredModule1 module
1.5        RequiredModule2                     Module     localrepo            RequiredModule2 module
```

### <a name="contents-of-modulewithdependencies2-module-manifest-file"></a><span data-ttu-id="1b3b5-129">Inhoud van de module ModuleWithDependencies2-manifestbestand</span><span class="sxs-lookup"><span data-stu-id="1b3b5-129">Contents of ModuleWithDependencies2 module manifest file</span></span>

```powershell
@{
# Version number of this module.
ModuleVersion = '2.0'
# ID used to uniquely identify this module
GUID = '0eae34da-99dd-4608-8d28-c614fe7b0841'
# Author of this module
Author = 'manikb'
# Company or vendor of this module
CompanyName = 'Unknown'
# Copyright statement for this module
Copyright = '(c) 2015 manikb. All rights reserved.'
# Description of the functionality provided by this module
Description = 'ModuleWithDependencies2 module'
# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @('RequiredModule1',
@{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'RequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'RequiredModule4'; ModuleVersion = '1.1'; MaximumVersion = '2.0'; },
@{ModuleName = 'RequiredModule5'; MaximumVersion = '1.5'; })
# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @('NestedRequiredModule1',
@{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '2.0'; },
@{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.5'; },
@{ModuleName = 'NestedRequiredModule4'; ModuleVersion = '0.7'; MaximumVersion = '2.4'; },
@{ModuleName = 'NestedRequiredModule5'; MaximumVersion = '1.6'; },'ModuleWithDependencies2.psm1')
# Functions to export from this module
FunctionsToExport = '\*'
# Cmdlets to export from this module
CmdletsToExport = '\*'
# Variables to export from this module
VariablesToExport = '\*'
# Aliases to export from this module
AliasesToExport = '\*'
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
      # Tags applied to this module. These help with module discovery in online galleries.
      Tags = 'Tag1', 'Tag2', 'Tag-ModuleWithDependencies2-2.0'
      # A URL to the license for this module.
      LicenseUri = 'http://modulewithdependencies2.com/license'
      # A URL to the main website for this project.
      ProjectUri = 'http://modulewithdependencies2.com/'
      # A URL to an icon representing this module.
      IconUri = 'http://modulewithdependencies2.com/icon'
      # ReleaseNotes of this module
      ReleaseNotes = 'ModuleWithDependencies2 release notes'
    } # End of PSData hashtable
} # End of PrivateData hashtable
}
```


### <a name="external-dependencies"></a><span data-ttu-id="1b3b5-130">Externe afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="1b3b5-130">External dependencies</span></span>
<span data-ttu-id="1b3b5-131">Enkele afhankelijkheden module extern kunnen worden beheerd, in dat geval ze moeten worden toegevoegd aan de vermelding ExternalModuleDependencies in de sectie PSData van de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-131">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>

<span data-ttu-id="1b3b5-132">Als 'SnippetPx' niet beschikbaar in de opslagplaats is, hieronder fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1b3b5-132">If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
```powershell
Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
```

