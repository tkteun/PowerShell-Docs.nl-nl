---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, Power shell, psgallery
title: Pakket handmatig downloaden
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328761"
---
# <a name="manual-package-download"></a><span data-ttu-id="abc32-103">Pakket handmatig downloaden</span><span class="sxs-lookup"><span data-stu-id="abc32-103">Manual Package Download</span></span>

<span data-ttu-id="abc32-104">De PowerShell Gallery ondersteunt het downloaden van een pakket van de website rechtstreeks, zonder gebruik te maken van de PowerShellGet-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="abc32-104">The PowerShell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="abc32-105">U kunt elk pakket downloaden als een NuGet package (`.nupkg`)-bestand, dat u vervolgens kunt kopiëren naar een interne opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="abc32-105">You can download any package as a NuGet package (`.nupkg`) file, which you can then copy to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="abc32-106">Hand matige pakket downloads is **niet** bedoeld als vervanging voor de `Install-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="abc32-106">Manual package download is **not** intended as a replacement for the `Install-Module` cmdlet.</span></span>
> <span data-ttu-id="abc32-107">Als u het pakket downloadt, wordt de module of het script niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="abc32-107">Downloading the package doesn't install the module or script.</span></span> <span data-ttu-id="abc32-108">Er zijn geen afhankelijkheden opgenomen in het NuGet-pakket dat is gedownload.</span><span class="sxs-lookup"><span data-stu-id="abc32-108">Dependencies aren't included in the NuGet package downloaded.</span></span> <span data-ttu-id="abc32-109">De volgende instructies zijn alleen bedoeld voor referentie doeleinden.</span><span class="sxs-lookup"><span data-stu-id="abc32-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="abc32-110">Hand matig downloaden gebruiken om een pakket te verkrijgen</span><span class="sxs-lookup"><span data-stu-id="abc32-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="abc32-111">Elke pagina heeft een koppeling voor hand matig downloaden, zoals hier wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="abc32-111">Each page has a link for Manual Download, as shown here:</span></span>

![Hand matig downloaden](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="abc32-113">Als u hand matig wilt downloaden, klikt u op **het onbewerkte nupkg-bestand downloaden**.</span><span class="sxs-lookup"><span data-stu-id="abc32-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="abc32-114">Er wordt een kopie van het pakket gekopieerd naar de downloadmap voor uw browser met de naam `<name>.<version>.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="abc32-114">A copy of the package is copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="abc32-115">Een NuGet-pakket is een ZIP-archief met extra bestanden met informatie over de inhoud van het pakket.</span><span class="sxs-lookup"><span data-stu-id="abc32-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="abc32-116">In sommige browsers, zoals Internet Explorer, wordt de `.nupkg` bestands extensie automatisch `.zip`vervangen door.</span><span class="sxs-lookup"><span data-stu-id="abc32-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="abc32-117">Als u het pakket wilt uitbreiden, `.nupkg` wijzigt u `.zip`de naam van het bestand in, indien nodig, en extraheert u vervolgens de inhoud naar een lokale map.</span><span class="sxs-lookup"><span data-stu-id="abc32-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="abc32-118">Een NuGet-pakket bestand bevat de volgende **NuGet-specifieke elementen** die geen deel uitmaken van de oorspronkelijke verpakte code:</span><span class="sxs-lookup"><span data-stu-id="abc32-118">A NuGet package file includes the following **NuGet-specific elements** that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="abc32-119">Een map met `_rels` de naam- `.rels` bevat een bestand waarin de afhankelijkheden worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="abc32-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="abc32-120">Een map met `package` de naam: bevat de NuGet gegevens</span><span class="sxs-lookup"><span data-stu-id="abc32-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="abc32-121">Een bestand met `[Content_Types].xml` de naam: beschrijft hoe extensies zoals PowerShellGet werken met NuGet</span><span class="sxs-lookup"><span data-stu-id="abc32-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="abc32-122">Een bestand met `<name>.nuspec` de naam: bevat het meren deel van de meta gegevens</span><span class="sxs-lookup"><span data-stu-id="abc32-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="abc32-123">Power shell-modules installeren vanuit een NuGet-pakket</span><span class="sxs-lookup"><span data-stu-id="abc32-123">Installing PowerShell modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="abc32-124">Deze instructies geven **niet** hetzelfde resultaat als het uitvoeren `Install-Module`van.</span><span class="sxs-lookup"><span data-stu-id="abc32-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="abc32-125">Deze instructies voldoen aan de minimale vereisten.</span><span class="sxs-lookup"><span data-stu-id="abc32-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="abc32-126">Deze zijn niet bedoeld als vervanging voor `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="abc32-126">They aren't intended to be a replacement for `Install-Module`.</span></span>
> <span data-ttu-id="abc32-127">Sommige stappen die worden `Install-Module` uitgevoerd door, zijn niet opgenomen.</span><span class="sxs-lookup"><span data-stu-id="abc32-127">Some steps performed by `Install-Module` aren't included.</span></span>

