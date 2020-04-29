---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery, psget
title: Werken met lokale PSRepositories
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75415822"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="a8bba-103">Werken met PowerShellGet-privé-opslagplaatsen</span><span class="sxs-lookup"><span data-stu-id="a8bba-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="a8bba-104">De PowerShellGet-module ondersteunt andere opslag plaatsen dan de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a8bba-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="a8bba-105">Met deze cmdlets kunnen de volgende scenario's worden ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="a8bba-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="a8bba-106">Ondersteuning voor een vertrouwde, vooraf gevalideerde set Power shell-modules voor gebruik in uw omgeving</span><span class="sxs-lookup"><span data-stu-id="a8bba-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="a8bba-107">Een CI/CD-pijp lijn testen die Power shell-modules of-scripts bouwt</span><span class="sxs-lookup"><span data-stu-id="a8bba-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="a8bba-108">Power shell-scripts en-modules leveren aan systemen die geen toegang tot internet hebben</span><span class="sxs-lookup"><span data-stu-id="a8bba-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="a8bba-109">Power shell-scripts en-modules bieden die alleen beschikbaar zijn voor uw organisatie</span><span class="sxs-lookup"><span data-stu-id="a8bba-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="a8bba-110">In dit artikel wordt beschreven hoe u een lokale Power shell-opslag plaats instelt.</span><span class="sxs-lookup"><span data-stu-id="a8bba-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="a8bba-111">Het artikel heeft ook betrekking op de [OfflinePowerShellGetDeploy][] -module die beschikbaar is via de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a8bba-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="a8bba-112">Deze module bevat cmdlets voor het installeren van de meest recente versie van PowerShellGet in uw lokale opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="a8bba-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="a8bba-113">Typen lokale opslag plaats</span><span class="sxs-lookup"><span data-stu-id="a8bba-113">Local repository types</span></span>

<span data-ttu-id="a8bba-114">Er zijn twee manieren om een lokale PSRepository: NuGet-server of-bestands share te maken.</span><span class="sxs-lookup"><span data-stu-id="a8bba-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="a8bba-115">Elk type heeft voor-en nadelen:</span><span class="sxs-lookup"><span data-stu-id="a8bba-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="a8bba-116">NuGet-server</span><span class="sxs-lookup"><span data-stu-id="a8bba-116">NuGet Server</span></span>

| <span data-ttu-id="a8bba-117">Voordelen</span><span class="sxs-lookup"><span data-stu-id="a8bba-117">Advantages</span></span>| <span data-ttu-id="a8bba-118">Nadelen</span><span class="sxs-lookup"><span data-stu-id="a8bba-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="a8bba-119">PowerShellGallery-functionaliteit nauw keurig nabootsen</span><span class="sxs-lookup"><span data-stu-id="a8bba-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="a8bba-120">Voor een app met meerdere lagen is ondersteuning van operations-planning &</span><span class="sxs-lookup"><span data-stu-id="a8bba-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="a8bba-121">NuGet kan worden geïntegreerd met Visual Studio, andere hulpprogram ma's</span><span class="sxs-lookup"><span data-stu-id="a8bba-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="a8bba-122">Het verificatie model en het NuGet-account beheer zijn vereist</span><span class="sxs-lookup"><span data-stu-id="a8bba-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="a8bba-123">NuGet biedt ondersteuning voor `.Nupkg` meta gegevens in pakketten</span><span class="sxs-lookup"><span data-stu-id="a8bba-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="a8bba-124">Voor publiceren is API-sleutel beheer & onderhoud vereist</span><span class="sxs-lookup"><span data-stu-id="a8bba-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="a8bba-125">Biedt zoeken, pakket beheer, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="a8bba-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="a8bba-126">Bestandsshare</span><span class="sxs-lookup"><span data-stu-id="a8bba-126">File Share</span></span>

