---
ms.date: 06/12/2017
keywords: Galerie, Power shell, cmdlet, psget
title: Boots trap-NuGet
ms.openlocfilehash: 70403006c7a48ac70a6766de3aa52d80cebbd86a
ms.sourcegitcommit: 1fa89ab20d14a61f139f1394c45aaedd5a7c5438
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/09/2020
ms.locfileid: "78935168"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="d1b92-103">Boots trap de NuGet-provider en NuGet. exe</span><span class="sxs-lookup"><span data-stu-id="d1b92-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="d1b92-104">NuGet. exe is niet opgenomen in de meest recente NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="d1b92-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="d1b92-105">Voor publicatie bewerkingen van een module of script is PowerShellGet vereist voor het binaire uitvoer bare bestand **NuGet. exe**.</span><span class="sxs-lookup"><span data-stu-id="d1b92-105">For publish operations of either a module or script, PowerShellGet requires the binary executable **NuGet.exe**.</span></span> <span data-ttu-id="d1b92-106">Alleen de NuGet-provider is vereist voor alle andere bewerkingen, zoals **zoeken**, **installeren**, **Opslaan**en **verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="d1b92-106">Only the NuGet provider is required for all other operations, including **find**, **install**, **save**, and **uninstall**.</span></span>
<span data-ttu-id="d1b92-107">PowerShellGet bevat logica voor het afhandelen van een gecombineerde Boots trap van de NuGet-provider en NuGet. exe, of voor Boots trap van alleen de NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="d1b92-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="d1b92-108">In beide gevallen moet er slechts één prompt bericht worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d1b92-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="d1b92-109">Als de computer niet is verbonden met internet, moet de gebruiker of een beheerder een vertrouwd exemplaar van de NuGet-provider en/of het bestand NuGet. exe naar de niet-verbonden computer kopiëren.</span><span class="sxs-lookup"><span data-stu-id="d1b92-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="d1b92-110">Vanaf versie 6 wordt de NuGet-provider opgenomen in de installatie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="d1b92-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="d1b92-111">Fout oplossen wanneer de NuGet-provider niet is geïnstalleerd op een computer die is verbonden met Internet</span><span class="sxs-lookup"><span data-stu-id="d1b92-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="d1b92-112">Fout bij het oplossen van het probleem wanneer de NuGet-provider beschikbaar is en NuGet. exe niet beschikbaar is tijdens de publicatie bewerking op een computer die is verbonden met Internet</span><span class="sxs-lookup"><span data-stu-id="d1b92-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="d1b92-113">Fout bij het oplossen van problemen wanneer zowel de NuGet-provider als NuGet. exe tijdens de publicatie niet beschikbaar zijn op een computer die is verbonden met Internet</span><span class="sxs-lookup"><span data-stu-id="d1b92-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
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
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="d1b92-114">De NuGet-provider hand matig Boots trappen op een computer die niet is verbonden met Internet</span><span class="sxs-lookup"><span data-stu-id="d1b92-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="d1b92-115">In de processen die hierboven worden beschreven, wordt ervan uitgegaan dat de machine is verbonden met internet en dat er bestanden kunnen worden gedownload vanaf een open bare locatie.</span><span class="sxs-lookup"><span data-stu-id="d1b92-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="d1b92-116">Als dat niet mogelijk is, kunt u het beste een Boots trap uitvoeren op een machine met behulp van de hierboven genoemde processen en de provider hand matig kopiëren naar het geïsoleerde knoop punt via een offline vertrouwd proces.</span><span class="sxs-lookup"><span data-stu-id="d1b92-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="d1b92-117">De meest voorkomende use-case voor dit scenario is wanneer een persoonlijke galerie beschikbaar is voor de ondersteuning van een geïsoleerde omgeving.</span><span class="sxs-lookup"><span data-stu-id="d1b92-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="d1b92-118">Nadat u het bovenstaande proces hebt uitgevoerd om een computer met een Internet verbinding te Boots trappen, vindt u de bestanden van de provider op de volgende locatie:</span><span class="sxs-lookup"><span data-stu-id="d1b92-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="d1b92-119">De structuur van de map of het bestand van de NuGet-provider is (mogelijk met een ander versie nummer):</span><span class="sxs-lookup"><span data-stu-id="d1b92-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="d1b92-120">Kopieer deze mappen en dit bestand met behulp van een vertrouwd proces naar de offline machines.</span><span class="sxs-lookup"><span data-stu-id="d1b92-120">Copy these folders and file using a trusted process to the offline machines.</span></span> <span data-ttu-id="d1b92-121">Als u de provider op de offline computer wilt gebruiken, moet u deze importeren.</span><span class="sxs-lookup"><span data-stu-id="d1b92-121">To use the provider on the offline machine, it must be imported.</span></span> <span data-ttu-id="d1b92-122">Voer de volgende opdracht uit op de offline computer:</span><span class="sxs-lookup"><span data-stu-id="d1b92-122">Run the following command on the offline machine:</span></span>

