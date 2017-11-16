---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Zoeken naar DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="find-dscresource"></a><span data-ttu-id="ee35b-103">Zoeken naar DscResource</span><span class="sxs-lookup"><span data-stu-id="ee35b-103">Find-DscResource</span></span>

<span data-ttu-id="ee35b-104">Zoekt DSC-Resources in modules.</span><span class="sxs-lookup"><span data-stu-id="ee35b-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="ee35b-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ee35b-105">Description</span></span>

<span data-ttu-id="ee35b-106">De cmdlet zoeken DscResource vindt [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) bronnen die zich bevinden in de modules die overeenkomen met de opgegeven criteria uit geregistreerde opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ee35b-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="ee35b-107">Voor elke module die deze cmdlet wordt gevonden, retourneert zoeken DscResource een PSGetDscResourceInfo-object dat u kunt doorsluizen naar installatie-Module voor het installeren van de modules die met de resources die deze cmdlet retourneert.</span><span class="sxs-lookup"><span data-stu-id="ee35b-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="ee35b-108">DSC is een nieuw management-platform in Windows PowerShell waarmee implementeren en beheren van configuratiegegevens voor de, softwareservices en beheren van de omgeving waarin deze services worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ee35b-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="ee35b-109">Desired dat State Configuration (DSC) bronnen vindt u de bouwstenen voor een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="ee35b-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="ee35b-110">Een bron beschrijft eigenschappen die kunnen worden geconfigureerd (schema) en bevat de functies van de PowerShell-script die de lokale Configuration Manager (LCM) ' om deze te maken zodat' aanroept.</span><span class="sxs-lookup"><span data-stu-id="ee35b-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="ee35b-111">Een resource kan iets als algemene als een bestand of de instelling van een IIS-server zo specifiek model.</span><span class="sxs-lookup"><span data-stu-id="ee35b-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="ee35b-112">Groepen van zoals bronnen worden gecombineerd in naar een DSC-Module, waarbij alle vereiste bestanden in een structuur die overdraagbaar en bevat metagegevens om te bepalen hoe de resources zijn bedoeld om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ee35b-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="ee35b-113">Zoeken naar DscResource kunt filteren met Versieparameters: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="ee35b-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="ee35b-114">Deze parameters elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="ee35b-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="ee35b-115">Deze Versieparameters zijn alleen met de naam van de één module zonder eventuele jokertekens toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ee35b-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="ee35b-116">Als de parameter RequiredVersion niet is opgegeven, retourneert zoeken DscResource de nieuwste versie van de module die gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van de module als er geen minimum versie is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ee35b-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="ee35b-117">Als de parameter RequiredVersion is opgegeven, retourneert zoeken DscResource alleen de versie van de module die exact overeenkomt met de opgegeven versie.</span><span class="sxs-lookup"><span data-stu-id="ee35b-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="ee35b-118">Zoeken naar DscResource kunt filteren op de metagegevens van de module met de - parameter van label</span><span class="sxs-lookup"><span data-stu-id="ee35b-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="ee35b-119">Zoeken naar DscResource kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter.</span><span class="sxs-lookup"><span data-stu-id="ee35b-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="ee35b-120">Zoeken naar DscResource kunt filteren op modules van alle of enkele van de geregistreerde opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ee35b-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="ee35b-121">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="ee35b-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="ee35b-122">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="ee35b-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="ee35b-123">Zoeken naar DscResource</span><span class="sxs-lookup"><span data-stu-id="ee35b-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="ee35b-124">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="ee35b-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

