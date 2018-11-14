---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery, psget
title: Werken met lokale PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619252"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="fab1f-103">Werken met lokale PowerShellGet-opslagplaatsen</span><span class="sxs-lookup"><span data-stu-id="fab1f-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="fab1f-104">De PowerShellGet-module-ondersteuning-opslagplaatsen dan de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="fab1f-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="fab1f-105">Deze cmdlets kunt de volgende scenario's:</span><span class="sxs-lookup"><span data-stu-id="fab1f-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="fab1f-106">Ondersteuning voor een vertrouwd en vooraf gevalideerde set PowerShell-modules voor gebruik in uw omgeving</span><span class="sxs-lookup"><span data-stu-id="fab1f-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="fab1f-107">Een CI/CD-pijplijn die PowerShell-modules of scripts voortbouwt testen</span><span class="sxs-lookup"><span data-stu-id="fab1f-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="fab1f-108">PowerShell-scripts en modules leveren voor systemen die geen toegang internet tot</span><span class="sxs-lookup"><span data-stu-id="fab1f-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="fab1f-109">Dit artikel wordt beschreven hoe u een lokale PowerShell-opslagplaats kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="fab1f-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="fab1f-110">Het artikel ook aandacht besteed aan het [OfflinePowerShellGetDeploy][] module die beschikbaar zijn vanuit de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="fab1f-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="fab1f-111">Deze module bevat cmdlets voor het installeren van de meest recente versie van PowerShellGet in uw lokale opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="fab1f-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="fab1f-112">Typen van de lokale opslagplaats</span><span class="sxs-lookup"><span data-stu-id="fab1f-112">Local repository types</span></span>

<span data-ttu-id="fab1f-113">Er zijn twee manieren om te maken van een lokale PSRepository: NuGet-server of de bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="fab1f-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="fab1f-114">Elk type heeft voor- en nadelen:</span><span class="sxs-lookup"><span data-stu-id="fab1f-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="fab1f-115">NuGet-Server</span><span class="sxs-lookup"><span data-stu-id="fab1f-115">NuGet Server</span></span>

| <span data-ttu-id="fab1f-116">Voordelen</span><span class="sxs-lookup"><span data-stu-id="fab1f-116">Advantages</span></span>| <span data-ttu-id="fab1f-117">Nadelen</span><span class="sxs-lookup"><span data-stu-id="fab1f-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="fab1f-118">Komt sterk overeen PowerShellGallery-functionaliteit</span><span class="sxs-lookup"><span data-stu-id="fab1f-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="fab1f-119">App met meerdere lagen vereist planning bewerkingen en ondersteuning</span><span class="sxs-lookup"><span data-stu-id="fab1f-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="fab1f-120">NuGet kan worden geïntegreerd met Visual Studio, andere hulpprogramma 's</span><span class="sxs-lookup"><span data-stu-id="fab1f-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="fab1f-121">Verificatiemodel en NuGet-accounts beheren die nodig zijn</span><span class="sxs-lookup"><span data-stu-id="fab1f-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="fab1f-122">NuGet biedt ondersteuning voor metagegevens in `.Nupkg` pakketten</span><span class="sxs-lookup"><span data-stu-id="fab1f-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="fab1f-123">Publicatie moet de API-sleutel en -onderhoud</span><span class="sxs-lookup"><span data-stu-id="fab1f-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="fab1f-124">Biedt zoeken, Pakketbeheer, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="fab1f-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="fab1f-125">Bestandsshare</span><span class="sxs-lookup"><span data-stu-id="fab1f-125">File Share</span></span>

| <span data-ttu-id="fab1f-126">Voordelen</span><span class="sxs-lookup"><span data-stu-id="fab1f-126">Advantages</span></span>| <span data-ttu-id="fab1f-127">Nadelen</span><span class="sxs-lookup"><span data-stu-id="fab1f-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="fab1f-128">Eenvoudig instellen, back-up maken en onderhouden</span><span class="sxs-lookup"><span data-stu-id="fab1f-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="fab1f-129">Metagegevens die worden gebruikt door de PowerShellGet is niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="fab1f-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="fab1f-130">Eenvoudige beveiligingsmodel - gebruikersmachtigingen voor de share</span><span class="sxs-lookup"><span data-stu-id="fab1f-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="fab1f-131">Er is geen gebruikersinterface naast basisopdrachten voor bestandsbeheer delen</span><span class="sxs-lookup"><span data-stu-id="fab1f-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="fab1f-132">Er zijn geen beperkingen, zoals bestaande artikelen vervangen</span><span class="sxs-lookup"><span data-stu-id="fab1f-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="fab1f-133">Beperkte beveiliging en geen de opname van wie wat bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="fab1f-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="fab1f-134">PowerShellGet werkt met het type en ondersteunt versies en de installatie van afhankelijkheid te zoeken.</span><span class="sxs-lookup"><span data-stu-id="fab1f-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="fab1f-135">Sommige functies die voor de PowerShell Gallery werken zijn echter niet beschikbaar voor basis NuGet-servers of -bestandsshares.</span><span class="sxs-lookup"><span data-stu-id="fab1f-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="fab1f-136">Alles wat is een pakket - niet differentiatie van scripts, modules, DSC-resources of rolmogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="fab1f-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="fab1f-137">Share bestandsservers kunnen pakketmetagegevens, met inbegrip van tags niet zien.</span><span class="sxs-lookup"><span data-stu-id="fab1f-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="fab1f-138">Het maken van een lokale opslagplaats</span><span class="sxs-lookup"><span data-stu-id="fab1f-138">Creating a local repository</span></span>