| <span data-ttu-id="a8bba-127">Voordelen</span><span class="sxs-lookup"><span data-stu-id="a8bba-127">Advantages</span></span>| <span data-ttu-id="a8bba-128">Nadelen</span><span class="sxs-lookup"><span data-stu-id="a8bba-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="a8bba-129">Eenvoudig in te stellen, back-ups te maken en te onderhouden</span><span class="sxs-lookup"><span data-stu-id="a8bba-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="a8bba-130">Meta gegevens die door PowerShellGet worden gebruikt, zijn niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="a8bba-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="a8bba-131">Eenvoudig beveiligings model: gebruikers machtigingen voor de share</span><span class="sxs-lookup"><span data-stu-id="a8bba-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="a8bba-132">Geen gebruikers interface buiten de basis bestands share</span><span class="sxs-lookup"><span data-stu-id="a8bba-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="a8bba-133">Geen beperkingen, zoals het vervangen van bestaande items</span><span class="sxs-lookup"><span data-stu-id="a8bba-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="a8bba-134">Beperkte beveiliging en geen opname van wie kan bijwerken wat er gebeurt</span><span class="sxs-lookup"><span data-stu-id="a8bba-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="a8bba-135">PowerShellGet werkt met beide typen en biedt ondersteuning voor het zoeken van versies en afhankelijkheids installatie.</span><span class="sxs-lookup"><span data-stu-id="a8bba-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="a8bba-136">Sommige functies die werken voor de PowerShell Gallery zijn echter niet beschikbaar voor basis NuGet-servers of-bestands shares.</span><span class="sxs-lookup"><span data-stu-id="a8bba-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="a8bba-137">Alles is een pakket-geen differentiatie van scripts, modules, DSC-resources of functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="a8bba-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="a8bba-138">Bestands share servers kunnen geen meta gegevens van pakketten zien, met inbegrip van tags.</span><span class="sxs-lookup"><span data-stu-id="a8bba-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="a8bba-139">Een lokale opslag plaats maken</span><span class="sxs-lookup"><span data-stu-id="a8bba-139">Creating a local repository</span></span>

<span data-ttu-id="a8bba-140">In het volgende artikel worden de stappen beschreven voor het instellen van uw eigen NuGet-server.</span><span class="sxs-lookup"><span data-stu-id="a8bba-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="a8bba-141">[NuGet. server][]</span><span class="sxs-lookup"><span data-stu-id="a8bba-141">[NuGet.Server][]</span></span>

<span data-ttu-id="a8bba-142">Volg de stappen tot en met het punt om pakketten toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="a8bba-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="a8bba-143">De stappen voor het [publiceren van een pakket](#publishing-to-a-local-repository) worden verderop in dit artikel besproken.</span><span class="sxs-lookup"><span data-stu-id="a8bba-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="a8bba-144">Zorg ervoor dat uw gebruikers machtigingen hebben voor toegang tot de bestands share voor een opslag plaats op basis van een bestands share.</span><span class="sxs-lookup"><span data-stu-id="a8bba-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="a8bba-145">Een lokale opslag plaats registreren</span><span class="sxs-lookup"><span data-stu-id="a8bba-145">Registering a local repository</span></span>

<span data-ttu-id="a8bba-146">Voordat een opslag plaats kan worden gebruikt, moet deze worden geregistreerd met `Register-PSRepository` behulp van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="a8bba-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="a8bba-147">In de onderstaande voor beelden wordt de **InstallationPolicy** ingesteld op *vertrouwd*, op de veronderstelling dat u uw eigen opslag plaats vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="a8bba-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="a8bba-148">Let op het verschil tussen hoe de twee opdrachten **ScriptSourceLocation**verwerken.</span><span class="sxs-lookup"><span data-stu-id="a8bba-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="a8bba-149">Voor opslag plaatsen op basis van een bestands share moeten de **SourceLocation** en **ScriptSourceLocation** overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="a8bba-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="a8bba-150">Voor een op het web gebaseerde opslag plaatsen moeten ze verschillend zijn, dus in dit voor beeld wordt een navolgende toegevoegd aan de **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="a8bba-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="a8bba-151">Als u de zojuist gemaakte PSRepository de standaard opslagplaats wilt maken, moet u de registratie van alle andere PSRepositories ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="a8bba-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="a8bba-152">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a8bba-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="a8bba-153">De naam van de opslag plaats ' PSGallery ' is gereserveerd voor gebruik door de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a8bba-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="a8bba-154">U kunt de registratie van PSGallery ongedaan maken, maar u kunt de naam PSGallery niet opnieuw gebruiken voor een andere opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="a8bba-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="a8bba-155">Als u de PSGallery wilt herstellen, voert u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="a8bba-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="a8bba-156">Publiceren naar een lokale opslag plaats</span><span class="sxs-lookup"><span data-stu-id="a8bba-156">Publishing to a local repository</span></span>

