---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057465"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="796aa-102">PowerShell-Module detecteren, installeren en inventariseren van scripts met PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="796aa-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="796aa-103">PowerShellGet is opgenomen in deze versie van WMF:</span><span class="sxs-lookup"><span data-stu-id="796aa-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="796aa-104">Find-Module kunt filteren op de metagegevens van de module met de - parameter Tag</span><span class="sxs-lookup"><span data-stu-id="796aa-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="796aa-105">Find-Module kunt filteren op zoektaal van de opslagplaats-specifieke met de parameter - Filter</span><span class="sxs-lookup"><span data-stu-id="796aa-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="796aa-106">Find-Module kan filteren op basis van de module met de opdracht-, - sleutelwoorden dscresource bieden, inhoud en - parameters bevat</span><span class="sxs-lookup"><span data-stu-id="796aa-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="796aa-107">Zoeken naar sleutelwoorden-dscresource bieden kunt detectie van afzonderlijke DSC-resources in opslagplaatsen</span><span class="sxs-lookup"><span data-stu-id="796aa-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="796aa-108">Ondersteuning voor het installeren van en publiceren naar bestandsshares met NuGet</span><span class="sxs-lookup"><span data-stu-id="796aa-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="796aa-109">Van de voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="796aa-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="796aa-110">Nieuwe functies in PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="796aa-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="796aa-111">Ondersteuning voor de side-by-side-versie van Windows PowerShell 5.0 of hoger</span><span class="sxs-lookup"><span data-stu-id="796aa-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="796aa-112">Ondersteuning voor de installatie van module afhankelijkheid</span><span class="sxs-lookup"><span data-stu-id="796aa-112">Module dependency installation support</span></span>
-   <span data-ttu-id="796aa-113">Drie nieuwe cmdlets</span><span class="sxs-lookup"><span data-stu-id="796aa-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="796aa-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="796aa-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="796aa-115">Verwijderen-Module</span><span class="sxs-lookup"><span data-stu-id="796aa-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="796aa-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="796aa-116">Save-Module</span></span>
