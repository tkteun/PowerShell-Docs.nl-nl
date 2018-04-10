---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 82b8046d5cbb47300f090ce2ffbf3c279ed19458
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="7a7c2-102">Detectie van de PowerShell-Module installeren en met PowerShellGet inventariseren</span><span class="sxs-lookup"><span data-stu-id="7a7c2-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="7a7c2-103">PowerShellGet is opgenomen in deze versie van WMF:</span><span class="sxs-lookup"><span data-stu-id="7a7c2-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="7a7c2-104">Zoek-Module kunt filteren op de metagegevens van de module met de - parameter van label</span><span class="sxs-lookup"><span data-stu-id="7a7c2-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="7a7c2-105">Zoek-Module kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter</span><span class="sxs-lookup"><span data-stu-id="7a7c2-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="7a7c2-106">Zoek-Module kunt filteren op basis van de module met de opdracht-, - DscResource, inhoud en - parameters bevat</span><span class="sxs-lookup"><span data-stu-id="7a7c2-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="7a7c2-107">Zoeken naar DscResource kunt detectie van afzonderlijke DSC-resources in de opslagplaatsen</span><span class="sxs-lookup"><span data-stu-id="7a7c2-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="7a7c2-108">Ondersteuning voor het installeren van en publiceren naar de gedeelde bestanden met NuGet</span><span class="sxs-lookup"><span data-stu-id="7a7c2-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="7a7c2-109">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="7a7c2-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="7a7c2-110">Nieuwe functies in PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="7a7c2-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="7a7c2-111">Side-by-side-versie-ondersteuning in Windows PowerShell 5.0 of hoger</span><span class="sxs-lookup"><span data-stu-id="7a7c2-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="7a7c2-112">Ondersteuning voor de installatie van module afhankelijkheid</span><span class="sxs-lookup"><span data-stu-id="7a7c2-112">Module dependency installation support</span></span>
-   <span data-ttu-id="7a7c2-113">Drie nieuwe cmdlets</span><span class="sxs-lookup"><span data-stu-id="7a7c2-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="7a7c2-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="7a7c2-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="7a7c2-115">Verwijderen-Module</span><span class="sxs-lookup"><span data-stu-id="7a7c2-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="7a7c2-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="7a7c2-116">Save-Module</span></span>