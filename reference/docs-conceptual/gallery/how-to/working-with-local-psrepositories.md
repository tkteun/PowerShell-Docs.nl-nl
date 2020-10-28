---
ms.date: 11/06/2018
title: Werken met lokale PSRepositories
description: De PowerShellGet-module ondersteunt andere opslag plaatsen dan de PowerShell Gallery. In dit artikel wordt beschreven hoe u een lokale Power shell-opslag plaats instelt.
ms.openlocfilehash: 24a2fd23124b3897952d64a347d103d9ee10248f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662351"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="9f8b3-104">Werken met PowerShellGet-privé-opslagplaatsen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-104">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="9f8b3-105">De PowerShellGet-module ondersteunt andere opslag plaatsen dan de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-105">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="9f8b3-106">Met deze cmdlets kunnen de volgende scenario's worden ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="9f8b3-106">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="9f8b3-107">Ondersteuning voor een vertrouwde, vooraf gevalideerde set Power shell-modules voor gebruik in uw omgeving</span><span class="sxs-lookup"><span data-stu-id="9f8b3-107">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="9f8b3-108">Een CI/CD-pijp lijn testen die Power shell-modules of-scripts bouwt</span><span class="sxs-lookup"><span data-stu-id="9f8b3-108">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="9f8b3-109">Power shell-scripts en-modules leveren aan systemen die geen toegang tot internet hebben</span><span class="sxs-lookup"><span data-stu-id="9f8b3-109">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="9f8b3-110">Power shell-scripts en-modules bieden die alleen beschikbaar zijn voor uw organisatie</span><span class="sxs-lookup"><span data-stu-id="9f8b3-110">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="9f8b3-111">In dit artikel wordt beschreven hoe u een lokale Power shell-opslag plaats instelt.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-111">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="9f8b3-112">Het artikel heeft ook betrekking op de [OfflinePowerShellGetDeploy][] -module die beschikbaar is via de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-112">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="9f8b3-113">Deze module bevat cmdlets voor het installeren van de meest recente versie van PowerShellGet in uw lokale opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-113">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="9f8b3-114">Typen lokale opslag plaats</span><span class="sxs-lookup"><span data-stu-id="9f8b3-114">Local repository types</span></span>

<span data-ttu-id="9f8b3-115">Er zijn twee manieren om een lokale PSRepository: NuGet-server of-bestands share te maken.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-115">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="9f8b3-116">Elk type heeft voor-en nadelen:</span><span class="sxs-lookup"><span data-stu-id="9f8b3-116">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="9f8b3-117">NuGet-server</span><span class="sxs-lookup"><span data-stu-id="9f8b3-117">NuGet Server</span></span>

| <span data-ttu-id="9f8b3-118">Voordelen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-118">Advantages</span></span>| <span data-ttu-id="9f8b3-119">Nadelen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-119">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="9f8b3-120">PowerShellGallery-functionaliteit nauw keurig nabootsen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-120">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="9f8b3-121">Voor een app met meerdere lagen is ondersteuning van operations-planning &</span><span class="sxs-lookup"><span data-stu-id="9f8b3-121">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="9f8b3-122">NuGet kan worden geïntegreerd met Visual Studio, andere hulpprogram ma's</span><span class="sxs-lookup"><span data-stu-id="9f8b3-122">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="9f8b3-123">Het verificatie model en het NuGet-account beheer zijn vereist</span><span class="sxs-lookup"><span data-stu-id="9f8b3-123">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="9f8b3-124">NuGet biedt ondersteuning voor meta gegevens in `.Nupkg` pakketten</span><span class="sxs-lookup"><span data-stu-id="9f8b3-124">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="9f8b3-125">Voor publiceren is API-sleutel beheer & onderhoud vereist</span><span class="sxs-lookup"><span data-stu-id="9f8b3-125">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="9f8b3-126">Biedt zoeken, pakket beheer, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-126">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="9f8b3-127">Bestandsshare</span><span class="sxs-lookup"><span data-stu-id="9f8b3-127">File Share</span></span>

