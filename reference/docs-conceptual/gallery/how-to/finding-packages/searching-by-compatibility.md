---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galerie, Power shell, cmdlet, psgallery
title: Pakketten met compatibele Power shell-edities of besturings systeem
ms.openlocfilehash: b414ce2c2b189e9da150cbe612e0bb2572d39e76
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278351"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="183f5-103">Pakketten met compatibele Power shell-edities of-besturings systemen</span><span class="sxs-lookup"><span data-stu-id="183f5-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="183f5-104">Vanaf versie 5,1 is Power shell beschikbaar in verschillende edities waarin verschillende functie sets en platform compatibiliteit worden aangegeven.</span><span class="sxs-lookup"><span data-stu-id="183f5-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="183f5-105">Zoeken op Power shell-editie</span><span class="sxs-lookup"><span data-stu-id="183f5-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="183f5-106">De twee versies van Power shell zijn:</span><span class="sxs-lookup"><span data-stu-id="183f5-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="183f5-107">**Desktop Edition:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van Power shell die worden uitgevoerd op edities van Windows met een volledige footprint, zoals Server Core en Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="183f5-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="183f5-108">**Core-editie:** Gebaseerd op .NET core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van Power shell die worden uitgevoerd op edities van Windows met een verminderde footprint, zoals nano server en Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="183f5-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="183f5-109">Met PowerShell Gallery kunt u pakketten filteren die compatibel zijn voor specifieke Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="183f5-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="183f5-110">Als voor een pakket compatibele PSEditions is opgegeven, worden deze vermeld als onderdeel van Power shell-edities op de pagina pakket weergave en ook in pakketten met resultaten.</span><span class="sxs-lookup"><span data-stu-id="183f5-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="183f5-111">U kunt ook zoeken naar compatibele pakketten met behulp van Power shell.</span><span class="sxs-lookup"><span data-stu-id="183f5-111">You can also search for compatible packages using PowerShell.</span></span>

![Pagina item weergave met PSEditions](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="183f5-113">Pakketten zoeken in de gebruikers interface van de galerie die werkt met Power shell core</span><span class="sxs-lookup"><span data-stu-id="183f5-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="183f5-114">Tags: "PSEdition_Desktop" en Tags: "PSEdition_Core" gebruiken om de pakketten op PowerShell Gallery te filteren.</span><span class="sxs-lookup"><span data-stu-id="183f5-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="183f5-115">Tags gebruiken: ' PSEdition_Core ' om items te zoeken die compatibel zijn met Power shell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="183f5-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Zoek resultaten voor items die compatibel zijn met Core PSEdition](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="183f5-117">Tags gebruiken: ' PSEdition_Desktop ' om items te zoeken die compatibel zijn met Power shell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="183f5-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Zoek resultaten voor items die compatibel zijn met Desktop PSEdition](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="183f5-119">Pakketten zoeken om compatibele versies te vinden met behulp van Power shell</span><span class="sxs-lookup"><span data-stu-id="183f5-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="183f5-120">U kunt labels opgeven voor het filteren van de Power shell-editie en het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="183f5-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="183f5-121">U gebruikt de cmdlet `Find-Package` om de `-Tag`-para meter op te geven voor de editie (en het besturings systeem) waarop u zich wilt richten.</span><span class="sxs-lookup"><span data-stu-id="183f5-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="183f5-122">Zo:</span><span class="sxs-lookup"><span data-stu-id="183f5-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="183f5-123">Zoeken op besturings systeem</span><span class="sxs-lookup"><span data-stu-id="183f5-123">Searching by Operating System</span></span>

<span data-ttu-id="183f5-124">Omdat Power shell core beschikbaar is voor Windows, Linux en MacOS, kunnen pakketten in de galerie worden ontworpen voor een combi natie van deze besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="183f5-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="183f5-125">Gebruik in de gebruikers interface van de galerie de volgende zoek tags om pakketten te vinden die zijn gelabeld door het besturings systeem:</span><span class="sxs-lookup"><span data-stu-id="183f5-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="183f5-126">Tags: "Windows"</span><span class="sxs-lookup"><span data-stu-id="183f5-126">Tags: "Windows"</span></span>
- <span data-ttu-id="183f5-127">Tags: Linux</span><span class="sxs-lookup"><span data-stu-id="183f5-127">Tags: "Linux"</span></span>
- <span data-ttu-id="183f5-128">Tags: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="183f5-128">Tags: "MacOS"</span></span>

<span data-ttu-id="183f5-129">U kunt deze Tags opgeven op `Find-Module` (en andere cmdlets in de module PowerShellGet), bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="183f5-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="183f5-130">Zoeken naar meerdere compatibiliteits problemen</span><span class="sxs-lookup"><span data-stu-id="183f5-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="183f5-131">U kunt zoeken naar een pakket met meerdere compatibiliteit met behulp van de syntaxis:</span><span class="sxs-lookup"><span data-stu-id="183f5-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="183f5-132">Tags: "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="183f5-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="183f5-133">Als u bijvoorbeeld zoekt naar een pakket met Power shell core-compatibiliteit dat op zowel mijn Windows-als Linux-computers wordt uitgevoerd, gebruikt u de zoek Tags:</span><span class="sxs-lookup"><span data-stu-id="183f5-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="183f5-134">Tags: "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="183f5-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="183f5-135">Als u wilt zoeken met behulp van Power shell, kunt u de `Find-Module` (en de andere cmdlets in de module PowerShellGet) gebruiken, zoals:</span><span class="sxs-lookup"><span data-stu-id="183f5-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="183f5-136">Meer informatie over het ontwerpen en vinden van de pakketten met compatibele Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="183f5-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="183f5-137">Modules met PSEditions</span><span class="sxs-lookup"><span data-stu-id="183f5-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="183f5-138">Scripts met PSEditions</span><span class="sxs-lookup"><span data-stu-id="183f5-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
