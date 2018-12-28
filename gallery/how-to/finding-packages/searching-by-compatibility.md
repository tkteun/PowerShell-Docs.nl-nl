---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakketten met compatibel besturingssysteem of PowerShell-edities
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: d396d0e4cfe3d279f399c17e7337380a31d373ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/21/2018
ms.locfileid: "53747701"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="fc8f8-103">Pakketten met compatibele PowerShell-edities en besturingssystemen</span><span class="sxs-lookup"><span data-stu-id="fc8f8-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="fc8f8-104">Vanaf versie 5.1 is is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platform compatibiliteiten.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="fc8f8-105">Te zoeken via PowerShell-editie</span><span class="sxs-lookup"><span data-stu-id="fc8f8-105">Searching by PowerShell Edition</span></span> 
<span data-ttu-id="fc8f8-106">De twee edities van Powershell zijn:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-106">The two editions of Powershell are:</span></span>
- <span data-ttu-id="fc8f8-107">**Desktop-editie:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Server Core- en Windows Desktop volledige footprint.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="fc8f8-108">**Core-editie:** Gebaseerd op .NET Core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Nano Server en Windows IoT verminderde footprint.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="fc8f8-109">PowerShell Gallery kunt u voor het filteren van pakketten die compatibel is voor bepaalde PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="fc8f8-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="fc8f8-110">Als een pakket met compatibele PSEditions opgegeven, ze worden weergegeven als onderdeel van de PowerShell-edities op de pagina van het pakket weergeven en in de pakketten resultaten.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="fc8f8-111">U kunt ook zoeken naar compatibele pakketten met behulp van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-111">You can also search for compatible packages using PowerShell.</span></span>

![Pagina voor item weergeven met PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="fc8f8-113">Zoeken naar pakketten in de UI-galerie die in PowerShell Core werken</span><span class="sxs-lookup"><span data-stu-id="fc8f8-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="fc8f8-114">Codes gebruiken: Tags en "PSEdition_Desktop": "PSEdition_Core" met filters in de pakketten op PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="fc8f8-115">Codes gebruiken: "PSEdition_Core" om te zoeken naar items die compatibel is met PowerShell Core-editie.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Zoekresultaten voor items die compatibel is met Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="fc8f8-117">Codes gebruiken: "PSEdition_Desktop" om te zoeken naar items die compatibel is met de PowerShell-Desktop-editie.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Zoekresultaten voor items die compatibel is met Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="fc8f8-119">Zoeken naar pakketten te vinden compatibel is met behulp van PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="fc8f8-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="fc8f8-120">U kunt tags te filteren voor de PowerShell-editie en het besturingssysteem opgeven.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-120">You can specify tags to filter for the PowerShell edition and OS.</span></span> <span data-ttu-id="fc8f8-121">U gebruikt de `Find-Package` cmdlet op te geven de `-Tag` parameter opgeven voor de editie (en besturingssysteem) u ontwikkelt.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="fc8f8-122">Als volgt:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="fc8f8-123">Zoeken op besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="fc8f8-123">Searching by Operating System</span></span> 

<span data-ttu-id="fc8f8-124">Omdat PowerShell Core beschikbaar voor Windows, Linux en Mac OS is, kunnen de pakketten in de galerie zijn ontworpen voor elke combinatie van deze besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="fc8f8-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="fc8f8-125">In de gebruikersinterface van de galerie door de volgende searchs-codes te vinden van pakketten die zijn gemarkeerd door het besturingssysteem te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="fc8f8-126">Labels: 'Windows'</span><span class="sxs-lookup"><span data-stu-id="fc8f8-126">Tags: "Windows"</span></span>
- <span data-ttu-id="fc8f8-127">Labels: "Linux"</span><span class="sxs-lookup"><span data-stu-id="fc8f8-127">Tags: "Linux"</span></span>
- <span data-ttu-id="fc8f8-128">Labels: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="fc8f8-128">Tags: "MacOS"</span></span> 

<span data-ttu-id="fc8f8-129">U kunt deze tags opgeven op `Find-Module` (en andere cmdlets in de PowerShellGet-module), zoals deze:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="fc8f8-130">Zoeken naar meerdere compatibiliteiten</span><span class="sxs-lookup"><span data-stu-id="fc8f8-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="fc8f8-131">U kunt zoeken naar een pakket met meerdere compatibiliteiten met behulp van de syntaxis:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span> 

<span data-ttu-id="fc8f8-132">Labels: "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="fc8f8-132">Tags: "Compatibility1" "Compatibility2"</span></span> 

<span data-ttu-id="fc8f8-133">Als u een pakket met de compatibiliteit van de PowerShell Core die wordt uitgevoerd op mijn Windows- en Linux-machines zoekt, bijvoorbeeld de search-codes gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="fc8f8-134">Labels: "PSEdition_Core" 'Windows' "Linux"</span><span class="sxs-lookup"><span data-stu-id="fc8f8-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span> 

<span data-ttu-id="fc8f8-135">Als u wilt zoeken met behulp van PowerShell, kunt u de `Find-Module` (en de andere cmdlets in de PowerShellGet-module), zoals deze:</span><span class="sxs-lookup"><span data-stu-id="fc8f8-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="fc8f8-136">Meer informatie over het ontwerpen en zoeken van de pakketten met compatibele PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="fc8f8-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="fc8f8-137">Modules met PSEditions</span><span class="sxs-lookup"><span data-stu-id="fc8f8-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="fc8f8-138">Scripts met PSEditions</span><span class="sxs-lookup"><span data-stu-id="fc8f8-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