| <span data-ttu-id="9f8b3-128">Voordelen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-128">Advantages</span></span>| <span data-ttu-id="9f8b3-129">Nadelen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-129">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="9f8b3-130">Eenvoudig in te stellen, back-ups te maken en te onderhouden</span><span class="sxs-lookup"><span data-stu-id="9f8b3-130">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="9f8b3-131">Meta gegevens die door PowerShellGet worden gebruikt, zijn niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="9f8b3-131">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="9f8b3-132">Eenvoudig beveiligings model: gebruikers machtigingen voor de share</span><span class="sxs-lookup"><span data-stu-id="9f8b3-132">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="9f8b3-133">Geen gebruikers interface buiten de basis bestands share</span><span class="sxs-lookup"><span data-stu-id="9f8b3-133">No UI beyond basic file share</span></span> |
| <span data-ttu-id="9f8b3-134">Geen beperkingen, zoals het vervangen van bestaande items</span><span class="sxs-lookup"><span data-stu-id="9f8b3-134">No constraints such as replacing existing items</span></span> | <span data-ttu-id="9f8b3-135">Beperkte beveiliging en geen opname van wie kan bijwerken wat er gebeurt</span><span class="sxs-lookup"><span data-stu-id="9f8b3-135">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="9f8b3-136">PowerShellGet werkt met beide typen en biedt ondersteuning voor het zoeken van versies en afhankelijkheids installatie.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-136">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="9f8b3-137">Sommige functies die werken voor de PowerShell Gallery zijn echter niet beschikbaar voor basis NuGet-servers of-bestands shares.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-137">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="9f8b3-138">Alles is een pakket-geen differentiatie van scripts, modules, DSC-resources of functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-138">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="9f8b3-139">Bestands share servers kunnen geen meta gegevens van pakketten zien, met inbegrip van tags.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-139">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="9f8b3-140">Een lokale opslag plaats maken</span><span class="sxs-lookup"><span data-stu-id="9f8b3-140">Creating a local repository</span></span>

<span data-ttu-id="9f8b3-141">In het volgende artikel worden de stappen beschreven voor het instellen van uw eigen NuGet-server.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-141">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="9f8b3-142">[NuGet. server][]</span><span class="sxs-lookup"><span data-stu-id="9f8b3-142">[NuGet.Server][]</span></span>

<span data-ttu-id="9f8b3-143">Volg de stappen tot en met het punt om pakketten toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-143">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="9f8b3-144">De stappen voor het [publiceren van een pakket](#publishing-to-a-local-repository) worden verderop in dit artikel besproken.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-144">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="9f8b3-145">Zorg ervoor dat uw gebruikers machtigingen hebben voor toegang tot de bestands share voor een opslag plaats op basis van een bestands share.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-145">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="9f8b3-146">Een lokale opslag plaats registreren</span><span class="sxs-lookup"><span data-stu-id="9f8b3-146">Registering a local repository</span></span>

<span data-ttu-id="9f8b3-147">Voordat een opslag plaats kan worden gebruikt, moet deze worden geregistreerd met behulp van de `Register-PSRepository` opdracht.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-147">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="9f8b3-148">In de onderstaande voor beelden wordt de **InstallationPolicy** ingesteld op *vertrouwd* , op de veronderstelling dat u uw eigen opslag plaats vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-148">In the examples below, the **InstallationPolicy** is set to *Trusted* , on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="9f8b3-149">Let op het verschil tussen hoe de twee opdrachten **ScriptSourceLocation** verwerken.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-149">Take note of the difference between how the two commands handle **ScriptSourceLocation** .</span></span> <span data-ttu-id="9f8b3-150">Voor opslag plaatsen op basis van een bestands share moeten de **SourceLocation** en **ScriptSourceLocation** overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-150">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="9f8b3-151">Voor een op het web gebaseerde opslag plaatsen moeten ze verschillend zijn, dus in dit voor beeld wordt een navolgende toegevoegd aan de **SourceLocation** .</span><span class="sxs-lookup"><span data-stu-id="9f8b3-151">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation** .</span></span>