<span data-ttu-id="a8bba-157">Zodra u de lokale PSRepository hebt geregistreerd, kunt u publiceren naar uw lokale PSRepository.</span><span class="sxs-lookup"><span data-stu-id="a8bba-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="a8bba-158">Er zijn twee belang rijke scenario's: uw eigen module publiceren en een module publiceren vanuit de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="a8bba-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="a8bba-159">Een module publiceren die u hebt gemaakt</span><span class="sxs-lookup"><span data-stu-id="a8bba-159">Publishing a module you authored</span></span>

<span data-ttu-id="a8bba-160">Gebruik `Publish-Module` en `Publish-Script` om uw module te publiceren op uw lokale PSRepository op dezelfde manier als voor de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a8bba-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="a8bba-161">De locatie voor de code opgeven</span><span class="sxs-lookup"><span data-stu-id="a8bba-161">Specify the location for your code</span></span>
- <span data-ttu-id="a8bba-162">Een API-sleutel opgeven</span><span class="sxs-lookup"><span data-stu-id="a8bba-162">Supply an API key</span></span>
- <span data-ttu-id="a8bba-163">Geef de naam van de opslag plaats op.</span><span class="sxs-lookup"><span data-stu-id="a8bba-163">Specify the repository name.</span></span> <span data-ttu-id="a8bba-164">Bijvoorbeeld: `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="a8bba-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="a8bba-165">U moet een account maken op de NuGet-server en u vervolgens aanmelden om de API-sleutel te genereren en op te slaan.</span><span class="sxs-lookup"><span data-stu-id="a8bba-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="a8bba-166">Voor een bestands share gebruikt u een niet-lege teken reeks voor de waarde NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="a8bba-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="a8bba-167">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="a8bba-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="a8bba-168">Om de beveiliging te waarborgen, moeten API-sleutels niet in scripts worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="a8bba-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="a8bba-169">Gebruik een systeem voor beveiligd sleutel beheer.</span><span class="sxs-lookup"><span data-stu-id="a8bba-169">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="a8bba-170">Een module publiceren vanuit de PSGallery</span><span class="sxs-lookup"><span data-stu-id="a8bba-170">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="a8bba-171">Als u een module van de PSGallery naar uw lokale PSRepository wilt publiceren, kunt u de cmdlet Save-package gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a8bba-171">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="a8bba-172">De naam van het pakket opgeven</span><span class="sxs-lookup"><span data-stu-id="a8bba-172">Specify the Name of the Package</span></span>
- <span data-ttu-id="a8bba-173">Geef ' NuGet ' op als provider</span><span class="sxs-lookup"><span data-stu-id="a8bba-173">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="a8bba-174">Geef de locatie van de PSGallery op als de bron (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="a8bba-174">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="a8bba-175">Het pad naar uw lokale opslag plaats opgeven</span><span class="sxs-lookup"><span data-stu-id="a8bba-175">Specify the path to your local Repository</span></span>

<span data-ttu-id="a8bba-176">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a8bba-176">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="a8bba-177">Als uw lokale PSRepository is gebaseerd op het web, is er een extra stap nodig die gebruikmaakt van nuget. exe om te publiceren.</span><span class="sxs-lookup"><span data-stu-id="a8bba-177">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="a8bba-178">Raadpleeg de documentatie voor het gebruik van [nuget. exe][].</span><span class="sxs-lookup"><span data-stu-id="a8bba-178">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="a8bba-179">PowerShellGet installeren op een systeem zonder verbinding</span><span class="sxs-lookup"><span data-stu-id="a8bba-179">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="a8bba-180">Het implementeren van PowerShellGet is moeilijk in omgevingen waarin de verbinding van systemen met internet is vereist.</span><span class="sxs-lookup"><span data-stu-id="a8bba-180">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="a8bba-181">PowerShellGet heeft een Boots trap proces waarmee de nieuwste versie wordt geïnstalleerd wanneer deze voor de eerste keer wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a8bba-181">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="a8bba-182">De OfflinePowerShellGetDeploy-module in de PowerShell Gallery biedt cmdlets die dit Boots trap proces ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="a8bba-182">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="a8bba-183">Als u een offline-implementatie wilt Boots trappen, moet u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="a8bba-183">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="a8bba-184">Down load en installeer de OfflinePowerShellGetDeploy uw systeem met Internet verbinding en uw niet-verbonden systemen</span><span class="sxs-lookup"><span data-stu-id="a8bba-184">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="a8bba-185">PowerShellGet en de bijbehorende afhankelijkheden downloaden op het met internet verbonden systeem `Save-PowerShellGetForOffline` met behulp van de cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8bba-185">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="a8bba-186">PowerShellGet en de bijbehorende afhankelijkheden kopiëren van het systeem dat is verbonden met internet naar het niet-verbonden systeem</span><span class="sxs-lookup"><span data-stu-id="a8bba-186">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="a8bba-187">Gebruik de `Install-PowerShellGetOffline` op het niet-verbonden systeem om PowerShellGet en de bijbehorende afhankelijkheden in de juiste mappen te plaatsen</span><span class="sxs-lookup"><span data-stu-id="a8bba-187">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="a8bba-188">De volgende opdrachten gebruiken `Save-PowerShellGetForOffline` om alle onderdelen in een map te plaatsen`f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="a8bba-188">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="a8bba-189">Op dit moment moet u de inhoud van `F:\OfflinePowerShellGet` beschikbaar maken voor uw niet-verbonden systemen.</span><span class="sxs-lookup"><span data-stu-id="a8bba-189">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="a8bba-190">Voer de `Install-PowerShellGetOffline` cmdlet uit om PowerShellGet op het niet-verbonden systeem te installeren.</span><span class="sxs-lookup"><span data-stu-id="a8bba-190">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="a8bba-191">Het is belang rijk dat u PowerShellGet in de Power shell-sessie niet uitvoert voordat u deze opdrachten uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a8bba-191">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="a8bba-192">Zodra PowerShellGet in de sessie is geladen, kunnen de onderdelen niet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="a8bba-192">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="a8bba-193">Als u PowerShellGet per ongeluk start, sluit u Power shell af en start u het opnieuw.</span><span class="sxs-lookup"><span data-stu-id="a8bba-193">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="a8bba-194">Nadat u deze opdrachten hebt uitgevoerd, kunt u PowerShellGet publiceren naar uw lokale opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="a8bba-194">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="a8bba-195">Verpakkings oplossingen gebruiken voor het hosten van PowerShellGet-opslag plaatsen</span><span class="sxs-lookup"><span data-stu-id="a8bba-195">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="a8bba-196">U kunt ook verpakkings oplossingen zoals Azure-artefacten gebruiken om een persoonlijke of open bare PowerShellGet-opslag plaats te hosten.</span><span class="sxs-lookup"><span data-stu-id="a8bba-196">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="a8bba-197">Zie de [documentatie van Azure artefacten](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library)voor meer informatie en instructies.</span><span class="sxs-lookup"><span data-stu-id="a8bba-197">For more information and instructions, see the [Azure Artifacts documentation](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8bba-198">Om de beveiliging te waarborgen, moeten API-sleutels niet in scripts worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="a8bba-198">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="a8bba-199">Gebruik een systeem voor beveiligd sleutel beheer.</span><span class="sxs-lookup"><span data-stu-id="a8bba-199">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget. server]: /nuget/hosting-packages/nuget-server
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget. exe]: /nuget/tools/nuget-exe-cli-reference
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
