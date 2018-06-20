---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Aan de slag met de PowerShell-galerie
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190159"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="8c3d1-103">Aan de slag met de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="8c3d1-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="8c3d1-104">Downloaden van items uit de PowerShell-galerie in uw systeem vereist de [PowerShellGet](/powershell/module/powershellget) module.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="8c3d1-105">U kunt de module PowerShellGet vinden in het volgende.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="8c3d1-106">U hoeft niet aan te melden bij het downloaden van items uit de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="8c3d1-107">Detectie van items van de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8c3d1-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="8c3d1-108">U kunt items in de PowerShell-galerie vinden met behulp van de **Search** besturingselement op deze website, of door te bladeren door de pagina's Modules en -Scripts.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="8c3d1-109">U kunt items van de PowerShell Gallery ook vinden door het uitvoeren van de [Find-Module][] en [zoeken Script][] cmdlets, afhankelijk van het itemtype met `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="8c3d1-110">Filteren van resultaten uit de galerie kan worden gedaan met behulp van de volgende parameters:</span><span class="sxs-lookup"><span data-stu-id="8c3d1-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="8c3d1-111">Naam</span><span class="sxs-lookup"><span data-stu-id="8c3d1-111">Name</span></span>
- <span data-ttu-id="8c3d1-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="8c3d1-112">AllVersions</span></span>
- <span data-ttu-id="8c3d1-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="8c3d1-113">MinimumVersion</span></span>
- <span data-ttu-id="8c3d1-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="8c3d1-114">RequiredVersion</span></span>
- <span data-ttu-id="8c3d1-115">Label</span><span class="sxs-lookup"><span data-stu-id="8c3d1-115">Tag</span></span>
- <span data-ttu-id="8c3d1-116">Bevat</span><span class="sxs-lookup"><span data-stu-id="8c3d1-116">Includes</span></span>
- <span data-ttu-id="8c3d1-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="8c3d1-117">DscResource</span></span>
- <span data-ttu-id="8c3d1-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="8c3d1-118">RoleCapability</span></span>
- <span data-ttu-id="8c3d1-119">Opdracht</span><span class="sxs-lookup"><span data-stu-id="8c3d1-119">Command</span></span>
- <span data-ttu-id="8c3d1-120">Filter</span><span class="sxs-lookup"><span data-stu-id="8c3d1-120">Filter</span></span>

<span data-ttu-id="8c3d1-121">U kunt uitvoeren als u alleen geïnteresseerd bent in het detecteren van specifieke DSC-resources in de galerie, de [zoeken DscResource] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="8c3d1-122">Zoeken naar DscResource retourneert gegevens van DSC-resources die zijn opgenomen in de galerie.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="8c3d1-123">Omdat de DSC-resources zijn altijd geleverd als onderdeel van een module, moet u nog steeds uitgevoerd [Install-Module][] voor het installeren van de DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="8c3d1-124">Meer informatie over de items in de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="8c3d1-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="8c3d1-125">Zodra u een item dat u geïnteresseerd bent in hebt geïdentificeerd, kunt u meer informatie over het.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="8c3d1-126">U kunt dit doen door te controleren dat item specifieke pagina in de galerie.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="8c3d1-127">Klik op deze pagina kunt u zult kunnen zien alle van de metagegevens geüpload met het item.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="8c3d1-128">Deze metagegevens voor een item wordt aangeboden door de auteur van het item en is niet geverifieerd door Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="8c3d1-129">De eigenaar van het item ten zeerste aan het galerie-account gebruikt voor het publiceren van het item is gekoppeld en is betrouwbaarder dan het veld Auteur.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="8c3d1-130">Als u ontdekt dat een item dat u van mening bent dat niet is gepubliceerd te goeder trouw, klikt u op **misbruik melden** op de pagina van het artikel.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="8c3d1-131">Als u werkt met [Find-Module][] of [zoeken Script][], u kunt deze gegevens weergeven in de geretourneerde PSGetModuleInfo-object.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="8c3d1-132">Bijvoorbeeld, `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` retourneert gegevens voor de module PSReadLine in de galerie.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="8c3d1-133">Downloaden van items van de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8c3d1-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="8c3d1-134">Bij het downloaden van items van de PowerShell Gallery raden we het volgende proces:</span><span class="sxs-lookup"><span data-stu-id="8c3d1-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="8c3d1-135">Controleren</span><span class="sxs-lookup"><span data-stu-id="8c3d1-135">Inspect</span></span>

