---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery, psget
title: De PowerShell Gallery
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685457"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="8d228-103">De PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8d228-103">The PowerShell Gallery</span></span>

<span data-ttu-id="8d228-104">De PowerShell Gallery is de centrale opslagplaats voor PowerShell-inhoud.</span><span class="sxs-lookup"><span data-stu-id="8d228-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="8d228-105">In deze vindt u nuttige PowerShell-modules met PowerShell-opdrachten en de resources van Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="8d228-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="8d228-106">U vindt hier ook PowerShell-scripts, waarvan sommige mogelijk PowerShell-werkstromen en die beschrijven een aantal taken en sequentiëren voor deze taken bieden.</span><span class="sxs-lookup"><span data-stu-id="8d228-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="8d228-107">Sommige van deze pakketten zijn geschreven door Microsoft en anderen worden geschreven door de PowerShell-community.</span><span class="sxs-lookup"><span data-stu-id="8d228-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="8d228-108">PowerShellGet-overzicht</span><span class="sxs-lookup"><span data-stu-id="8d228-108">PowerShellGet Overview</span></span>

<span data-ttu-id="8d228-109">De PowerShellGet-module bevat cmdlets voor het detecteren, installeren, bijwerken en publiceren van PowerShell-pakketten die artefacten, zoals Modules, DSC-Resources, Rolmogelijkheden en Scripts bevatten de [PowerShell Gallery](https://www.PowerShellGallery.com)en andere opslagplaatsen met privé.</span><span class="sxs-lookup"><span data-stu-id="8d228-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="8d228-110">Aan de slag met de galerie</span><span class="sxs-lookup"><span data-stu-id="8d228-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="8d228-111">Installatie van pakketten uit de galerie, is de meest recente versie van de PowerShellGet-module vereist.</span><span class="sxs-lookup"><span data-stu-id="8d228-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="8d228-112">Zie [PowerShellGet installeren](installing-psget.md) voor volledige instructies.</span><span class="sxs-lookup"><span data-stu-id="8d228-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="8d228-113">Bekijk de [aan de slag](getting-started.md) pagina voor meer informatie over het gebruik van PowerShellGet-opdrachten in de galerie.</span><span class="sxs-lookup"><span data-stu-id="8d228-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="8d228-114">U kunt ook uitvoeren *Update-Help-Module PowerShellGet* om lokale help voor deze opdrachten te installeren.</span><span class="sxs-lookup"><span data-stu-id="8d228-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="8d228-115">Ondersteunde besturingssystemen</span><span class="sxs-lookup"><span data-stu-id="8d228-115">Supported Operating Systems</span></span>

<span data-ttu-id="8d228-116">De **PowerShellGet** module vereist **Windows PowerShell 3.0 of hoger**, of **PowerShell Core 6.0 of hoger**.</span><span class="sxs-lookup"><span data-stu-id="8d228-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="8d228-117">Een geschikte versie van **Windows PowerShell** is beschikbaar voor deze besturingssystemen:</span><span class="sxs-lookup"><span data-stu-id="8d228-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="8d228-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8d228-118">Windows 10</span></span>
- <span data-ttu-id="8d228-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="8d228-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="8d228-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="8d228-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="8d228-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8d228-121">Windows 7 SP1</span></span>
- <span data-ttu-id="8d228-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="8d228-122">Windows Server 2019</span></span>
- <span data-ttu-id="8d228-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8d228-123">Windows Server 2016</span></span>
- <span data-ttu-id="8d228-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8d228-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="8d228-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8d228-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="8d228-126">**PowerShellGet** moet .NET Framework 4.5 of hoger.</span><span class="sxs-lookup"><span data-stu-id="8d228-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="8d228-127">U kunt installeren .NET Framework 4.5 of hoger van [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d228-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="8d228-128">Aangezien **PowerShell Core** platformoverschrijdende is en dat betekent dat het werkt op Windows, Linux en Mac OS, die ook wordt **PowerShellGet** beschikbaar is op deze systemen.</span><span class="sxs-lookup"><span data-stu-id="8d228-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="8d228-129">Voor een volledige lijst van systemen die worden ondersteund door **PowerShell Core** Zie [PowerShell installeren](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="8d228-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="8d228-130">Veel modules die worden gehost in de galerie ondersteuning biedt voor verschillende besturingssystemen en gelden aanvullende vereisten.</span><span class="sxs-lookup"><span data-stu-id="8d228-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="8d228-131">Raadpleeg de documentatie voor de modules voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8d228-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="8d228-132">Hebt u een vraag?</span><span class="sxs-lookup"><span data-stu-id="8d228-132">Got a question?</span></span> <span data-ttu-id="8d228-133">Hebt u feedback?</span><span class="sxs-lookup"><span data-stu-id="8d228-133">Have feedback?</span></span>

<span data-ttu-id="8d228-134">Meer informatie over de PowerShell Gallery en PowerShellGet vindt u de [aan de slag](getting-started.md) pagina.</span><span class="sxs-lookup"><span data-stu-id="8d228-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="8d228-135">Geef feedback en het rapport problemen met behulp van [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="8d228-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