<span data-ttu-id="fab1f-139">Het volgende artikel vindt u de stappen voor het instellen van uw eigen NuGet-Server.</span><span class="sxs-lookup"><span data-stu-id="fab1f-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="fab1f-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="fab1f-140">[NuGet.Server][]</span></span>

<span data-ttu-id="fab1f-141">Volg de stappen tot het moment van het toevoegen van pakketten.</span><span class="sxs-lookup"><span data-stu-id="fab1f-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="fab1f-142">De stappen voor het [publiceren van een pakket](#publishing-to-a-local-repository) verderop in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="fab1f-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="fab1f-143">Voor een bestand op basis van een share-opslagplaats, ervoor zorgen dat uw gebruikers machtigingen hebben voor toegang tot de bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="fab1f-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="fab1f-144">Een lokale opslagplaats registreren</span><span class="sxs-lookup"><span data-stu-id="fab1f-144">Registering a local repository</span></span>

<span data-ttu-id="fab1f-145">Voordat een opslagplaats kan worden gebruikt, moet deze worden geregistreerd met behulp van de `Register-PSRepository` opdracht.</span><span class="sxs-lookup"><span data-stu-id="fab1f-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="fab1f-146">In de onderstaande voorbeelden de **InstallationPolicy** is ingesteld op *vertrouwde*, op de veronderstelling dat u uw eigen opslagplaats vertrouwen.</span><span class="sxs-lookup"><span data-stu-id="fab1f-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="fab1f-147">Noteer het verschil tussen hoe de twee opdrachten verwerkt **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="fab1f-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="fab1f-148">Voor een bestand op basis van een share-opslagplaatsen, de **SourceLocation** en **ScriptSourceLocation** moeten overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="fab1f-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="fab1f-149">Een website op basis van-opslagplaats, moeten ze verschillend zijn, dus in dit voorbeeld een afsluitende '/' wordt toegevoegd aan de **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="fab1f-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="fab1f-150">Als u wilt dat de zojuist gemaakte PSRepository moet de standaard-opslagplaats, moet u de registratie ongedaan maken voor alle andere PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="fab1f-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="fab1f-151">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fab1f-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="fab1f-152">De naam van de opslagplaats 'PSGallery' is gereserveerd voor gebruik door de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="fab1f-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="fab1f-153">U kunt de registratie ongedaan maken PSGallery, maar u kunt de naam PSGallery voor een andere opslagplaats niet opnieuw gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fab1f-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="fab1f-154">Als u herstellen van de PSGallery wilt, voert u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="fab1f-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="fab1f-155">Publiceren naar een lokale opslagplaats</span><span class="sxs-lookup"><span data-stu-id="fab1f-155">Publishing to a local repository</span></span>

<span data-ttu-id="fab1f-156">Zodra u de lokale PSRepository hebt geregistreerd, kunt u publiceren op uw lokale PSRepository.</span><span class="sxs-lookup"><span data-stu-id="fab1f-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="fab1f-157">Er zijn twee hoofdscenario publishing's: uw eigen module publiceren en publiceren van een module op basis van de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="fab1f-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="fab1f-158">Publiceren van een module die u gemaakt</span><span class="sxs-lookup"><span data-stu-id="fab1f-158">Publishing a module you authored</span></span>

