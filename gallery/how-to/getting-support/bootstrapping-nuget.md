---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Uitvoeren van de bootstrap NuGet
ms.openlocfilehash: f707e23737361ee7f82a16150402c9e719ee0ae1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221796"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="1c52d-103">De NuGet-provider en NuGet.exe bootstrap</span><span class="sxs-lookup"><span data-stu-id="1c52d-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="1c52d-104">NuGet.exe is niet opgenomen in de meest recente NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="1c52d-104">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="1c52d-105">Publiceren voor bewerkingen van een module of een script, PowerShellGet de binaire uitvoerbare NuGet.exe vereist.</span><span class="sxs-lookup"><span data-stu-id="1c52d-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="1c52d-106">Alleen de NuGet-provider vereist voor alle andere bewerkingen is, inclusief *vinden*, *installeren*, *opslaan*, en *verwijderen*.</span><span class="sxs-lookup"><span data-stu-id="1c52d-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="1c52d-107">PowerShellGet bevat de logica voor het afhandelen van hetzij een gecombineerde bootstrap van de NuGet-provider en NuGet.exe of bootstrap van alleen de NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="1c52d-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="1c52d-108">In beide gevallen wordt moet alleen een enkel bericht plaatsvinden.</span><span class="sxs-lookup"><span data-stu-id="1c52d-108">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="1c52d-109">Als de machine niet is verbonden met Internet, moet de gebruiker of beheerder een vertrouwde instantie van de NuGet-provider en/of het bestand NuGet.exe kopiëren naar de niet-verbonden computer.</span><span class="sxs-lookup"><span data-stu-id="1c52d-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

><span data-ttu-id="1c52d-110">**Opmerking**: vanaf versie 6, de NuGet-provider is opgenomen in de installatie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c52d-110">**Note**: Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="1c52d-111">Fout bij het oplossen van wanneer de NuGet-provider is niet geïnstalleerd op een computer waarop Internet is aangesloten</span><span class="sxs-lookup"><span data-stu-id="1c52d-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="1c52d-112">Fout bij het oplossen van wanneer de provider NuGet beschikbaar is en NuGet.exe is niet beschikbaar tijdens het publiceren op een computer waarop Internet is aangesloten</span><span class="sxs-lookup"><span data-stu-id="1c52d-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="1c52d-113">Fout bij het oplossen van wanneer zowel NuGet-provider en NuGet.exe zijn niet beschikbaar tijdens het publiceren op een computer waarop Internet is aangesloten</span><span class="sxs-lookup"><span data-stu-id="1c52d-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="1c52d-114">De NuGet-provider op een computer die niet is verbonden met Internet handmatig uitvoeren van de bootstrap</span><span class="sxs-lookup"><span data-stu-id="1c52d-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="1c52d-115">De processen aangetoond dat hierboven wordt ervan uitgegaan dat de computer is verbonden met Internet en bestanden kan downloaden vanaf een openbaar toegankelijke locatie.</span><span class="sxs-lookup"><span data-stu-id="1c52d-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="1c52d-116">Als dat niet mogelijk is, is de enige optie bootstrap van een machine met behulp van de bovenstaande processen en de provider handmatig kopiëren naar het geïsoleerde knooppunt via een vertrouwde offlineproces.</span><span class="sxs-lookup"><span data-stu-id="1c52d-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="1c52d-117">De meest voorkomende gebruiksvoorbeeld voor dit scenario is wanneer een persoonlijke galerie beschikbaar ter ondersteuning van een geïsoleerde omgeving.</span><span class="sxs-lookup"><span data-stu-id="1c52d-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="1c52d-118">Nadat u het proces hierboven voor een Internet verbonden machine bootstrap, vindt u provider-bestanden in de locatie:</span><span class="sxs-lookup"><span data-stu-id="1c52d-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="1c52d-119">De map/bestand structuur van de NuGet-provider zijn (mogelijk met een andere versienummer):</span><span class="sxs-lookup"><span data-stu-id="1c52d-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

<span data-ttu-id="1c52d-120">NuGet</span><span class="sxs-lookup"><span data-stu-id="1c52d-120">NuGet</span></span><br>
<span data-ttu-id="1c52d-121">--2.8.5.208</span><span class="sxs-lookup"><span data-stu-id="1c52d-121">--2.8.5.208</span></span><br>
<span data-ttu-id="1c52d-122">---Microsoft.PackageManagement.NuGetProvider.dll</span><span class="sxs-lookup"><span data-stu-id="1c52d-122">----Microsoft.PackageManagement.NuGetProvider.dll</span></span>

