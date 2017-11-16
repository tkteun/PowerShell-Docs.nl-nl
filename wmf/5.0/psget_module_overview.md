---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 2c7e718bc518b332cb4303ef73b1bf5c924ca471
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="a29c3-102">Detectie van de PowerShell-Module installeren en met PowerShellGet inventariseren</span><span class="sxs-lookup"><span data-stu-id="a29c3-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>
 
<span data-ttu-id="a29c3-103">PowerShellGet is opgenomen in deze versie van WMF:</span><span class="sxs-lookup"><span data-stu-id="a29c3-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="a29c3-104">Zoek-Module kunt filteren op de metagegevens van de module met de - parameter van label</span><span class="sxs-lookup"><span data-stu-id="a29c3-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="a29c3-105">Zoek-Module kunt filteren op zoektaal opslagplaats-specifieke met de - parameter Filter</span><span class="sxs-lookup"><span data-stu-id="a29c3-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="a29c3-106">Zoek-Module kunt filteren op basis van de module met de opdracht-, - DscResource, inhoud en - parameters bevat</span><span class="sxs-lookup"><span data-stu-id="a29c3-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="a29c3-107">Zoeken naar DscResource kunt detectie van afzonderlijke DSC-resources in de opslagplaatsen</span><span class="sxs-lookup"><span data-stu-id="a29c3-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="a29c3-108">Ondersteuning voor het installeren van en publiceren naar de gedeelde bestanden met NuGet</span><span class="sxs-lookup"><span data-stu-id="a29c3-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="a29c3-109">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="a29c3-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="a29c3-110">Nieuwe functies in PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a29c3-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="a29c3-111">Side-by-side-versie-ondersteuning in Windows PowerShell 5.0 of hoger</span><span class="sxs-lookup"><span data-stu-id="a29c3-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="a29c3-112">Ondersteuning voor de installatie van module afhankelijkheid</span><span class="sxs-lookup"><span data-stu-id="a29c3-112">Module dependency installation support</span></span>
-   <span data-ttu-id="a29c3-113">Drie nieuwe cmdlets</span><span class="sxs-lookup"><span data-stu-id="a29c3-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="a29c3-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a29c3-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="a29c3-115">Verwijderen-Module</span><span class="sxs-lookup"><span data-stu-id="a29c3-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="a29c3-116">Opslaan-Module</span><span class="sxs-lookup"><span data-stu-id="a29c3-116">Save-Module</span></span>
    
