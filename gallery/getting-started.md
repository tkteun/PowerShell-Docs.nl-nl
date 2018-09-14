---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Aan de slag met de PowerShell Gallery
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523028"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="e5dc7-103">Aan de slag met de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e5dc7-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="e5dc7-104">De juiste manier voor het installeren van items vanuit de PowerShell Gallery is met de cmdlets in de [PowerShellGet](/powershell/module/powershellget) module.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-104">The proper way to install items from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="e5dc7-105">U hoeft zich niet aanmelden bij het downloaden van items vanuit de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="e5dc7-106">Het is mogelijk een pakket rechtstreeks downloaden vanuit de PowerShell Gallery, maar dit is niet een aanbevolen aanpak.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="e5dc7-107">Zie voor meer informatie, [handmatig pakket downloaden](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span><span class="sxs-lookup"><span data-stu-id="e5dc7-107">For more details, see [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span></span>  


## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="e5dc7-108">Detectie van items uit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e5dc7-108">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="e5dc7-109">U kunt items in de PowerShell Gallery zoeken met behulp van de **zoeken** besturingselement op deze website, of door te bladeren door de pagina's Modules en -Scripts.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-109">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="e5dc7-110">U kunt ook items uit de PowerShell Gallery vinden door te voeren de [Find-Module][] en [Find-Script][] cmdlets, afhankelijk van het itemtype met `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-110">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="e5dc7-111">Resultaten van de galerie filteren kan worden gedaan met behulp van de volgende parameters:</span><span class="sxs-lookup"><span data-stu-id="e5dc7-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="e5dc7-112">Naam</span><span class="sxs-lookup"><span data-stu-id="e5dc7-112">Name</span></span>
- <span data-ttu-id="e5dc7-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="e5dc7-113">AllVersions</span></span>
- <span data-ttu-id="e5dc7-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e5dc7-114">MinimumVersion</span></span>
- <span data-ttu-id="e5dc7-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e5dc7-115">RequiredVersion</span></span>
- <span data-ttu-id="e5dc7-116">Label</span><span class="sxs-lookup"><span data-stu-id="e5dc7-116">Tag</span></span>
- <span data-ttu-id="e5dc7-117">Bevat</span><span class="sxs-lookup"><span data-stu-id="e5dc7-117">Includes</span></span>
- <span data-ttu-id="e5dc7-118">Sleutelwoorden voor dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="e5dc7-118">DscResource</span></span>
- <span data-ttu-id="e5dc7-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e5dc7-119">RoleCapability</span></span>
- <span data-ttu-id="e5dc7-120">Opdracht</span><span class="sxs-lookup"><span data-stu-id="e5dc7-120">Command</span></span>
- <span data-ttu-id="e5dc7-121">Filter</span><span class="sxs-lookup"><span data-stu-id="e5dc7-121">Filter</span></span>

<span data-ttu-id="e5dc7-122">Als u alleen geïnteresseerd in het detecteren van specifieke DSC-resources in de galerie bent, kunt u uitvoeren de [Zoeken naar sleutelwoorden-dscresource bieden] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="e5dc7-123">Zoeken naar sleutelwoorden-dscresource bieden retourneert gegevens van DSC-resources die zijn opgenomen in de galerie.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="e5dc7-124">Omdat de DSC-resources worden altijd geleverd als onderdeel van een module, moet u nog steeds uitgevoerd [Install-Module][] voor het installeren van de DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="e5dc7-125">Meer informatie over de items in de PowerShell-galerie</span><span class="sxs-lookup"><span data-stu-id="e5dc7-125">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="e5dc7-126">Wanneer u een item dat u geïnteresseerd bent in hebt geïdentificeerd, kunt u meer informatie over deze.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-126">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="e5dc7-127">U kunt dit doen door te controleren van specifieke pagina in de galerie van het artikel.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-127">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="e5dc7-128">Op deze pagina kunt u zult kunnen zien van alle van de metagegevens van het item zijn geüpload.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-128">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="e5dc7-129">Deze metagegevens voor een item wordt geleverd door de auteur van het item en wordt niet gecontroleerd door Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-129">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="e5dc7-130">De eigenaar van het item is nauw verbonden met het galerie-account gebruikt voor het publiceren van het item en is betrouwbaarder dan het veld ' auteur '.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-130">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="e5dc7-131">Als u ontdekt een item dat u denkt dat niet is gepubliceerd in goed vertrouwen, klikt u op **misbruik** op de pagina van het artikel.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-131">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="e5dc7-132">Als u werkt met [Find-Module][] of [Find-Script][], u kunt deze gegevens weergeven in de geretourneerde PSGetModuleInfo-object.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="e5dc7-133">Bijvoorbeeld uitgevoerd `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="e5dc7-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="e5dc7-134">retourneert de gegevens op de module PSReadLine in de galerie.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="e5dc7-135">Downloaden van items uit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e5dc7-135">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="e5dc7-136">We raden het volgende proces wanneer het downloaden van items uit de galerie met PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e5dc7-136">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="e5dc7-137">Controleren</span><span class="sxs-lookup"><span data-stu-id="e5dc7-137">Inspect</span></span>

<span data-ttu-id="e5dc7-138">Voor het downloaden van een item uit de galerie voor inspectie, voer een de [Save-Module][] of [Save-Script][] cmdlet, afhankelijk van het itemtype.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-138">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="e5dc7-139">Hiermee kunt u het item lokaal opslaan zonder dat deze wordt geïnstalleerd, en de inhoud van het item controleren.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-139">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="e5dc7-140">Vergeet niet om het opgeslagen item handmatig verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-140">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="e5dc7-141">Sommige van deze items zijn gemaakt door Microsoft en anderen worden geschreven door de PowerShell-community.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-141">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="e5dc7-142">Microsoft raadt aan dat u de inhoud en code van items in deze galerie voorafgaand aan installatie controleren.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-142">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="e5dc7-143">Als u ontdekt een item dat u denkt dat niet is gepubliceerd in goed vertrouwen, klikt u op **misbruik** op de pagina van het artikel.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-143">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="e5dc7-144">Installeren</span><span class="sxs-lookup"><span data-stu-id="e5dc7-144">Install</span></span>

<span data-ttu-id="e5dc7-145">Voor het installeren van een item uit de galerie voor gebruik, voer een de [Install-Module][] of [Script voor installatie][] cmdlet, afhankelijk van het itemtype.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-145">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="e5dc7-146">[Install-Module][] installeert van de module `$env:ProgramFiles\WindowsPowerShell\Modules` standaard.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="e5dc7-147">Hiervoor moet een administrator-account.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-147">This requires an administrator account.</span></span> <span data-ttu-id="e5dc7-148">Als u de `-Scope CurrentUser` parameter, de module is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e5dc7-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="e5dc7-149">[Script voor installatie][] wordt geïnstalleerd met het script `$env:ProgramFiles\WindowsPowerShell\Scripts` standaard.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="e5dc7-150">Hiervoor moet een administrator-account.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-150">This requires an administrator account.</span></span> <span data-ttu-id="e5dc7-151">Als u de `-Scope CurrentUser` parameter, het script is geïnstalleerd op `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="e5dc7-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="e5dc7-152">Standaard [Install-Module][] en [Script voor installatie][] installeert de meest recente versie van een item.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="e5dc7-153">Toevoegen voor het installeren van een oudere versie van het item, de `-RequiredVersion` parameter.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-153">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="e5dc7-154">Implementeer</span><span class="sxs-lookup"><span data-stu-id="e5dc7-154">Deploy</span></span>

<span data-ttu-id="e5dc7-155">Voor het implementeren van een item uit de galerie met PowerShell voor Azure Automation, klikt u op **implementeren in Azure Automation** op de pagina met details van item.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-155">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="e5dc7-156">U wordt omgeleid naar de Azure-beheerportal, waar u zich aanmelden met behulp van de referenties van uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-156">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="e5dc7-157">Houd er rekening mee dat items met afhankelijkheden implementeren alle afhankelijkheden voor Azure Automation implementeert.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-157">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="e5dc7-158">De knop 'Implementeren voor Azure Automation' kan worden uitgeschakeld door toe te voegen de **AzureAutomationNotSupported** tag in de itemmetagegevens van het.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="e5dc7-159">Zie voor meer informatie over Azure Automation, de [Azure Automation](/azure/automation) documentatie.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="e5dc7-160">Bijwerken van items uit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e5dc7-160">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="e5dc7-161">Om bij te werken items hebt geïnstalleerd vanuit PowerShell Gallery, voer de [Update-Module] [] of [updatescript] []-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-161">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="e5dc7-162">Wanneer uitvoert zonder extra parameters, [] [-Update-Module] probeert bij te werken van elke module geïnstalleerd door te voeren [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="e5dc7-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="e5dc7-163">Als u wilt bijwerken selectief modules, toevoegen de `-Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="e5dc7-164">Op dezelfde manier als uitvoert zonder eventuele extra parameters, [updatescript] [] ook probeert om bij te werken van elk script dat is geïnstalleerd door te voeren [Script voor installatie][].</span><span class="sxs-lookup"><span data-stu-id="e5dc7-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="e5dc7-165">Als u selectief-bijwerken scripts, wilt toevoegen de `-Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="e5dc7-166">Lijst met items die u hebt geïnstalleerd vanuit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="e5dc7-166">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="e5dc7-167">Als u wilt weten welke modules die u hebt geïnstalleerd vanuit de PowerShell Gallery, voer de [Get-InstalledModule][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="e5dc7-168">Met deze opdracht worden alle modules op uw systeem is geïnstalleerd die zijn geïnstalleerd rechtstreeks vanuit de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="e5dc7-169">Op dezelfde manier als u wilt weten welke scripts die u hebt geïnstalleerd vanuit de PowerShell Gallery, voer de [Get-InstalledScript][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="e5dc7-170">Met deze opdracht worden alle van de scripts die u hebt op uw systeem en die rechtstreeks vanuit de PowerShell Gallery zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e5dc7-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Zoeken naar sleutelwoorden-dscresource bieden]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Script voor installatie]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script