<span data-ttu-id="9f8b3-152">Als u de zojuist gemaakte PSRepository de standaard opslagplaats wilt maken, moet u de registratie van alle andere PSRepositories ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-152">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="9f8b3-153">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9f8b3-153">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="9f8b3-154">De naam van de opslag plaats ' PSGallery ' is gereserveerd voor gebruik door de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-154">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="9f8b3-155">U kunt de registratie van PSGallery ongedaan maken, maar u kunt de naam PSGallery niet opnieuw gebruiken voor een andere opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-155">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="9f8b3-156">Als u de PSGallery wilt herstellen, voert u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="9f8b3-156">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="9f8b3-157">Publiceren naar een lokale opslag plaats</span><span class="sxs-lookup"><span data-stu-id="9f8b3-157">Publishing to a local repository</span></span>

<span data-ttu-id="9f8b3-158">Zodra u de lokale PSRepository hebt geregistreerd, kunt u publiceren naar uw lokale PSRepository.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-158">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="9f8b3-159">Er zijn twee belang rijke scenario's: uw eigen module publiceren en een module publiceren vanuit de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-159">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="9f8b3-160">Een module publiceren die u hebt gemaakt</span><span class="sxs-lookup"><span data-stu-id="9f8b3-160">Publishing a module you authored</span></span>

