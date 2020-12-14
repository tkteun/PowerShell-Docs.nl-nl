---
ms.date: 12/01/2020
title: De PowerShell Gallery
description: De PowerShell Gallery is de centrale opslag plaats voor Power shell-modules, scripts en DSC-resources.
ms.openlocfilehash: f1ce6a8e2d5d72ac14cf3e4854626ef612d27891
ms.sourcegitcommit: 62282bb9c36fea3b4290b9263c1cd8e9ac216e29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96470312"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="feaad-103">De PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="feaad-103">The PowerShell Gallery</span></span>

<span data-ttu-id="feaad-104">De PowerShell Gallery is de centrale opslag plaats voor Power shell-inhoud.</span><span class="sxs-lookup"><span data-stu-id="feaad-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="feaad-105">Hierin vindt u nuttige Power shell-modules met Power shell-opdrachten en resources voor desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="feaad-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="feaad-106">U kunt ook Power shell-scripts vinden, waarvan sommige Power shell-werk stromen kunnen bevatten en die een overzicht geven van een set taken en voor deze taken sequentiëren bieden.</span><span class="sxs-lookup"><span data-stu-id="feaad-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="feaad-107">Sommige van deze pakketten zijn gemaakt door micro soft en andere zijn gemaakt door de Power shell-community.</span><span class="sxs-lookup"><span data-stu-id="feaad-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="feaad-108">Overzicht van PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="feaad-108">PowerShellGet Overview</span></span>

<span data-ttu-id="feaad-109">De PowerShellGet-module bevat cmdlets voor het detecteren, installeren, bijwerken en publiceren van Power shell-pakketten die artefacten, zoals modules, DSC-resources, functie mogelijkheden en scripts van de [PowerShell Gallery](https://www.PowerShellGallery.com) en andere particuliere opslag plaatsen bevatten.</span><span class="sxs-lookup"><span data-stu-id="feaad-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="feaad-110">Aan de slag met de galerie</span><span class="sxs-lookup"><span data-stu-id="feaad-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="feaad-111">Voor het installeren van pakketten in de galerie is de nieuwste versie van de PowerShellGet-module vereist.</span><span class="sxs-lookup"><span data-stu-id="feaad-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span> <span data-ttu-id="feaad-112">Zie [PowerShellGet installeren](installing-psget.md) voor volledige instructies.</span><span class="sxs-lookup"><span data-stu-id="feaad-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="feaad-113">Raadpleeg de pagina [Aan de slag](getting-started.md) voor meer informatie over het uitvoeren van PowerShellGet-opdrachten in de Gallery.</span><span class="sxs-lookup"><span data-stu-id="feaad-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="feaad-114">U kunt ook *Update-Help -Module PowerShellGet* uitvoeren om lokale Help-onderwerpen voor deze opdrachten te installeren.</span><span class="sxs-lookup"><span data-stu-id="feaad-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="feaad-115">Ondersteunde besturingssystemen</span><span class="sxs-lookup"><span data-stu-id="feaad-115">Supported Operating Systems</span></span>

<span data-ttu-id="feaad-116">Voor de **PowerShellGet**-module is **PowerShell 3.0 of hoger** vereist.</span><span class="sxs-lookup"><span data-stu-id="feaad-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="feaad-117">**PowerShellGet** vereist .NET Framework 4,5 of hoger.</span><span class="sxs-lookup"><span data-stu-id="feaad-117">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="feaad-118">Zie [de .NET Framework voor ontwikkel aars installeren](/dotnet/framework/install/guide-for-developers)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="feaad-118">For more information, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers).</span></span>

<span data-ttu-id="feaad-119">Aangezien **Power shell core** meerdere platformen heeft, betekent dit dat het werkt in Windows, Linux en MacOS, waardoor **PowerShellGet** ook beschikbaar is op deze systemen.</span><span class="sxs-lookup"><span data-stu-id="feaad-119">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="feaad-120">Zie [Power Shell installeren](/powershell/scripting/install/installing-powershell)voor een volledige lijst met systemen die worden ondersteund door **Power shell core** .</span><span class="sxs-lookup"><span data-stu-id="feaad-120">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/install/installing-powershell).</span></span>

<span data-ttu-id="feaad-121">Veel modules die in de galerie worden gehost, bieden ondersteuning voor verschillende besturings systemen en hebben aanvullende vereisten.</span><span class="sxs-lookup"><span data-stu-id="feaad-121">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span>
<span data-ttu-id="feaad-122">Raadpleeg de documentatie voor de modules voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="feaad-122">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="feaad-123">Hebt u een vraag?</span><span class="sxs-lookup"><span data-stu-id="feaad-123">Got a question?</span></span> <span data-ttu-id="feaad-124">Wilt u feedback geven?</span><span class="sxs-lookup"><span data-stu-id="feaad-124">Have feedback?</span></span>

<span data-ttu-id="feaad-125">Meer informatie over de PowerShell Gallery en PowerShellGet vindt u op de pagina [aan](getting-started.md) de slag.</span><span class="sxs-lookup"><span data-stu-id="feaad-125">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span>

<span data-ttu-id="feaad-126">Zie de pagina [PowerShell Gallery status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) op github voor een overzicht van de huidige status van de PowerShell Gallery Services.</span><span class="sxs-lookup"><span data-stu-id="feaad-126">To see the current status of the PowerShell Gallery services, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>

<span data-ttu-id="feaad-127">Geef feedback en Meld problemen met de [github-opslag plaats](https://github.com/PowerShell/PowerShellGallery/issues).</span><span class="sxs-lookup"><span data-stu-id="feaad-127">Please provide feedback and report issues the [GitHub repository](https://github.com/PowerShell/PowerShellGallery/issues).</span></span>
