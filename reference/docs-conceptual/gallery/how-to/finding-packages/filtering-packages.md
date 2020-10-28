---
ms.date: 06/12/2017
title: Zoek resultaten filteren
description: In dit artikel wordt de gebruikers interface beschreven waarmee inhoud in het PowerShell Gallery wordt gefilterd.
ms.openlocfilehash: cc375f3ddb35c95ed134776500bd326bc3db6b1a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661405"
---
# <a name="filtering-search-results"></a><span data-ttu-id="a45e2-103">Zoek resultaten filteren</span><span class="sxs-lookup"><span data-stu-id="a45e2-103">Filtering search results</span></span>

<span data-ttu-id="a45e2-104">Op het [tabblad pakketten](https://www.powershellgallery.com/packages) worden alle beschik bare pakketten weer gegeven in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a45e2-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="a45e2-105">Er zijn verschillende manieren waarop u de pakketten kunt filteren, sorteren en doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="a45e2-105">There are several ways to filter, sort, and search the packages.</span></span> <span data-ttu-id="a45e2-106">Klik op het pakket voor meer informatie over een bepaald pakket.</span><span class="sxs-lookup"><span data-stu-id="a45e2-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="a45e2-107">Filteren op</span><span class="sxs-lookup"><span data-stu-id="a45e2-107">Filter By</span></span>

<span data-ttu-id="a45e2-108">De vervolg keuzelijst onder filteren op staat gebruikers toe om de resultaten te filteren op:</span><span class="sxs-lookup"><span data-stu-id="a45e2-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>

- <span data-ttu-id="a45e2-109">Voorlopige versie toevoegen</span><span class="sxs-lookup"><span data-stu-id="a45e2-109">Include Prerelease</span></span>
- <span data-ttu-id="a45e2-110">Alleen stabiel</span><span class="sxs-lookup"><span data-stu-id="a45e2-110">Stable Only</span></span>

<span data-ttu-id="a45e2-111">Zie [prerelease-versie die is toegevoegd aan PowerShellGet en PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in het Power shell-team blog voor meer informatie over ' Prerelease ' en ' stabiele '.</span><span class="sxs-lookup"><span data-stu-id="a45e2-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="a45e2-112">Met de selectie vakjes in de vervolg keuzelijst kunnen gebruikers de resultaten filteren door:</span><span class="sxs-lookup"><span data-stu-id="a45e2-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>

- <span data-ttu-id="a45e2-113">Pakket typen</span><span class="sxs-lookup"><span data-stu-id="a45e2-113">Package Types</span></span>
  - <span data-ttu-id="a45e2-114">Module</span><span class="sxs-lookup"><span data-stu-id="a45e2-114">Module</span></span>
  - <span data-ttu-id="a45e2-115">Script</span><span class="sxs-lookup"><span data-stu-id="a45e2-115">Script</span></span>
- <span data-ttu-id="a45e2-116">Categorieën</span><span class="sxs-lookup"><span data-stu-id="a45e2-116">Categories</span></span>
  - <span data-ttu-id="a45e2-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a45e2-117">Cmdlet</span></span>
  - <span data-ttu-id="a45e2-118">DSC-resource</span><span class="sxs-lookup"><span data-stu-id="a45e2-118">DSC Resource</span></span>
  - <span data-ttu-id="a45e2-119">Functie</span><span class="sxs-lookup"><span data-stu-id="a45e2-119">Function</span></span>
  - <span data-ttu-id="a45e2-120">Functie mogelijkheid</span><span class="sxs-lookup"><span data-stu-id="a45e2-120">Role Capability</span></span>
  - <span data-ttu-id="a45e2-121">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="a45e2-121">Workflow</span></span>

<span data-ttu-id="a45e2-122">Als u alleen modules in de PowerShell Gallery wilt weer geven, controleert u module in de pakket typen.</span><span class="sxs-lookup"><span data-stu-id="a45e2-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span> <span data-ttu-id="a45e2-123">Als u alleen scripts wilt weer geven in de PowerShell Gallery, controleert u het script in de pakket typen.</span><span class="sxs-lookup"><span data-stu-id="a45e2-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="a45e2-124">Filters zijn inclusief.</span><span class="sxs-lookup"><span data-stu-id="a45e2-124">Filters are inclusive.</span></span> <span data-ttu-id="a45e2-125">Voor beeld: een pakket met cmdlets en functies wordt weer gegeven als de cmdlet of functie (of beide) is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="a45e2-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span> <span data-ttu-id="a45e2-126">Als geen van beide is geselecteerd, wordt het pakket niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a45e2-126">If neither are selected, the package will not appear.</span></span> <span data-ttu-id="a45e2-127">Als alle categorieën zijn geselecteerd, worden alleen pakketten met een van deze categorieën weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a45e2-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span> <span data-ttu-id="a45e2-128">**Pakketten die geen deel uitmaken van een van deze categorieën, worden niet weer gegeven.**</span><span class="sxs-lookup"><span data-stu-id="a45e2-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="a45e2-129">Sorteren op</span><span class="sxs-lookup"><span data-stu-id="a45e2-129">Sort By</span></span>

<span data-ttu-id="a45e2-130">Met de vervolg keuzelijst sorteren op kunnen gebruikers de resultaten sorteren op:</span><span class="sxs-lookup"><span data-stu-id="a45e2-130">The Sort By drop-down allows users to sort the results by:</span></span>

- <span data-ttu-id="a45e2-131">Populariteit: populariteit wordt bepaald door het Download aantal</span><span class="sxs-lookup"><span data-stu-id="a45e2-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="a45e2-132">A-Z-alfabetisch op pakket naam</span><span class="sxs-lookup"><span data-stu-id="a45e2-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="a45e2-133">Recent: pakketten worden weer gegeven in de volg orde van publicatie datum</span><span class="sxs-lookup"><span data-stu-id="a45e2-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="a45e2-134">Zoekvak</span><span class="sxs-lookup"><span data-stu-id="a45e2-134">Search Box</span></span>

<span data-ttu-id="a45e2-135">Met het zoekvak kunnen gebruikers de pakketten zoeken op tref woorden.</span><span class="sxs-lookup"><span data-stu-id="a45e2-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="a45e2-136">Zie [Galerie Zoek syntaxis](search-syntax.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a45e2-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