<span data-ttu-id="9f8b3-161">Gebruik `Publish-Module` en `Publish-Script` om uw module te publiceren op uw lokale PSRepository op dezelfde manier als voor de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-161">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="9f8b3-162">De locatie voor de code opgeven</span><span class="sxs-lookup"><span data-stu-id="9f8b3-162">Specify the location for your code</span></span>
- <span data-ttu-id="9f8b3-163">Een API-sleutel opgeven</span><span class="sxs-lookup"><span data-stu-id="9f8b3-163">Supply an API key</span></span>
- <span data-ttu-id="9f8b3-164">Geef de naam van de opslag plaats op.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-164">Specify the repository name.</span></span> <span data-ttu-id="9f8b3-165">Bijvoorbeeld: `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="9f8b3-165">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="9f8b3-166">U moet een account maken op de NuGet-server en u vervolgens aanmelden om de API-sleutel te genereren en op te slaan.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-166">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="9f8b3-167">Voor een bestands share gebruikt u een niet-lege teken reeks voor de waarde NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-167">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="9f8b3-168">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="9f8b3-168">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="9f8b3-169">Om de beveiliging te waarborgen, moeten API-sleutels niet in scripts worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-169">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="9f8b3-170">Gebruik een systeem voor beveiligd sleutel beheer.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-170">Use a secure key management system.</span></span> <span data-ttu-id="9f8b3-171">Wanneer u een opdracht hand matig uitvoert, moeten de API-sleutels niet worden door gegeven als onbewerkte tekst om te voor komen dat deze wordt geregistreerd `Read-Host` . de cmdlet kan worden gebruikt om de waarde van de API-sleutel veilig door te geven.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-171">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="9f8b3-172">Een module publiceren vanuit de PSGallery</span><span class="sxs-lookup"><span data-stu-id="9f8b3-172">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="9f8b3-173">Als u een module van de PSGallery naar uw lokale PSRepository wilt publiceren, kunt u de cmdlet Save-package gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-173">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="9f8b3-174">De naam van het pakket opgeven</span><span class="sxs-lookup"><span data-stu-id="9f8b3-174">Specify the Name of the Package</span></span>
- <span data-ttu-id="9f8b3-175">Geef ' NuGet ' op als provider</span><span class="sxs-lookup"><span data-stu-id="9f8b3-175">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="9f8b3-176">Geef de locatie van de PSGallery op als de bron (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="9f8b3-176">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="9f8b3-177">Het pad naar uw lokale opslag plaats opgeven</span><span class="sxs-lookup"><span data-stu-id="9f8b3-177">Specify the path to your local Repository</span></span>

<span data-ttu-id="9f8b3-178">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9f8b3-178">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="9f8b3-179">Als uw lokale PSRepository is gebaseerd op het web, hebt u een extra stap nodig die gebruikmaakt van nuget.exe om te publiceren.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-179">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="9f8b3-180">Raadpleeg de documentatie voor het gebruik van [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="9f8b3-180">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="9f8b3-181">PowerShellGet installeren op een systeem zonder verbinding</span><span class="sxs-lookup"><span data-stu-id="9f8b3-181">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="9f8b3-182">Het implementeren van PowerShellGet is moeilijk in omgevingen waarin de verbinding van systemen met internet is vereist.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-182">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="9f8b3-183">PowerShellGet heeft een Boots trap proces waarmee de nieuwste versie wordt geïnstalleerd wanneer deze voor de eerste keer wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-183">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="9f8b3-184">De OfflinePowerShellGetDeploy-module in de PowerShell Gallery biedt cmdlets die dit Boots trap proces ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-184">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="9f8b3-185">Als u een offline-implementatie wilt Boots trappen, moet u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="9f8b3-185">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="9f8b3-186">Down load en installeer de OfflinePowerShellGetDeploy uw systeem met Internet verbinding en uw niet-verbonden systemen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-186">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="9f8b3-187">PowerShellGet en de bijbehorende afhankelijkheden downloaden op het met internet verbonden systeem met behulp van de `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f8b3-187">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="9f8b3-188">PowerShellGet en de bijbehorende afhankelijkheden kopiëren van het systeem dat is verbonden met internet naar het niet-verbonden systeem</span><span class="sxs-lookup"><span data-stu-id="9f8b3-188">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="9f8b3-189">Gebruik de `Install-PowerShellGetOffline` op het niet-verbonden systeem om PowerShellGet en de bijbehorende afhankelijkheden in de juiste mappen te plaatsen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-189">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="9f8b3-190">De volgende opdrachten gebruiken `Save-PowerShellGetForOffline` om alle onderdelen in een map te plaatsen `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="9f8b3-190">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="9f8b3-191">Op dit moment moet u de inhoud van beschikbaar maken `F:\OfflinePowerShellGet` voor uw niet-verbonden systemen.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-191">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="9f8b3-192">Voer de `Install-PowerShellGetOffline` cmdlet uit om PowerShellGet op het niet-verbonden systeem te installeren.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-192">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="9f8b3-193">Het is belang rijk dat u PowerShellGet in de Power shell-sessie niet uitvoert voordat u deze opdrachten uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-193">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="9f8b3-194">Zodra PowerShellGet in de sessie is geladen, kunnen de onderdelen niet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-194">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="9f8b3-195">Als u PowerShellGet per ongeluk start, sluit u Power shell af en start u het opnieuw.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-195">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="9f8b3-196">Nadat u deze opdrachten hebt uitgevoerd, kunt u PowerShellGet publiceren naar uw lokale opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-196">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey $nuGetApiKey
```

> [!IMPORTANT]
> <span data-ttu-id="9f8b3-197">Om de beveiliging te waarborgen, moeten API-sleutels niet in scripts worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-197">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="9f8b3-198">Gebruik een systeem voor beveiligd sleutel beheer.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-198">Use a secure key management system.</span></span> <span data-ttu-id="9f8b3-199">Wanneer u een opdracht hand matig uitvoert, moeten de API-sleutels niet worden door gegeven als onbewerkte tekst om te voor komen dat deze wordt geregistreerd `Read-Host` . de cmdlet kan worden gebruikt om de waarde van de API-sleutel veilig door te geven.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-199">When executing a command manually, API keys should not be passed as plain-text to avoid it being logged, the `Read-Host` cmdlet can be used to safely pass the value of the API key.</span></span>

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="9f8b3-200">Verpakkings oplossingen gebruiken voor het hosten van PowerShellGet-opslag plaatsen</span><span class="sxs-lookup"><span data-stu-id="9f8b3-200">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="9f8b3-201">U kunt ook verpakkings oplossingen zoals Azure-artefacten gebruiken om een persoonlijke of open bare PowerShellGet-opslag plaats te hosten.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-201">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="9f8b3-202">Zie de [documentatie van Azure artefacten](/azure/devops/artifacts/tutorials/private-powershell-library)voor meer informatie en instructies.</span><span class="sxs-lookup"><span data-stu-id="9f8b3-202">For more information and instructions, see the [Azure Artifacts documentation](/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget. server]: /nuget/hosting-packages/nuget-server
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