<span data-ttu-id="abc32-128">De eenvoudigste manier is om de NuGet-specifieke elementen uit de map te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="abc32-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="abc32-129">Als u de elementen verwijdert, blijft de Power shell-code die is gemaakt door de auteur van het pakket.</span><span class="sxs-lookup"><span data-stu-id="abc32-129">Removing the elements leaves the PowerShell code created by the package author.</span></span>
<span data-ttu-id="abc32-130">Zie voor de lijst met NuGet-elementen [hand matig downloaden gebruiken om een pakket te verkrijgen](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="abc32-130">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

<span data-ttu-id="abc32-131">De stappen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="abc32-131">The steps are as follows:</span></span>

1. <span data-ttu-id="abc32-132">Pak de inhoud van het NuGet-pakket uit naar een lokale map.</span><span class="sxs-lookup"><span data-stu-id="abc32-132">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="abc32-133">Verwijder de NuGet elementen uit de map.</span><span class="sxs-lookup"><span data-stu-id="abc32-133">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="abc32-134">Wijzig de naam van de map.</span><span class="sxs-lookup"><span data-stu-id="abc32-134">Rename the folder.</span></span> <span data-ttu-id="abc32-135">De naam van de standaardmap is `<name>.<version>`doorgaans.</span><span class="sxs-lookup"><span data-stu-id="abc32-135">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="abc32-136">De versie kan bevatten `-prerelease` als de module is gelabeld als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="abc32-136">The version can include `-prerelease` if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="abc32-137">Wijzig de naam van de map in alleen de module.</span><span class="sxs-lookup"><span data-stu-id="abc32-137">Rename the folder to just the module name.</span></span> <span data-ttu-id="abc32-138">Wordt bijvoorbeeld `azurerm.storage.5.0.4-preview`. `azurerm.storage`</span><span class="sxs-lookup"><span data-stu-id="abc32-138">For example, `azurerm.storage.5.0.4-preview` becomes `azurerm.storage`.</span></span>
4. <span data-ttu-id="abc32-139">Kopieer de map naar een van de mappen in de `$env:PSModulePath value`.</span><span class="sxs-lookup"><span data-stu-id="abc32-139">Copy the folder to one of the folders in the `$env:PSModulePath value`.</span></span> <span data-ttu-id="abc32-140">`$env:PSModulePath`is een door punt komma's gescheiden set paden waarin Power shell naar modules moet zoeken.</span><span class="sxs-lookup"><span data-stu-id="abc32-140">`$env:PSModulePath` is a semicolon-delimited set of paths in which PowerShell should look for modules.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abc32-141">De hand matige down load bevat geen afhankelijkheden die nodig zijn voor de module.</span><span class="sxs-lookup"><span data-stu-id="abc32-141">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="abc32-142">Als het pakket afhankelijkheden heeft, moeten deze op het systeem worden geïnstalleerd om deze module correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="abc32-142">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="abc32-143">Het PowerShell Gallery toont alle afhankelijkheden die vereist zijn voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="abc32-143">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="abc32-144">Power shell-scripts installeren vanuit een NuGet-pakket</span><span class="sxs-lookup"><span data-stu-id="abc32-144">Installing PowerShell scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="abc32-145">Deze instructies geven **niet** hetzelfde resultaat als het uitvoeren `Install-Script`van.</span><span class="sxs-lookup"><span data-stu-id="abc32-145">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="abc32-146">Deze instructies voldoen aan de minimale vereisten.</span><span class="sxs-lookup"><span data-stu-id="abc32-146">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="abc32-147">Deze zijn niet bedoeld als vervanging voor `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="abc32-147">They aren't intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="abc32-148">De eenvoudigste manier is om het NuGet-pakket uit te pakken en vervolgens het script rechtstreeks te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="abc32-148">The easiest approach is to extract the NuGet package, then use the script directly.</span></span>

<span data-ttu-id="abc32-149">De stappen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="abc32-149">The steps are as follows:</span></span>

1. <span data-ttu-id="abc32-150">Pak de inhoud van het NuGet-pakket uit.</span><span class="sxs-lookup"><span data-stu-id="abc32-150">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="abc32-151">Het `.PS1` bestand in de map kan rechtstreeks vanuit deze locatie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="abc32-151">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="abc32-152">U kunt de NuGet-specifieke elementen in de map verwijderen.</span><span class="sxs-lookup"><span data-stu-id="abc32-152">You may delete the NuGet-specific elements in the folder.</span></span>

<span data-ttu-id="abc32-153">Zie voor de lijst met NuGet-elementen [hand matig downloaden gebruiken om een pakket te verkrijgen](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="abc32-153">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abc32-154">De hand matige down load bevat geen afhankelijkheden die nodig zijn voor de module.</span><span class="sxs-lookup"><span data-stu-id="abc32-154">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="abc32-155">Als het pakket afhankelijkheden heeft, moeten deze op het systeem worden geïnstalleerd om deze module correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="abc32-155">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="abc32-156">Het PowerShell Gallery toont alle afhankelijkheden die vereist zijn voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="abc32-156">The PowerShell Gallery shows all dependencies required by the package.</span></span>