```powershell
Import-PackageProvider -Name NuGet
```

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="d1b92-123">NuGet. exe hand matig Boots trappen voor het ondersteunen van publicatie bewerkingen op een computer die niet is verbonden met Internet</span><span class="sxs-lookup"><span data-stu-id="d1b92-123">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="d1b92-124">Naast het proces voor het hand matig Boots trapn van de NuGet-provider, is het bestand NuGet. exe binary vereist als de computer wordt gebruikt voor het publiceren van modules of scripts in een persoonlijke galerie met behulp van de `Publish-Module`-of `Publish-Script`-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d1b92-124">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="d1b92-125">De meest voorkomende use-case voor dit scenario is wanneer een persoonlijke galerie beschikbaar is voor de ondersteuning van een geïsoleerde omgeving.</span><span class="sxs-lookup"><span data-stu-id="d1b92-125">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="d1b92-126">Er zijn twee opties voor het verkrijgen van het bestand NuGet. exe.</span><span class="sxs-lookup"><span data-stu-id="d1b92-126">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="d1b92-127">Een optie is een Boots trap uitvoeren van een computer die is verbonden met internet en de bestanden kopiëren naar de offline machines met behulp van een vertrouwd proces.</span><span class="sxs-lookup"><span data-stu-id="d1b92-127">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="d1b92-128">Na Boots traping van de met internet verbonden computer, bevindt het binaire bestand NuGet. exe zich in een van de volgende mappen:</span><span class="sxs-lookup"><span data-stu-id="d1b92-128">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

 - <span data-ttu-id="d1b92-129">Als de `Publish-Module`-of `Publish-Script`-cmdlets zijn uitgevoerd met verhoogde machtigingen (als beheerder):</span><span class="sxs-lookup"><span data-stu-id="d1b92-129">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

   ```powershell
   $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
   ```

- <span data-ttu-id="d1b92-130">Als de cmdlets zijn uitgevoerd als een gebruiker zonder verhoogde machtigingen:</span><span class="sxs-lookup"><span data-stu-id="d1b92-130">If the cmdlets were executed as a user without elevated permissions:</span></span>

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```

<span data-ttu-id="d1b92-131">Een tweede mogelijkheid is om NuGet. exe te downloaden van de NuGet.Org-website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) wanneer u een Brok-versie selecteert voor productie machines, moet u ervoor zorgen dat deze later is dan 2.8.5.208 en de versie identificeren die wordt aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="d1b92-131">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="d1b92-132">Vergeet niet om het bestand te deblokkeren als dit is gedownload met behulp van een browser.</span><span class="sxs-lookup"><span data-stu-id="d1b92-132">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="d1b92-133">Dit kan worden uitgevoerd met behulp van de cmdlet `Unblock-File`.</span><span class="sxs-lookup"><span data-stu-id="d1b92-133">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="d1b92-134">In beide gevallen kan het bestand NuGet. exe worden gekopieerd naar een wille keurige locatie in `$env:path`, maar de standaard locaties zijn:</span><span class="sxs-lookup"><span data-stu-id="d1b92-134">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

- <span data-ttu-id="d1b92-135">Om het uitvoer bare bestand beschikbaar te maken zodat alle gebruikers `Publish-Module`-en `Publish-Script`-cmdlets kunnen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="d1b92-135">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

  ```powershell
  $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
  ```

- <span data-ttu-id="d1b92-136">Als u het uitvoer bare bestand alleen beschikbaar wilt maken voor een specifieke gebruiker, kopieert u op de locatie alleen binnen het profiel van de gebruiker:</span><span class="sxs-lookup"><span data-stu-id="d1b92-136">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```