<span data-ttu-id="8c3d1-136">Voor het downloaden van een item uit de galerie voor inspectie, voer de [opslaan-Module][] of [opslaan Script][] cmdlet, afhankelijk van het itemtype.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="8c3d1-137">Hiermee kunt u het item lokaal opslaan zonder het te installeren en de inhoud van het item controleren.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="8c3d1-138">Onthoud het opgeslagen item handmatig verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="8c3d1-139">Sommige van deze items zijn gemaakt door Microsoft en anderen zijn ontworpen door de PowerShell-community.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="8c3d1-140">Microsoft raadt aan dat u de inhoud en code van de items in deze galerie voorafgaand aan installatie bekijken.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="8c3d1-141">Als u ontdekt dat een item dat u van mening bent dat niet is gepubliceerd te goeder trouw, klikt u op **misbruik melden** op de pagina van het artikel.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="8c3d1-142">Installeren</span><span class="sxs-lookup"><span data-stu-id="8c3d1-142">Install</span></span>

<span data-ttu-id="8c3d1-143">Uitvoeren als u wilt installeren een item uit de galerie voor gebruik, de [Install-Module][] of [Script voor installatie][] cmdlet, afhankelijk van het itemtype.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="8c3d1-144">[Install-Module][] installeert u de module `$env:ProgramFiles\WindowsPowerShell\Modules` standaard.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="8c3d1-145">Hiervoor moet een administrator-account.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-145">This requires an administrator account.</span></span> <span data-ttu-id="8c3d1-146">Als u de `-Scope CurrentUser` parameter, de module is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="8c3d1-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="8c3d1-147">[Script voor installatie][] installeert u het script `$env:ProgramFiles\WindowsPowerShell\Scripts` standaard.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="8c3d1-148">Hiervoor moet een administrator-account.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-148">This requires an administrator account.</span></span> <span data-ttu-id="8c3d1-149">Als u de `-Scope CurrentUser` parameter, het script wordt geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="8c3d1-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="8c3d1-150">Standaard [Install-Module][] en [Script voor installatie][] installeert de meest recente versie van een item.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="8c3d1-151">Voor het installeren van een oudere versie van het item toevoegen de `-RequiredVersion` parameter.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="8c3d1-152">Implementeer</span><span class="sxs-lookup"><span data-stu-id="8c3d1-152">Deploy</span></span>

<span data-ttu-id="8c3d1-153">Voor het implementeren van een item uit de galerie PowerShell voor Azure Automation, klikt u op **implementeren in Azure Automation** op de detailpagina item.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="8c3d1-154">U wordt omgeleid naar de Azure-beheerportal, waar u zich aanmelden met behulp van de referenties van uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="8c3d1-155">Houd er rekening mee dat het implementeren van items met afhankelijkheden alle afhankelijkheden voor Azure Automation inzetten.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="8c3d1-156">De knop 'Implementeren in Azure Automation' kan worden uitgeschakeld door het toevoegen van de **AzureAutomationNotSupported** label in de itemmetagegevens van uw.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="8c3d1-157">Zie voor meer informatie over Azure Automation, de [Azure Automation](/azure/automation) documentatie.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="8c3d1-158">Bijwerken van de items van de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8c3d1-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="8c3d1-159">Om bij te werken items geïnstalleerd vanuit de PowerShell-galerie, voer de [Update-Module] [] of [updatescript] [] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="8c3d1-160">Wanneer uitvoert zonder extra parameters, [] [Update-Module] probeert bij te werken van elke module die is geïnstalleerd door het uitvoeren van [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="8c3d1-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="8c3d1-161">Om bij te werken selectief modules, voeg de `-Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="8c3d1-162">Op dezelfde manier als uitvoert zonder extra parameters, [] [updatescript] ook probeert om te werken elk geïnstalleerd door het uitvoeren van script [Script voor installatie][].</span><span class="sxs-lookup"><span data-stu-id="8c3d1-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="8c3d1-163">Voor het selectief bijwerken scripts, voeg de `-Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="8c3d1-164">Lijst met items die u hebt geïnstalleerd vanuit de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="8c3d1-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="8c3d1-165">Als u wilt weten welke modules die u hebt geïnstalleerd vanuit de PowerShell-galerie, voer de [Get-InstalledModule][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="8c3d1-166">Met deze opdracht worden alle van de modules die op uw systeem is geïnstalleerd en die rechtstreeks vanuit de PowerShell-galerie zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="8c3d1-167">Op dezelfde manier als u wilt weten welke scripts die u hebt geïnstalleerd vanuit de PowerShell-galerie, voer de [Get-InstalledScript][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="8c3d1-168">Met deze opdracht worden alle van de scripts die op uw systeem is geïnstalleerd en die rechtstreeks van de PowerShell Gallery zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8c3d1-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[zoeken DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[zoeken Script]: /powershell/module/powershellget/Find-Script
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Script voor installatie]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[opslaan-Module]: /powershell/module/powershellget/Save-Module
[Save-Module]: /powershell/module/powershellget/Save-Module
[opslaan Script]: /powershell/module/powershellget/Save-Script
[Save-Script]: /powershell/module/powershellget/Save-Script