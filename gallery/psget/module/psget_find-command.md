---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Opdracht Zoeken
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a><span data-ttu-id="17c80-103">Opdracht Zoeken</span><span class="sxs-lookup"><span data-stu-id="17c80-103">Find-Command</span></span>

<span data-ttu-id="17c80-104">Hiermee zoekt PowerShell-opdrachten in modules.</span><span class="sxs-lookup"><span data-stu-id="17c80-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="17c80-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="17c80-105">Description</span></span>
<span data-ttu-id="17c80-106">De opdracht Zoeken cmdlet vindt een PowerShell-opdrachten zoals cmdlets, aliassen, functies en werkstromen.</span><span class="sxs-lookup"><span data-stu-id="17c80-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="17c80-107">Opdracht Zoeken zoekt modules in geregistreerde opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="17c80-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="17c80-108">Voor elke opdracht die door deze cmdlet worden gevonden, retourneert deze een PSGetCommandInfo-object.</span><span class="sxs-lookup"><span data-stu-id="17c80-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="17c80-109">U kunt een PSGetCommandInfo-object doorgeven aan de cmdlet Install-Module voor het installeren van de module waarin de opdracht.</span><span class="sxs-lookup"><span data-stu-id="17c80-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="17c80-110">Opdracht Zoeken kunt filteren met Versieparameters: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="17c80-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="17c80-111">Deze parameters elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="17c80-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="17c80-112">Deze Versieparameters zijn alleen met de naam van de één module zonder eventuele jokertekens toegestaan.</span><span class="sxs-lookup"><span data-stu-id="17c80-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="17c80-113">Als de parameter RequiredVersion niet is opgegeven, retourneert opdracht Zoeken de nieuwste versie van de module die gelijk is aan of groter is dan de opgegeven minimumversie of de nieuwste versie van de module als er geen minimum versie is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="17c80-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="17c80-114">Als de parameter RequiredVersion is opgegeven, zijn zoeken opdracht retourneert alleen de versie van de module die exact overeenkomt met de opgegeven versie.</span><span class="sxs-lookup"><span data-stu-id="17c80-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="17c80-115">Opdracht Zoeken kunt filteren op de metagegevens van de module met de - parameter van label</span><span class="sxs-lookup"><span data-stu-id="17c80-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="17c80-116">Opdracht Zoeken kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter.</span><span class="sxs-lookup"><span data-stu-id="17c80-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="17c80-117">Opdracht Zoeken kunt filteren op modules van alle of enkele van de geregistreerde opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="17c80-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="17c80-118">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="17c80-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="17c80-119">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="17c80-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="17c80-120">Opdracht Zoeken</span><span class="sxs-lookup"><span data-stu-id="17c80-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="17c80-121">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="17c80-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

