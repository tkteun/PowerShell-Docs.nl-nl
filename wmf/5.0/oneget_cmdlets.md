---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 134c22efe4fb86045ffb326e109dfbcc741bcf2f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="50475-102">PackageManagement-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="50475-102">PackageManagement Cmdlets</span></span>
<span data-ttu-id="50475-103">Dit is de kern van PackageManagement ter ondersteuning van software-detectie, installatie en -inventarisatie (SDII).</span><span class="sxs-lookup"><span data-stu-id="50475-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="50475-104">Probeer de cmdlets voor deze bewerkingen uit:</span><span class="sxs-lookup"><span data-stu-id="50475-104">Try out the cmdlets for these operations:</span></span>
-   <span data-ttu-id="50475-105">Find-Package</span><span class="sxs-lookup"><span data-stu-id="50475-105">Find-Package</span></span>
-   <span data-ttu-id="50475-106">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="50475-106">Find-PackageProvider</span></span>
-   <span data-ttu-id="50475-107">Get-Package</span><span class="sxs-lookup"><span data-stu-id="50475-107">Get-Package</span></span>
-   <span data-ttu-id="50475-108">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="50475-108">Get-PackageProvider</span></span>
-   <span data-ttu-id="50475-109">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="50475-109">Get-PackageSource</span></span>
-   <span data-ttu-id="50475-110">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="50475-110">Import-PackageProvider</span></span>
-   <span data-ttu-id="50475-111">Install-Package</span><span class="sxs-lookup"><span data-stu-id="50475-111">Install-Package</span></span>
-   <span data-ttu-id="50475-112">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="50475-112">Install-PackageProvider</span></span>
-   <span data-ttu-id="50475-113">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="50475-113">Register-PackageSource</span></span>
-   <span data-ttu-id="50475-114">Save-Package</span><span class="sxs-lookup"><span data-stu-id="50475-114">Save-Package</span></span>
-   <span data-ttu-id="50475-115">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="50475-115">Set-PackageSource</span></span>
-   <span data-ttu-id="50475-116">Verwijderen van pakket</span><span class="sxs-lookup"><span data-stu-id="50475-116">Uninstall-Package</span></span>
-   <span data-ttu-id="50475-117">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="50475-117">Unregister-PackageSource</span></span>

<span data-ttu-id="50475-118">Als PackageManagement een PowerShell-module is, kunt u het volgende als u wilt bijwerken PackageManagement zelf doen:</span><span class="sxs-lookup"><span data-stu-id="50475-118">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>
```powershell
PS C:\> Install-Module PackageManagement –Force
```
<span data-ttu-id="50475-119">In dit geval moet u PowerShell-sessie overschakelen naar de nieuwe versie van PackageManagement opnieuw invoeren.</span><span class="sxs-lookup"><span data-stu-id="50475-119">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdlethttpstechnetmicrosoftcomlibrarydn890709aspx"></a>[<span data-ttu-id="50475-120">Zoeken naar pakket Cmdlet</span><span class="sxs-lookup"><span data-stu-id="50475-120">Find-Package Cmdlet</span></span>](https://technet.microsoft.com/library/dn890709.aspx)
<span data-ttu-id="50475-121">Met deze cmdlet kan de detectie van softwarepakketten in beschikbaar pakket gegevensbronnen waarvoor gebruik wordt geladen pakket providers.</span><span class="sxs-lookup"><span data-stu-id="50475-121">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomlibrarymt676544aspx"></a>[<span data-ttu-id="50475-122">Zoeken naar PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="50475-122">Find-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/library/mt676544.aspx)
<span data-ttu-id="50475-123">De cmdlet zoeken PackageProvider zoeken naar overeenkomende PackageManagement providers die beschikbaar in het pakket gegevensbronnen die zijn geregistreerd met PowerShellGet zijn.</span><span class="sxs-lookup"><span data-stu-id="50475-123">The Find-PackageProvider cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="50475-124">Dit zijn pakket providers beschikbaar voor installatie met de cmdlet Install-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="50475-124">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span> <span data-ttu-id="50475-125">Standaard bevat deze modules beschikbaar in de PowerShell-galerie met de 'PackageManagement' en 'Provider' labels.</span><span class="sxs-lookup"><span data-stu-id="50475-125">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span> 

