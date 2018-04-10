---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_items_tab
ms.openlocfilehash: 5058253678a4f996b080e43820fee06b35b681f4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="items-tab"></a><span data-ttu-id="9a958-103">Tabblad items</span><span class="sxs-lookup"><span data-stu-id="9a958-103">Items Tab</span></span>

<span data-ttu-id="9a958-104">De [tabblad Items](https://www.powershellgallery.com/items) alle beschikbare items worden weergegeven in de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="9a958-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="9a958-105">Er zijn verschillende manieren filteren, sorteren en zoek de items.</span><span class="sxs-lookup"><span data-stu-id="9a958-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="9a958-106">Voor meer informatie over een bepaald item, klikt u op het item.</span><span class="sxs-lookup"><span data-stu-id="9a958-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="9a958-107">Filteren op</span><span class="sxs-lookup"><span data-stu-id="9a958-107">Filter By</span></span>

<span data-ttu-id="9a958-108">De vervolgkeuzelijst onder 'Filteren op' kan gebruikers de resultaten door te filteren:</span><span class="sxs-lookup"><span data-stu-id="9a958-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="9a958-109">Include Prerelease</span><span class="sxs-lookup"><span data-stu-id="9a958-109">Include Prerelease</span></span>
* <span data-ttu-id="9a958-110">Alleen stabiele</span><span class="sxs-lookup"><span data-stu-id="9a958-110">Stable Only</span></span>

<span data-ttu-id="9a958-111">Zie voor meer informatie over 'Prerelease' en 'Stabiele' [Prerelease versiebeheer toegevoegd aan PowerShellGet en PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in de PowerShell-teamblog.</span><span class="sxs-lookup"><span data-stu-id="9a958-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="9a958-112">De selectievakjes uit onder de vervolgkeuzelijst kunnen gebruikers de resultaten door te filteren:</span><span class="sxs-lookup"><span data-stu-id="9a958-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="9a958-113">Itemtypen</span><span class="sxs-lookup"><span data-stu-id="9a958-113">Item Types</span></span>
  - <span data-ttu-id="9a958-114">Module</span><span class="sxs-lookup"><span data-stu-id="9a958-114">Module</span></span>
  - <span data-ttu-id="9a958-115">Script</span><span class="sxs-lookup"><span data-stu-id="9a958-115">Script</span></span>
* <span data-ttu-id="9a958-116">Categorieën</span><span class="sxs-lookup"><span data-stu-id="9a958-116">Categories</span></span>
  - <span data-ttu-id="9a958-117">De cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a958-117">Cmdlet</span></span>
  - <span data-ttu-id="9a958-118">DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="9a958-118">DSC Resource</span></span>
  - <span data-ttu-id="9a958-119">Functie</span><span class="sxs-lookup"><span data-stu-id="9a958-119">Function</span></span>
  - <span data-ttu-id="9a958-120">Mogelijkheid tot rol</span><span class="sxs-lookup"><span data-stu-id="9a958-120">Role Capability</span></span>
  - <span data-ttu-id="9a958-121">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="9a958-121">Workflow</span></span>

<span data-ttu-id="9a958-122">Als u wilt zien alleen modules in de PowerShell-galerie, Controleer Module in de itemtypen.</span><span class="sxs-lookup"><span data-stu-id="9a958-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="9a958-123">Controleer op dezelfde manier als u wilt zien alleen scripts die in de PowerShell-galerie, Script in de itemtypen.</span><span class="sxs-lookup"><span data-stu-id="9a958-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="9a958-124">Filters zijn inclusief.</span><span class="sxs-lookup"><span data-stu-id="9a958-124">Filters are inclusive.</span></span>
> <span data-ttu-id="9a958-125">Voorbeeld: Een item met zowel cmdlets en functies wordt weergegeven als een Cmdlet of functie (of beide) worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="9a958-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="9a958-126">Als geen van beide zijn geselecteerd, wordt het item wordt niet weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9a958-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="9a958-127">Alle categorieën zijn geselecteerd, wordt alleen items met een van deze categorieën die wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9a958-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="9a958-128">**Items die niet bij een van deze categorieën horen worden niet weergegeven.**</span><span class="sxs-lookup"><span data-stu-id="9a958-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="9a958-129">Sorteren op</span><span class="sxs-lookup"><span data-stu-id="9a958-129">Sort By</span></span>

<span data-ttu-id="9a958-130">De sorteren op vervolgkeuzelijst kan gebruikers de resultaten sorteren op:</span><span class="sxs-lookup"><span data-stu-id="9a958-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="9a958-131">Populariteit - populariteit wordt bepaald door het aantal downloaden</span><span class="sxs-lookup"><span data-stu-id="9a958-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="9a958-132">A-Z - alfabetisch op itemnaam</span><span class="sxs-lookup"><span data-stu-id="9a958-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="9a958-133">Recente - Items worden weergegeven in de volgorde van de datum publiceren</span><span class="sxs-lookup"><span data-stu-id="9a958-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="9a958-134">Zoekvak</span><span class="sxs-lookup"><span data-stu-id="9a958-134">Search Box</span></span>

<span data-ttu-id="9a958-135">Het zoekvak kunnen gebruikers de items in de trefwoorden zoeken.</span><span class="sxs-lookup"><span data-stu-id="9a958-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="9a958-136">Zie voor meer informatie [galerie Zoeksyntaxis](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="9a958-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>