---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2f05fe96ec792a31fabf3aff0f9e18b40178316c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685310"
---
# <a name="packagemanagement-cmdlets"></a>PackageManagement-cmdlets

Dit is de kern van PackageManagement ter ondersteuning van, installatie, en software-inventaris (SDII). Probeer de cmdlets voor deze bewerkingen:

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

PackageManagement is een PowerShell-module, kunt u het volgende voor het bijwerken van PackageManagement zelf doen:

```powershell
Install-Module PackageManagement –Force
```

In dit geval moet u PowerShell-sessie opnieuw invoeren om over te schakelen naar de nieuwe versie van PackageManagement.

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[Zoeken-Package-Cmdlet](/powershell/module/PackageManagement/Find-Package)

Met deze cmdlet kunt de detectie van software-updatepakketten in pakket beschikbaar bronnen met behulp van pakket providers geladen.

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[Zoeken-PackageProvider Cmdlet](/powershell/module/PackageManagement/Find-PackageProvider)

De `Find-PackageProvider` cmdlet gevonden die overeenkomen met PackageManagement-providers die beschikbaar in pakketbronnen zijn geregistreerd met PowerShellGet. Dit pakket providers beschikbaar voor installatie zijn de `Install-PackageProvider` cmdlet. Standaard bevat deze modules beschikbaar in de PowerShell-galerie met de 'PackageManagement' en 'Provider' Tags.

`Find-PackageProvider` ook zoeken naar overeenkomende PackageManagement-providers die beschikbaar in de azure blob-archief van het PackageManagement waar we de provider van PackageManagement boostrapper gebruiken zijn voor het zoeken en ze te installeren.

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[De Cmdlet Get-pakket](/powershell/module/PackageManagement/Get-Package)

Deze cmdlet retourneert een lijst van alle softwarepakketten die zijn geïnstalleerd met behulp van PackageManagement.

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[Get-PackageProvider Cmdlet](/powershell/module/PackageManagement/Get-PackageProvider)

Pakket-providers die worden geladen en gereed voor gebruik op de lokale computer kunnen worden geïnventariseerd door met de cmdlet.

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[Get-PackageSource Cmdlet](/powershell/module/PackageManagement/Get-PackageSource)

Deze cmdlet wordt een lijst met pakketbronnen die zijn geregistreerd voor een Pakketprovider.

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[De Cmdlet import-PackageProvider](/powershell/module/PackageManagement/Import-PackageProvider)

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

## <a name="-install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[ De Cmdlet Install-Package](/powershell/module/PackageManagement/Install-Package)

Met deze cmdlet kan de installatie van software-updatepakketten in pakket beschikbaar bronnen met behulp van pakket providers geladen.

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[De Cmdlet Install-PackageProvider](/powershell/module/PackageManagement/Install-PackageProvider)

Deze cmdlet installeert een of meer Package Management pakket providers.

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

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[De Cmdlet register-PackageSource](/powershell/module/PackageManagement/Register-PackageSource)

Deze cmdlet wordt een pakketbron toegevoegd voor een opgegeven pakket-provider.
Elke provider van PackageManagement mogelijk op een of meerdere bronnen van de software of -opslagplaatsen. PackageManagement biedt PowerShell-cmdlets voor het toevoegen/verwijderen/query de bron. U kunt bijvoorbeeld een pakketbron registreren voor de NuGet-provider:

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[Cmdlet opslaan-pakket](/powershell/module/PackageManagement/Save-Package)

Deze cmdlet slaat pakketten naar de lokale computer zonder deze te installeren.

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[Set-PackageSource Cmdlet](/powershell/module/PackageManagement/Set-PackageSource)

Deze cmdlet wijzigt informatie over een bestaande pakketbron.

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[De Cmdlet Uninstall-pakket](/powershell/module/PackageManagement/Uninstall-Package)

Deze cmdlet verwijdert pakketten die op de lokale computer zijn geïnstalleerd.

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[De registratie ongedaan maken PackageSource Cmdlet](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```