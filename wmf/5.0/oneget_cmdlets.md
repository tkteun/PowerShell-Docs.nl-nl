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
# <a name="packagemanagement-cmdlets"></a>PackageManagement-Cmdlets
Dit is de kern van PackageManagement ter ondersteuning van software-detectie, installatie en -inventarisatie (SDII). Probeer de cmdlets voor deze bewerkingen uit:
-   Find-Package
-   Find-PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   Import-PackageProvider
-   Install-Package
-   Install-PackageProvider
-   Register-PackageSource
-   Save-Package
-   Set-PackageSource
-   Verwijderen van pakket
-   Unregister-PackageSource

Als PackageManagement een PowerShell-module is, kunt u het volgende als u wilt bijwerken PackageManagement zelf doen:
```powershell
PS C:\> Install-Module PackageManagement –Force
```
In dit geval moet u PowerShell-sessie overschakelen naar de nieuwe versie van PackageManagement opnieuw invoeren.

## <a name="find-package-cmdlethttpstechnetmicrosoftcomlibrarydn890709aspx"></a>[Zoeken naar pakket Cmdlet](https://technet.microsoft.com/library/dn890709.aspx)
Met deze cmdlet kan de detectie van softwarepakketten in beschikbaar pakket gegevensbronnen waarvoor gebruik wordt geladen pakket providers.
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

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomlibrarymt676544aspx"></a>[Zoeken naar PackageProvider Cmdlet](https://technet.microsoft.com/library/mt676544.aspx)
De cmdlet zoeken PackageProvider zoeken naar overeenkomende PackageManagement providers die beschikbaar in het pakket gegevensbronnen die zijn geregistreerd met PowerShellGet zijn. Dit zijn pakket providers beschikbaar voor installatie met de cmdlet Install-PackageProvider. Standaard bevat deze modules beschikbaar in de PowerShell-galerie met de 'PackageManagement' en 'Provider' labels. 

Zoeken naar PackageProvider vindt ook overeenkomende PackageManagement providers die beschikbaar in de PackageManagement azure blob-opslag waar we de PackageManagement boostrapper provider gebruiken zijn voor het zoeken en installeren.
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomlibrarydn890704aspx"></a>[De Cmdlet Get-pakket](https://technet.microsoft.com/library/dn890704.aspx)
Deze cmdlet retourneert een lijst van alle softwarepakketten die zijn geïnstalleerd met behulp van PackageManagement.
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[Get-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/dn890703.aspx)
Pakket-providers die worden geladen en klaar voor gebruik op de lokale computer kunnen worden geïnventariseerd met de cmdlet.
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[Get-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890705.aspx)
Deze cmdlet wordt een lijst met pakket-bronnen die zijn geregistreerd voor een Pakketprovider.
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[De Cmdlet import-PackageProvider](https://technet.microsoft.com/en-us/library/mt676545.aspx)
Deze cmdlet wordt Package Management pakket providers toegevoegd aan de huidige sessie.
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

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[ De Cmdlet Install-Package](https://technet.microsoft.com/en-us/library/dn890711.aspx)

Met deze cmdlet kan de installatie van softwarepakketten in beschikbaar pakket gegevensbronnen waarvoor gebruik wordt geladen pakket providers.
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[De Cmdlet Install-PackageProvider](https://technet.microsoft.com/en-us/library/mt676543.aspx)
Deze cmdlet wordt een of meer Management pakket met pakket-providers geïnstalleerd.
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

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[De Cmdlet register-PackageSource](https://technet.microsoft.com/en-us/library/dn890701.aspx)
Deze cmdlet wordt een pakketbron toegevoegd voor een opgegeven pakket-provider.
Elke provider PackageManagement misschien op een of meerdere software-bronnen of -opslagplaatsen. PackageManagement biedt PowerShell-cmdlets voor toevoegen/verwijderen/query de bron. U kunt bijvoorbeeld een pakketbron registreren voor de NuGet-provider:
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[Cmdlet opslaan-pakket](https://technet.microsoft.com/en-us/library/dn890708.aspx)
Deze cmdlet slaat pakketten op de lokale computer zonder ze te installeren.
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[Set-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890710.aspx)
Deze cmdlet wordt informatie over een bestaande pakketbron gewijzigd. 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[De Cmdlet Uninstall-pakket](https://technet.microsoft.com/en-us/library/dn890702.aspx)
Deze cmdlet verwijdert pakketten die zijn geïnstalleerd op de lokale computer.
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[Hef de registratie van PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