<span data-ttu-id="fab1f-159">Gebruik `Publish-Module` en `Publish-Script` uw module publiceren naar uw lokale PSRepository de dezelfde manier als voor de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="fab1f-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="fab1f-160">Geef de locatie voor uw code</span><span class="sxs-lookup"><span data-stu-id="fab1f-160">Specify the location for your code</span></span>
- <span data-ttu-id="fab1f-161">Een API-sleutel opgeven</span><span class="sxs-lookup"><span data-stu-id="fab1f-161">Supply an API key</span></span>
- <span data-ttu-id="fab1f-162">Geef de naam van de opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="fab1f-162">Specify the repository name.</span></span> <span data-ttu-id="fab1f-163">bijvoorbeeld `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="fab1f-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="fab1f-164">U moet een account maken in de NuGet-server en meld u aan om te genereren en opslaan van de API-sleutel.</span><span class="sxs-lookup"><span data-stu-id="fab1f-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="fab1f-165">Gebruik een niet-lege tekenreeks voor de NuGetApiKey-waarde voor een bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="fab1f-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="fab1f-166">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="fab1f-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="fab1f-167">Om beveiliging te waarborgen, mag API-sleutels niet zijn hardgecodeerd in scripts.</span><span class="sxs-lookup"><span data-stu-id="fab1f-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="fab1f-168">Een systeem veilig Sleutelbeheer gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fab1f-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="fab1f-169">Een module op basis van de PSGallery publiceren</span><span class="sxs-lookup"><span data-stu-id="fab1f-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="fab1f-170">Voor het publiceren van een module op basis van de PSGallery naar uw lokale PSRepository, kunt u de cmdlet 'Opslaan-Package'.</span><span class="sxs-lookup"><span data-stu-id="fab1f-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="fab1f-171">Geef de naam van het pakket</span><span class="sxs-lookup"><span data-stu-id="fab1f-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="fab1f-172">'NuGet' opgeven als de Provider</span><span class="sxs-lookup"><span data-stu-id="fab1f-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="fab1f-173">De locatie PSGallery opgeven als de bron (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="fab1f-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="fab1f-174">Geef het pad op naar uw lokale opslagplaats</span><span class="sxs-lookup"><span data-stu-id="fab1f-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="fab1f-175">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fab1f-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="fab1f-176">Als uw lokale PSRepository webgebaseerde, hiervoor een extra stap die gebruikmaakt van nuget.exe om te publiceren.</span><span class="sxs-lookup"><span data-stu-id="fab1f-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="fab1f-177">Zie de documentatie voor het gebruik van [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="fab1f-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="fab1f-178">PowerShellGet installeren op een niet-verbonden systeem</span><span class="sxs-lookup"><span data-stu-id="fab1f-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="fab1f-179">PowerShellGet implementeren is het moeilijk in omgevingen waarvoor systemen worden losgekoppeld van het internet.</span><span class="sxs-lookup"><span data-stu-id="fab1f-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="fab1f-180">PowerShellGet heeft een bootstrap proces dat de eerste keer dat deze wordt gebruikt voor de meest recente versie installeert.</span><span class="sxs-lookup"><span data-stu-id="fab1f-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="fab1f-181">De module OfflinePowerShellGetDeploy in de PowerShell Gallery bevat cmdlets die ondersteuning bieden voor deze bootstrap-proces.</span><span class="sxs-lookup"><span data-stu-id="fab1f-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="fab1f-182">Als u wilt de implementatie van een offline bootstrap, moet u naar:</span><span class="sxs-lookup"><span data-stu-id="fab1f-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="fab1f-183">Download en installeer het systeem OfflinePowerShellGetDeploy uw internetverbinding en uw niet-verbonden systemen</span><span class="sxs-lookup"><span data-stu-id="fab1f-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="fab1f-184">Downloaden van PowerShellGet en de bijbehorende afhankelijkheden op het internet verbonden systeem gebruikt de `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="fab1f-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="fab1f-185">PowerShellGet en de bijbehorende afhankelijkheden van het internet verbonden systeem naar het niet-verbonden systeem kopiëren</span><span class="sxs-lookup"><span data-stu-id="fab1f-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="fab1f-186">Gebruik de `Install-PowerShellGetOffline` op het niet-verbonden systeem PowerShellGet en de bijbehorende afhankelijkheden in de juiste mappen plaatsen</span><span class="sxs-lookup"><span data-stu-id="fab1f-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="fab1f-187">De volgende opdrachten gebruikt `Save-PowerShellGetForOffline` om alle onderdelen in een map `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="fab1f-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="fab1f-188">Op dit moment moet u de inhoud van `F:\OfflinePowerShellGet` beschikbaar zijn voor uw niet-verbonden systemen.</span><span class="sxs-lookup"><span data-stu-id="fab1f-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="fab1f-189">Voer de `Install-PowerShellGetOffline` cmdlet PowerShellGet installeren op de niet-verbonden systeem.</span><span class="sxs-lookup"><span data-stu-id="fab1f-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="fab1f-190">Het is belangrijk dat u niet PowerShellGet in de PowerShell-sessie uitvoert voordat u deze opdrachten uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fab1f-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="fab1f-191">Zodra de PowerShellGet in de sessie is geladen, kunnen de onderdelen kunnen niet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="fab1f-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="fab1f-192">Als u PowerShellGet per ongeluk starten, afsluiten en opnieuw opstarten van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fab1f-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="fab1f-193">Na het uitvoeren van deze opdrachten, bent u klaar om te publiceren PowerShellGet op uw lokale opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="fab1f-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="fab1f-194">Om beveiliging te waarborgen, mag API-sleutels niet zijn hardgecodeerd in scripts.</span><span class="sxs-lookup"><span data-stu-id="fab1f-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="fab1f-195">Een systeem veilig Sleutelbeheer gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fab1f-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