<span data-ttu-id="1c52d-123">Kopieer deze mappen en het bestand met een vertrouwd proces op de virtuele machines offline.</span><span class="sxs-lookup"><span data-stu-id="1c52d-123">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="1c52d-124">Bewerkingen op een machine die niet is verbonden met Internet NuGet.exe ter ondersteuning van handmatig uitvoeren van de bootstrap publiceren</span><span class="sxs-lookup"><span data-stu-id="1c52d-124">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="1c52d-125">Naast het proces van de provider NuGet handmatig bootstrap als de computer wordt gebruikt voor het publiceren van modules of scripts in een persoonlijke galerie met de *publiceren-Module* of *publiceren Script* -cmdlets het NuGet.exe binaire uitvoerbare bestand is vereist.</span><span class="sxs-lookup"><span data-stu-id="1c52d-125">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the *Publish-Module* or *Publish-Script* cmdlets, the NuGet.exe binary executable file will be required.</span></span>
<span data-ttu-id="1c52d-126">De meest voorkomende gebruiksvoorbeeld voor dit scenario is wanneer een persoonlijke galerie beschikbaar ter ondersteuning van een geïsoleerde omgeving.</span><span class="sxs-lookup"><span data-stu-id="1c52d-126">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="1c52d-127">Er zijn twee opties om op te halen van het bestand NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="1c52d-127">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="1c52d-128">Een mogelijkheid is het bootstrap van een machine die is verbonden met Internet en kopieer de bestanden naar de offline-machines met een vertrouwd proces.</span><span class="sxs-lookup"><span data-stu-id="1c52d-128">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="1c52d-129">Na het uitvoeren van de bootstrap de Internet verbonden machine, zich het binaire NuGet.exe bevindt in een van twee mappen:</span><span class="sxs-lookup"><span data-stu-id="1c52d-129">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="1c52d-130">Als de *publiceren-Module* of *publiceren Script* cmdlets zijn uitgevoerd met verhoogde machtigingen (als een Administrator):</span><span class="sxs-lookup"><span data-stu-id="1c52d-130">If the *Publish-Module* or *Publish-Script* cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="1c52d-131">Als de cmdlets zijn uitgevoerd als een gebruiker zonder verhoogde machtigingen:</span><span class="sxs-lookup"><span data-stu-id="1c52d-131">If the cmdlets were executed as a user without elevated permissions:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="1c52d-132">Er is een tweede optie NuGet.exe downloaden van de website NuGet.Org: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span><span class="sxs-lookup"><span data-stu-id="1c52d-132">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span></span><br>
<span data-ttu-id="1c52d-133">Als u een Nuget-versie voor productiemachines, zorg ervoor dat deze later is dan 2.8.5.208 en identificeren van de versie die zijn gelabeld 'aanbevolen'.</span><span class="sxs-lookup"><span data-stu-id="1c52d-133">When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="1c52d-134">Vergeet niet om de blokkering van het bestand als het is gedownload via een browser te.</span><span class="sxs-lookup"><span data-stu-id="1c52d-134">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="1c52d-135">Dit kan worden uitgevoerd met behulp van de *blokkering bestand* cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c52d-135">This can be performed by using the *Unblock-File* cmdlet.</span></span>

<span data-ttu-id="1c52d-136">In beide gevallen wordt het bestand NuGet.exe kan worden gekopieerd naar een locatie in *$env: pad*, maar de standaardlocaties zijn:</span><span class="sxs-lookup"><span data-stu-id="1c52d-136">In either case, the NuGet.exe file can be copied to any location in *$env:path*, but the standard locations are:</span></span>

<span data-ttu-id="1c52d-137">Het uitvoerbare bestand om beschikbaar te maken zodat alle gebruikers kunnen gebruiken *publiceren-Module* en *publiceren Script* cmdlets:</span><span class="sxs-lookup"><span data-stu-id="1c52d-137">To make the executable available so that all users can use *Publish-Module* and *Publish-Script* cmdlets:</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="1c52d-138">Als u het uitvoerbare bestand voor een specifieke gebruiker, kopiëren naar de locatie binnen alleen die gebruiker profiel:</span><span class="sxs-lookup"><span data-stu-id="1c52d-138">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```