<span data-ttu-id="50475-126">Zoeken naar PackageProvider vindt ook overeenkomende PackageManagement providers die beschikbaar in de PackageManagement azure blob-opslag waar we de PackageManagement boostrapper provider gebruiken zijn voor het zoeken en installeren.</span><span class="sxs-lookup"><span data-stu-id="50475-126">Find-PackageProvider also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomlibrarydn890704aspx"></a>[<span data-ttu-id="50475-127">De Cmdlet Get-pakket</span><span class="sxs-lookup"><span data-stu-id="50475-127">Get-Package Cmdlet</span></span>](https://technet.microsoft.com/library/dn890704.aspx)
<span data-ttu-id="50475-128">Deze cmdlet retourneert een lijst van alle softwarepakketten die zijn geïnstalleerd met behulp van PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="50475-128">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[<span data-ttu-id="50475-129">Get-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="50475-129">Get-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890703.aspx)
<span data-ttu-id="50475-130">Pakket-providers die worden geladen en klaar voor gebruik op de lokale computer kunnen worden geïnventariseerd met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50475-130">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[<span data-ttu-id="50475-131">Get-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="50475-131">Get-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890705.aspx)
<span data-ttu-id="50475-132">Deze cmdlet wordt een lijst met pakket-bronnen die zijn geregistreerd voor een Pakketprovider.</span><span class="sxs-lookup"><span data-stu-id="50475-132">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[<span data-ttu-id="50475-133">De Cmdlet import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="50475-133">Import-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676545.aspx)
<span data-ttu-id="50475-134">Deze cmdlet wordt Package Management pakket providers toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="50475-134">This cmdlet adds Package Management package providers to the current session.</span></span>
```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[<span data-ttu-id="50475-135"> De Cmdlet Install-Package</span><span class="sxs-lookup"><span data-stu-id="50475-135"> Install-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890711.aspx)

<span data-ttu-id="50475-136">Met deze cmdlet kan de installatie van softwarepakketten in beschikbaar pakket gegevensbronnen waarvoor gebruik wordt geladen pakket providers.</span><span class="sxs-lookup"><span data-stu-id="50475-136">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[<span data-ttu-id="50475-137">De Cmdlet Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="50475-137">Install-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676543.aspx)
<span data-ttu-id="50475-138">Deze cmdlet wordt een of meer Management pakket met pakket-providers geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="50475-138">This cmdlet installs one or more Package Management package providers.</span></span>
```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[<span data-ttu-id="50475-139">De Cmdlet register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="50475-139">Register-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890701.aspx)
<span data-ttu-id="50475-140">Deze cmdlet wordt een pakketbron toegevoegd voor een opgegeven pakket-provider.</span><span class="sxs-lookup"><span data-stu-id="50475-140">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="50475-141">Elke provider PackageManagement misschien op een of meerdere software-bronnen of -opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="50475-141">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="50475-142">PackageManagement biedt PowerShell-cmdlets voor toevoegen/verwijderen/query de bron.</span><span class="sxs-lookup"><span data-stu-id="50475-142">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="50475-143">U kunt bijvoorbeeld een pakketbron registreren voor de NuGet-provider:</span><span class="sxs-lookup"><span data-stu-id="50475-143">For example, you can register a package source for the NuGet provider:</span></span>
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[<span data-ttu-id="50475-144">Cmdlet opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="50475-144">Save-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890708.aspx)
<span data-ttu-id="50475-145">Deze cmdlet slaat pakketten op de lokale computer zonder ze te installeren.</span><span class="sxs-lookup"><span data-stu-id="50475-145">This cmdlet saves packages to the local computer without installing them.</span></span>
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[<span data-ttu-id="50475-146">Set-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="50475-146">Set-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890710.aspx)
<span data-ttu-id="50475-147">Deze cmdlet wordt informatie over een bestaande pakketbron gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="50475-147">This cmdlet changes information about an existing package source.</span></span> 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[<span data-ttu-id="50475-148">De Cmdlet Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="50475-148">Uninstall-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890702.aspx)
<span data-ttu-id="50475-149">Deze cmdlet verwijdert pakketten die zijn geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="50475-149">This cmdlet uninstalls packages installed on the local computer.</span></span>
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[<span data-ttu-id="50475-150">Hef de registratie van PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="50475-150">Unregister-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

