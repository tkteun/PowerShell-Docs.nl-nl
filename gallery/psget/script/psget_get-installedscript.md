---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedscript"></a><span data-ttu-id="e31f4-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="e31f4-103">Get-InstalledScript</span></span>

<span data-ttu-id="e31f4-104">Haalt geïnstalleerde scripts op een computer.</span><span class="sxs-lookup"><span data-stu-id="e31f4-104">Gets installed scripts on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="e31f4-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e31f4-105">Description</span></span>

<span data-ttu-id="e31f4-106">De cmdlet Get-InstalledScript haalt geïnstalleerde PowerShell-scripts op een computer.</span><span class="sxs-lookup"><span data-stu-id="e31f4-106">The Get-InstalledScript cmdlet gets installed PowerShell scripts on a computer.</span></span>

<span data-ttu-id="e31f4-107">Voor elke geïnstalleerde script retourneert Get-InstalledScript een PSRepositoryItemInfo-object dat kan eventueel worden doorgesluisd naar Uninstall-Script voor het verwijderen van de geïnstalleerde scripts.</span><span class="sxs-lookup"><span data-stu-id="e31f4-107">For each installed script, Get-InstalledScript returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Script for uninstalling the installed scripts.</span></span>

- <span data-ttu-id="e31f4-108">Get-InstalledScript kunt geïnstalleerde scripts op basis van naam, Versieparameters filteren.</span><span class="sxs-lookup"><span data-stu-id="e31f4-108">Get-InstalledScript can filter installed scripts based on name, version parameters.</span></span>
- <span data-ttu-id="e31f4-109">Get-InstalledScript kunt filteren met Versieparameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="e31f4-109">Get-InstalledScript can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="e31f4-110">Deze parameters zijn, met uitzondering van MinmimumVersion en MaximumVersion, sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="e31f4-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="e31f4-111">Deze Versieparameters zijn alleen met de naam van één script zonder eventuele jokertekens toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e31f4-111">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="e31f4-112">Als de parameter RequiredVersion niet is opgegeven, retourneert Get-InstalledScript de meest recente versie van het geïnstalleerde script dat gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van het script als er geen minimum versie is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e31f4-112">If the RequiredVersion parameter is not specified, Get-InstalledScript returns the latest version of the installed script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span> 
  - <span data-ttu-id="e31f4-113">Als de parameter RequiredVersion is opgegeven, wordt met Get-InstalledScript alleen de versie van geïnstalleerde script die exact overeenkomt met de opgegeven versie retourneert.</span><span class="sxs-lookup"><span data-stu-id="e31f4-113">If the RequiredVersion parameter is specified, Get-InstalledScript only returns the version of installed script that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="e31f4-114">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="e31f4-114">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="e31f4-115">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="e31f4-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="e31f4-116">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="e31f4-116">Get-InstalledScript</span></span>](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a><span data-ttu-id="e31f4-117">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="e31f4-117">Example commands</span></span>

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

