---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Zoekresultaten filteren
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687592"
---
# <a name="filtering-search-results"></a><span data-ttu-id="6ccb1-103">Zoekresultaten filteren</span><span class="sxs-lookup"><span data-stu-id="6ccb1-103">Filtering search results</span></span>

<span data-ttu-id="6ccb1-104">De [pakketten tabblad](https://www.powershellgallery.com/packages) weergegeven van alle beschikbare pakketten in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="6ccb1-105">Er zijn verschillende manieren om te filteren, sorteren en zoeken van de pakketten.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="6ccb1-106">Voor meer informatie over een bepaald pakket, klikt u op het pakket.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="6ccb1-107">Filteren op</span><span class="sxs-lookup"><span data-stu-id="6ccb1-107">Filter By</span></span>

<span data-ttu-id="6ccb1-108">De vervolgkeuzelijst onder 'Filteren op' kan gebruikers om de resultaten door te filteren:</span><span class="sxs-lookup"><span data-stu-id="6ccb1-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="6ccb1-109">Voorlopige versie opnemen</span><span class="sxs-lookup"><span data-stu-id="6ccb1-109">Include Prerelease</span></span>
- <span data-ttu-id="6ccb1-110">Alleen stabiel</span><span class="sxs-lookup"><span data-stu-id="6ccb1-110">Stable Only</span></span>

<span data-ttu-id="6ccb1-111">Zie voor meer informatie over 'Voorlopige versie' en "Stabiele" [voorlopige versie versiebeheer toegevoegd aan PowerShellGet en PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in de Blog van het PowerShell-Team.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="6ccb1-112">De selectievakjes onder de vervolgkeuzelijst toestaan dat gebruikers om de resultaten door te filteren:</span><span class="sxs-lookup"><span data-stu-id="6ccb1-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="6ccb1-113">Pakkettypen</span><span class="sxs-lookup"><span data-stu-id="6ccb1-113">Package Types</span></span>
  - <span data-ttu-id="6ccb1-114">Module</span><span class="sxs-lookup"><span data-stu-id="6ccb1-114">Module</span></span>
  - <span data-ttu-id="6ccb1-115">Script</span><span class="sxs-lookup"><span data-stu-id="6ccb1-115">Script</span></span>
- <span data-ttu-id="6ccb1-116">Categorieën</span><span class="sxs-lookup"><span data-stu-id="6ccb1-116">Categories</span></span>
  - <span data-ttu-id="6ccb1-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6ccb1-117">Cmdlet</span></span>
  - <span data-ttu-id="6ccb1-118">DSC Resource</span><span class="sxs-lookup"><span data-stu-id="6ccb1-118">DSC Resource</span></span>
  - <span data-ttu-id="6ccb1-119">Functie</span><span class="sxs-lookup"><span data-stu-id="6ccb1-119">Function</span></span>
  - <span data-ttu-id="6ccb1-120">Mogelijkheid van de rol</span><span class="sxs-lookup"><span data-stu-id="6ccb1-120">Role Capability</span></span>
  - <span data-ttu-id="6ccb1-121">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="6ccb1-121">Workflow</span></span>

<span data-ttu-id="6ccb1-122">Als u wilt zien alleen modules in de PowerShell Gallery, Module in de pakkettypen controleren</span><span class="sxs-lookup"><span data-stu-id="6ccb1-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="6ccb1-123">Controleer op dezelfde manier als u wilt zien alleen scripts die in de PowerShell Gallery, Script in de pakkettypen.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="6ccb1-124">Filters zijn inclusief.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-124">Filters are inclusive.</span></span>
> <span data-ttu-id="6ccb1-125">Voorbeeld: Een pakket op met zowel cmdlets en -functies wordt weergegeven als een Cmdlet of functie (of beide) worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="6ccb1-126">Als geen van beide zijn geselecteerd, wordt het pakket niet weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="6ccb1-127">Alle categorieën zijn geselecteerd, wordt alleen de pakketten met een van deze categorieën worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="6ccb1-128">**Pakketten die niet tot een van deze categorieën behoren worden niet weergegeven.**</span><span class="sxs-lookup"><span data-stu-id="6ccb1-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="6ccb1-129">Sorteren op</span><span class="sxs-lookup"><span data-stu-id="6ccb1-129">Sort By</span></span>

<span data-ttu-id="6ccb1-130">De sorteren op vervolgkeuzelijst kan gebruikers de resultaten sorteren op:</span><span class="sxs-lookup"><span data-stu-id="6ccb1-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="6ccb1-131">Populariteit - populariteit wordt bepaald door het aantal downloaden</span><span class="sxs-lookup"><span data-stu-id="6ccb1-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="6ccb1-132">A-Z - alfabetisch op pakketnaam</span><span class="sxs-lookup"><span data-stu-id="6ccb1-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="6ccb1-133">Recente - pakketten worden weergegeven in de volgorde van publiceren-datum</span><span class="sxs-lookup"><span data-stu-id="6ccb1-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="6ccb1-134">Zoekvak</span><span class="sxs-lookup"><span data-stu-id="6ccb1-134">Search Box</span></span>

<span data-ttu-id="6ccb1-135">Het zoekvak kunnen gebruikers de pakketten op trefwoorden zoeken.</span><span class="sxs-lookup"><span data-stu-id="6ccb1-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="6ccb1-136">Zie voor meer informatie, [galerie Zoeksyntaxis](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="6ccb1-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
