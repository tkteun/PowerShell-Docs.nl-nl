---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery, psget
title: De PowerShell-galerie
ms.openlocfilehash: 65e0c427310ac20621109a6620e926a7894cf8f8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="4f9e1-103">De PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="4f9e1-103">The PowerShell Gallery</span></span>

<span data-ttu-id="4f9e1-104">De PowerShell-galerie is de centrale opslagplaats voor PowerShell-inhoud.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="4f9e1-105">In dit vindt u nuttige PowerShell-modules met PowerShell-opdrachten en resources Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="4f9e1-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="4f9e1-106">U kunt ook PowerShell-scripts, kunnen sommige van deze PowerShell-werkstromen en overzicht maken van een set taken bevatten en sequentiëren voor deze taken bieden vinden.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="4f9e1-107">Sommige van deze items zijn gemaakt door Microsoft en anderen zijn ontworpen door de PowerShell-community.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="4f9e1-108">Overzicht van PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4f9e1-108">PowerShellGet Overview</span></span>

<span data-ttu-id="4f9e1-109">De PowerShellGet-module bevat cmdlets voor het detecteren, installeren, bijwerken en publiceren van PowerShell-artefacten, zoals Modules, DSC-Resources, rol mogelijkheden en -Scripts uit de [PowerShell Gallery](https://www.PowerShellGallery.com) en andere persoonlijke opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="4f9e1-110">Aan de slag met de galerie</span><span class="sxs-lookup"><span data-stu-id="4f9e1-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="4f9e1-111">Installeren van items uit de galerie, is de meest recente versie van de module PowerShellGet vereist.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="4f9e1-112">Zie [installeren PowerShellGet](installing-psget.md) voor volledige instructies.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="4f9e1-113">Bekijk de [aan de slag](getting-started.md) pagina voor meer informatie over het gebruik van PowerShellGet opdrachten in de galerie.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="4f9e1-114">U kunt ook uitvoeren *Update-Help-Module PowerShellGet* om lokale help voor deze opdrachten te installeren.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="4f9e1-115">Ondersteunde besturingssystemen</span><span class="sxs-lookup"><span data-stu-id="4f9e1-115">Supported Operating Systems</span></span>

<span data-ttu-id="4f9e1-116">De **PowerShellGet** module vereist **PowerShell 3.0 of hoger**.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="4f9e1-117">Daarom **PowerShellGet** moet een van de volgende besturingssystemen:</span><span class="sxs-lookup"><span data-stu-id="4f9e1-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="4f9e1-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="4f9e1-118">Windows 10</span></span>
- <span data-ttu-id="4f9e1-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="4f9e1-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="4f9e1-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="4f9e1-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="4f9e1-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="4f9e1-121">Windows 7 SP1</span></span>
- <span data-ttu-id="4f9e1-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="4f9e1-122">Windows Server 2016</span></span>
- <span data-ttu-id="4f9e1-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4f9e1-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="4f9e1-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="4f9e1-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="4f9e1-125">**PowerShellGet** vereist ook .NET Framework 4.5 of hoger.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="4f9e1-126">U kunt installeren .NET Framework 4.5 of hoger van [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="4f9e1-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="4f9e1-127">Hebt u een vraag?</span><span class="sxs-lookup"><span data-stu-id="4f9e1-127">Got a question?</span></span> <span data-ttu-id="4f9e1-128">Hebt u feedback?</span><span class="sxs-lookup"><span data-stu-id="4f9e1-128">Have feedback?</span></span>

<span data-ttu-id="4f9e1-129">Meer informatie over de PowerShell-galerie en PowerShellGet vindt u in de [aan de slag](getting-started.md) pagina.</span><span class="sxs-lookup"><span data-stu-id="4f9e1-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="4f9e1-130">Geef feedback en rapport problemen met [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="4f9e1-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>