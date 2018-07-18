---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Uitvoeren van de bootstrap NuGet
ms.openlocfilehash: 2d321097fda201c0d8f843b2194a161eceabe4e1
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094014"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Het NuGet-provider en NuGet.exe opstarten

NuGet.exe is niet opgenomen in de meest recente NuGet-provider.
Publiceren voor bewerkingen van een module of een script, PowerShellGet de binaire uitvoerbare NuGet.exe vereist.
Alleen de NuGet-provider vereist voor alle andere bewerkingen is, inclusief *vinden*, *installeren*, *opslaan*, en *verwijderen*.
PowerShellGet, bevat de logica voor het afhandelen van ofwel een gecombineerde bootstrap van het NuGet-provider en NuGet.exe of bootstrap van alleen de NuGet-provider.
In beide gevallen moet alleen een enkel bericht moet worden uitgevoerd.
Als de machine niet is verbonden met Internet, moet de gebruiker of beheerder een vertrouwde instantie van de NuGet-provider en/of het bestand NuGet.exe kopiëren naar de niet-verbonden machine.

> [!NOTE]
> Vanaf versie 6, is het NuGet-provider opgenomen in de installatie van PowerShell. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Het oplossen van de fout als de NuGet-provider is niet geïnstalleerd op een computer die Internet is verbonden

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
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
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Fout bij het oplossen van wanneer vindt u het NuGet-provider en NuGet.exe is niet beschikbaar tijdens het publiceren op een computer die is Internet verbonden

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
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

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Het oplossen van fout wanneer zowel NuGet-provider en NuGet.exe zijn niet beschikbaar tijdens het publiceren op een computer die Internet is verbonden

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
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

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Handmatig opstarten de NuGet-provider op een computer die niet is verbonden met Internet

De processen aangetoond dat hierboven wordt ervan uitgegaan dat de machine is verbonden met Internet en bestanden kan downloaden vanaf een openbare locatie.
Als dat niet mogelijk is, is de enige optie bootstrap-een virtuele machine met de bovenstaande processen en de provider handmatig kopiëren naar het geïsoleerde knooppunt via een offlineproces vertrouwd.
De meest voorkomende use-case voor dit scenario is wanneer een privégalerie beschikbaar voor ondersteuning van een geïsoleerde omgeving.

Nadat u het proces dat hierboven is een Internet verbonden virtuele machine opstarten, vindt u bestanden van de provider op de locatie:

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

De structuur van de map/bestand van het NuGet-provider zijn (eventueel met een andere versie getal):

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Kopieer deze mappen en het bestand met behulp van een vertrouwd proces op de offline virtuele machines.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Handmatig opstarten NuGet.exe ter ondersteuning van bewerkingen op een computer die niet is verbonden met Internet publiceren

Naast het proces handmatig opstarten van het NuGet-provider als de machine wordt gebruikt om modules of scripts publiceren naar een privégalerie met de `Publish-Module` of `Publish-Script` cmdlets, het NuGet.exe binaire uitvoerbare bestand is vereist.

De meest voorkomende use-case voor dit scenario is wanneer een privégalerie beschikbaar voor ondersteuning van een geïsoleerde omgeving.
Er zijn twee opties voor het bestand NuGet.exe verkrijgen.

Een optie is het bootstrap-een virtuele machine die is verbonden met Internet en kopieer de bestanden naar de offline-machines met behulp van een vertrouwd proces.
Na het opstarten van het Internet verbonden machine, worden de binaire NuGet.exe worden geplaatst in een van twee mappen:

Als de `Publish-Module` of `Publish-Script` cmdlets zijn uitgevoerd met verhoogde bevoegdheden (als beheerder):

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Als de cmdlets zijn uitgevoerd als een gebruiker zonder verhoogde bevoegdheden:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Een tweede optie is om NuGet.exe downloaden van de website NuGet.Org: [ https://dist.nuget.org/index.html ](https://www.nuget.org/downloads) bij het selecteren van een Nuget-versie voor productiemachines, zorgt ervoor dat deze later zijn dan 2.8.5.208 en identificeren van de versie die is is met het label " aanbevolen'.
Vergeet niet om de blokkering van het bestand als deze is gedownload met behulp van een browser.
Dit kan worden uitgevoerd met behulp van de `Unblock-File` cmdlet.

In beide gevallen moet het bestand NuGet.exe kan worden gekopieerd naar een locatie in `$env:path`, maar de standaard locaties zijn:

Het uitvoerbare bestand om beschikbaar te maken zodat alle gebruikers kunnen gebruiken `Publish-Module` en `Publish-Script` cmdlets:

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Als u het uitvoerbare bestand op een specifieke gebruiker, kopiëren naar de locatie binnen van die gebruiker-profiel:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```