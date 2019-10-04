---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery, psget
title: De PowerShell Gallery
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328740"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="8e728-103">De PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8e728-103">The PowerShell Gallery</span></span>

<span data-ttu-id="8e728-104">De PowerShell Gallery is de centrale opslag plaats voor Power shell-inhoud.</span><span class="sxs-lookup"><span data-stu-id="8e728-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="8e728-105">Hierin vindt u nuttige Power shell-modules met Power shell-opdrachten en resources voor desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="8e728-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="8e728-106">U kunt ook Power shell-scripts vinden, waarvan sommige Power shell-werk stromen kunnen bevatten en die een overzicht geven van een set taken en voor deze taken sequentiëren bieden.</span><span class="sxs-lookup"><span data-stu-id="8e728-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="8e728-107">Sommige van deze pakketten zijn gemaakt door micro soft en andere zijn gemaakt door de Power shell-community.</span><span class="sxs-lookup"><span data-stu-id="8e728-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="8e728-108">Overzicht van PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8e728-108">PowerShellGet Overview</span></span>

<span data-ttu-id="8e728-109">De PowerShellGet-module bevat cmdlets voor het detecteren, installeren, bijwerken en publiceren van Power shell-pakketten met artefacten, zoals modules, DSC-resources, functie mogelijkheden en scripts van de [PowerShell Gallery](https://www.PowerShellGallery.com) en andere persoonlijke opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="8e728-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="8e728-110">Aan de slag met de galerie</span><span class="sxs-lookup"><span data-stu-id="8e728-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="8e728-111">Voor het installeren van pakketten in de galerie is de nieuwste versie van de PowerShellGet-module vereist.</span><span class="sxs-lookup"><span data-stu-id="8e728-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="8e728-112">Zie [PowerShellGet installeren](installing-psget.md) voor volledige instructies.</span><span class="sxs-lookup"><span data-stu-id="8e728-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="8e728-113">Bekijk de pagina [aan](getting-started.md) de slag voor meer informatie over het gebruik van PowerShellGet-opdrachten met de galerie.</span><span class="sxs-lookup"><span data-stu-id="8e728-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="8e728-114">U kunt ook *Update-Help-module PowerShellGet* uitvoeren om de lokale Help voor deze opdrachten te installeren.</span><span class="sxs-lookup"><span data-stu-id="8e728-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="8e728-115">Ondersteunde besturings systemen</span><span class="sxs-lookup"><span data-stu-id="8e728-115">Supported Operating Systems</span></span>

<span data-ttu-id="8e728-116">De **PowerShellGet** -module vereist **Windows Power Shell 3,0 of hoger**, of **Power shell Core 6,0 of hoger**.</span><span class="sxs-lookup"><span data-stu-id="8e728-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="8e728-117">Er is een geschikte versie van **Windows Power shell** beschikbaar voor deze besturings systemen:</span><span class="sxs-lookup"><span data-stu-id="8e728-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="8e728-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8e728-118">Windows 10</span></span>
- <span data-ttu-id="8e728-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="8e728-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="8e728-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="8e728-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="8e728-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8e728-121">Windows 7 SP1</span></span>
- <span data-ttu-id="8e728-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="8e728-122">Windows Server 2019</span></span>
- <span data-ttu-id="8e728-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8e728-123">Windows Server 2016</span></span>
- <span data-ttu-id="8e728-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8e728-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="8e728-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8e728-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="8e728-126">**PowerShellGet** vereist .NET Framework 4,5 of hoger.</span><span class="sxs-lookup"><span data-stu-id="8e728-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="8e728-127">U kunt .NET Framework 4,5 of hoger [installeren.](https://msdn.microsoft.com/library/5a4x27ek.aspx)</span><span class="sxs-lookup"><span data-stu-id="8e728-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="8e728-128">Aangezien **Power shell core** meerdere platformen heeft, betekent dit dat het werkt in Windows, Linux en MacOS, waardoor **PowerShellGet** ook beschikbaar is op deze systemen.</span><span class="sxs-lookup"><span data-stu-id="8e728-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="8e728-129">Zie [Power Shell installeren](/powershell/scripting/setup/installing-powershell)voor een volledige lijst met systemen die worden ondersteund door **Power shell core** .</span><span class="sxs-lookup"><span data-stu-id="8e728-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="8e728-130">Veel modules die in de galerie worden gehost, bieden ondersteuning voor verschillende besturings systemen en hebben aanvullende vereisten.</span><span class="sxs-lookup"><span data-stu-id="8e728-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="8e728-131">Raadpleeg de documentatie voor de modules voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8e728-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="8e728-132">Hebt u een vraag?</span><span class="sxs-lookup"><span data-stu-id="8e728-132">Got a question?</span></span> <span data-ttu-id="8e728-133">Feedback geven?</span><span class="sxs-lookup"><span data-stu-id="8e728-133">Have feedback?</span></span>

<span data-ttu-id="8e728-134">Meer informatie over de PowerShell Gallery en PowerShellGet vindt u op de pagina [aan](getting-started.md) de slag.</span><span class="sxs-lookup"><span data-stu-id="8e728-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="8e728-135">Geef feedback en Meld problemen met [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="8e728-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>