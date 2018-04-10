---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Find-Module
ms.openlocfilehash: 03dff4454a31638df564568ef51eec158685c8e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="find-module"></a><span data-ttu-id="a99e9-103">Find-Module</span><span class="sxs-lookup"><span data-stu-id="a99e9-103">Find-Module</span></span>
<span data-ttu-id="a99e9-104">Zoeken naar modules vanuit een online-galerie die voldoen aan opgegeven criteria.</span><span class="sxs-lookup"><span data-stu-id="a99e9-104">Finds modules from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="a99e9-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a99e9-105">Description</span></span>
<span data-ttu-id="a99e9-106">Zoeken naar Module detecteert de modules uit geregistreerde opslagplaatsen die overeenkomt met de opgegeven criteria.</span><span class="sxs-lookup"><span data-stu-id="a99e9-106">Find-Module discovers the modules from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="a99e9-107">Voor elke module die wordt gevonden, retourneert Find-Module een PSRepositoryItemInfo-object dat kan eventueel worden doorgesluisd naar installatie-Module voor het installeren van de modules.</span><span class="sxs-lookup"><span data-stu-id="a99e9-107">For each module found, Find-Module returns a PSRepositoryItemInfo object which can optionally be piped to Install-Module for installing the modules.</span></span>

- <span data-ttu-id="a99e9-108">Zoek-Module kunt filteren op basis van de module met-opdracht - DscResource, - RoleCapability inhoud en - parameters bevat.</span><span class="sxs-lookup"><span data-stu-id="a99e9-108">Find-Module can filter based on module contents with the -Command, -DscResource, -RoleCapability and -Includes parameters.</span></span>
- <span data-ttu-id="a99e9-109">Zoek-Module kunt filteren met Versieparameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="a99e9-109">Find-Module can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="a99e9-110">Deze parameters zijn, met uitzondering van MinmimumVersion en MaximumVersion, sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="a99e9-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="a99e9-111">Deze Versieparameters zijn alleen met de naam van de één module zonder eventuele jokertekens toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a99e9-111">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="a99e9-112">Als de parameter RequiredVersion niet is opgegeven, retourneert Find-Module de nieuwste versie van de module die gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van de module als er geen minimum versie is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a99e9-112">If the RequiredVersion parameter is not specified, Find-Module returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="a99e9-113">Als de parameter RequiredVersion is opgegeven, retourneert Find-Module alleen de versie van de module die exact overeenkomt met de opgegeven versie.</span><span class="sxs-lookup"><span data-stu-id="a99e9-113">If the RequiredVersion parameter is specified, Find-Module only returns the version of module that exactly matches the specified version.</span></span>
- <span data-ttu-id="a99e9-114">Zoek-Module kunt filteren op de metagegevens van de module met de - parameter van label</span><span class="sxs-lookup"><span data-stu-id="a99e9-114">Find-Module can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="a99e9-115">Zoek-Module kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter.</span><span class="sxs-lookup"><span data-stu-id="a99e9-115">Find-Module can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="a99e9-116">Zoek-Module kunt filteren op modules van alle of enkele van de geregistreerde opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a99e9-116">Find-Module can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a99e9-117">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="a99e9-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a99e9-118">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="a99e9-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="a99e9-119">Find-Module</span><span class="sxs-lookup"><span data-stu-id="a99e9-119">Find-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a><span data-ttu-id="a99e9-120">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="a99e9-120">Example commands</span></span>
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion.
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module with a specific prerelease version
Find-Module -Name AzureRM -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```