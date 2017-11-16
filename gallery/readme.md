---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery, psget
title: De PowerShell-galerie
ms.openlocfilehash: 9fe341e4b297764321f3b3f07caca8ef4b8b40e0
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2017
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="17ad8-103">De PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="17ad8-103">The PowerShell Gallery</span></span>

<span data-ttu-id="17ad8-104">De PowerShell-galerie is de centrale opslagplaats voor PowerShell-inhoud.</span><span class="sxs-lookup"><span data-stu-id="17ad8-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="17ad8-105">U vindt nieuwe PowerShell-opdrachten of Desired State Configuration (DSC) resources in de galerie.</span><span class="sxs-lookup"><span data-stu-id="17ad8-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="17ad8-106">Overzicht van PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="17ad8-106">PowerShellGet Overview</span></span>

<span data-ttu-id="17ad8-107">De PowerShellGet-module bevat cmdlets voor het detecteren, installeren, bijwerken en publiceren van PowerShell-artefacten, zoals Modules, DSC-Resources, rol mogelijkheden en -Scripts uit de [PowerShell Gallery](https://www.PowerShellGallery.com) en andere persoonlijke opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="17ad8-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="17ad8-108">Aan de slag met de galerie</span><span class="sxs-lookup"><span data-stu-id="17ad8-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="17ad8-109">Installeren van items uit de galerie, is de meest recente versie van de module PowerShellGet, die beschikbaar is in Windows 10, in Windows Management Framework (WMF) 5.0 of in het installatieprogramma (MSI) gebaseerde (voor PowerShell 3 en 4) vereist.</span><span class="sxs-lookup"><span data-stu-id="17ad8-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="17ad8-110">[**Ophalen van Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="17ad8-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="17ad8-111">[**Ophalen van WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), of</span><span class="sxs-lookup"><span data-stu-id="17ad8-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="17ad8-112">**MSI-Installer ophalen**</span><span class="sxs-lookup"><span data-stu-id="17ad8-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="17ad8-113">Met de meest recente [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) -module, kunt u:</span><span class="sxs-lookup"><span data-stu-id="17ad8-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="17ad8-114">Zoekopdracht in de items in de galerie met [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) en [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="17ad8-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="17ad8-115">Items opslaan in uw systeem uit de galerie met [opslaan-Module](https://go.microsoft.com/fwlink/?LinkId=821669) en [opslaan-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="17ad8-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="17ad8-116">Installeren van items uit de galerie met [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) en [Script voor installatie](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="17ad8-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="17ad8-117">Items uploaden naar de galerie met [publiceren-Module](https://go.microsoft.com/fwlink/?LinkId=821666) en [publiceren-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="17ad8-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="17ad8-118">Toevoegen van uw eigen aangepaste opslagplaats met [registreren PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="17ad8-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="17ad8-119">Bekijk de [aan de slag](psgallery/psgallery_gettingstarted.md) pagina voor meer informatie over het gebruik van PowerShellGet opdrachten in de galerie.</span><span class="sxs-lookup"><span data-stu-id="17ad8-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="17ad8-120">U kunt ook uitvoeren *Update-Help-Module PowerShellGet* om lokale help voor deze opdrachten te installeren.</span><span class="sxs-lookup"><span data-stu-id="17ad8-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="17ad8-121">Ondersteunde besturingssystemen</span><span class="sxs-lookup"><span data-stu-id="17ad8-121">Supported Operating Systems</span></span>

<span data-ttu-id="17ad8-122">De **PowerShellGet** module vereist **PowerShell 3.0 of hoger**.</span><span class="sxs-lookup"><span data-stu-id="17ad8-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="17ad8-123">Daarom **PowerShellGet** moet een van de volgende besturingssystemen:</span><span class="sxs-lookup"><span data-stu-id="17ad8-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="17ad8-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="17ad8-124">Windows 10</span></span>
- <span data-ttu-id="17ad8-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="17ad8-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="17ad8-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="17ad8-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="17ad8-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="17ad8-127">Windows 7 SP1</span></span>
- <span data-ttu-id="17ad8-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="17ad8-128">Windows Server 2016</span></span>
- <span data-ttu-id="17ad8-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="17ad8-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="17ad8-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="17ad8-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="17ad8-131">**PowerShellGet** vereist ook .NET Framework 4.5 of hoger.</span><span class="sxs-lookup"><span data-stu-id="17ad8-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="17ad8-132">U kunt installeren .NET Framework 4.5 of hoger van [hier](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="17ad8-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="17ad8-133">Hebt u een vraag?</span><span class="sxs-lookup"><span data-stu-id="17ad8-133">Got a question?</span></span> <span data-ttu-id="17ad8-134">Hebt u feedback?</span><span class="sxs-lookup"><span data-stu-id="17ad8-134">Have feedback?</span></span>

<span data-ttu-id="17ad8-135">Meer informatie over de PowerShell-galerie en PowerShellGet vindt u in de [aan de slag](psgallery/psgallery_gettingstarted.md) pagina.</span><span class="sxs-lookup"><span data-stu-id="17ad8-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="17ad8-136">Geef feedback en rapport problemen met [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="17ad8-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

