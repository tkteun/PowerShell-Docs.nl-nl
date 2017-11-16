---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Zoeken naar RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a><span data-ttu-id="05cce-103">Zoeken naar RoleCapability</span><span class="sxs-lookup"><span data-stu-id="05cce-103">Find-RoleCapability</span></span>

<span data-ttu-id="05cce-104">Hiermee zoekt rol mogelijkheden in modules.</span><span class="sxs-lookup"><span data-stu-id="05cce-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="05cce-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="05cce-105">Description</span></span>
<span data-ttu-id="05cce-106">De cmdlet zoeken RoleCapability zoekt PowerShell rol mogelijkheden in modules.</span><span class="sxs-lookup"><span data-stu-id="05cce-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="05cce-107">Modules zoekt zoeken RoleCapability in geregistreerde opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="05cce-107">Find-RoleCapability searches modules in registered repositories.</span></span> <span data-ttu-id="05cce-108">Voor de capaciteit van elke rol die deze cmdlet vindt, wordt een PSGetRoleCapabilityInfo-object.</span><span class="sxs-lookup"><span data-stu-id="05cce-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="05cce-109">U kunt een PSGetRoleCapabilityInfo-object doorgeven aan de cmdlet Install-Module voor het installeren van de module met de mogelijkheid van de rol.</span><span class="sxs-lookup"><span data-stu-id="05cce-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="05cce-110">PowerShell rol mogelijkheden definiëren die opdrachten, toepassingen, enzovoort beschikbaar zijn voor een gebruiker op een eindpunt net genoeg Administration (JEA).</span><span class="sxs-lookup"><span data-stu-id="05cce-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="05cce-111">Rol mogelijkheden worden gedefinieerd door de bestanden met de extensie .psrc.</span><span class="sxs-lookup"><span data-stu-id="05cce-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="05cce-112">Zoeken naar RoleCapability kunt filteren met Versieparameters: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="05cce-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="05cce-113">Deze parameters elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="05cce-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="05cce-114">Deze Versieparameters zijn alleen met de naam van de één module zonder eventuele jokertekens toegestaan.</span><span class="sxs-lookup"><span data-stu-id="05cce-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="05cce-115">Als de parameter RequiredVersion niet is opgegeven, retourneert zoeken RoleCapability de nieuwste versie van de module die gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van de module als er geen minimum versie is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="05cce-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="05cce-116">Als de parameter RequiredVersion is opgegeven, retourneert zoeken RoleCapability alleen de versie van de module die exact overeenkomt met de opgegeven versie.</span><span class="sxs-lookup"><span data-stu-id="05cce-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="05cce-117">Zoeken naar RoleCapability kunt filteren op de metagegevens van de module met de - parameter van label</span><span class="sxs-lookup"><span data-stu-id="05cce-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="05cce-118">Zoeken naar RoleCapability kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter.</span><span class="sxs-lookup"><span data-stu-id="05cce-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="05cce-119">Zoeken naar RoleCapability kunt filteren op modules van alle of enkele van de geregistreerde opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="05cce-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="05cce-120">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="05cce-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="05cce-121">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="05cce-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="05cce-122">Zoeken naar RoleCapability</span><span class="sxs-lookup"><span data-stu-id="05cce-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="05cce-123">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="05cce-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

