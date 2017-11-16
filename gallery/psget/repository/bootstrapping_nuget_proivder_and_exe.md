---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Uitvoeren van de bootstrap NuGet-Provider en EXE
ms.openlocfilehash: 0036972eb9a0c20469da1aadafe223e6ec80f16a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="bootstrap-both-nuget-provider-and-nugetexe-or-bootstrap-only-nuget-provider"></a>Bootstrap-NuGet provider zowel NuGet.exe of bootstrap NuGet-provider

NuGet.exe is niet opgenomen in de meest recente NuGet-provider.
Publiceren voor bewerkingen van een module of een script, PowerShellGet de binaire uitvoerbare NuGet.exe vereist.
Alleen de NuGet-provider vereist voor alle andere bewerkingen is, inclusief *vinden*, *installeren*, *opslaan*, en *verwijderen*.
PowerShellGet bevat de logica voor het afhandelen van hetzij een gecombineerde bootstrap van de NuGet-provider en NuGet.exe of bootstrap van alleen de NuGet-provider.
In beide gevallen wordt moet alleen een enkel bericht plaatsvinden.
Als de machine niet is verbonden met Internet, moet de gebruiker of beheerder een vertrouwde instantie van de NuGet-provider en/of het bestand NuGet.exe kopiëren naar de niet-verbonden computer.

>**Opmerking**: vanaf versie 6, de NuGet-provider is opgenomen in de installatie van PowerShell. [http://github.com/PowerShell/PowerShell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Fout bij het oplossen van wanneer de NuGet-provider is niet geïnstalleerd op een computer waarop Internet is aangesloten

```powershell
PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

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
## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Fout bij het oplossen van wanneer de provider NuGet beschikbaar is en NuGet.exe is niet beschikbaar tijdens het publiceren op een computer waarop Internet is aangesloten

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Fout bij het oplossen van wanneer zowel NuGet-provider en NuGet.exe zijn niet beschikbaar tijdens het publiceren op een computer waarop Internet is aangesloten

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>De NuGet-provider op een computer die niet is verbonden met Internet handmatig uitvoeren van de bootstrap

De processen aangetoond dat hierboven wordt ervan uitgegaan dat de computer is verbonden met Internet en bestanden kan downloaden vanaf een openbaar toegankelijke locatie.
Als dat niet mogelijk is, is de enige optie bootstrap van een machine met behulp van de bovenstaande processen en de provider handmatig kopiëren naar het geïsoleerde knooppunt via een vertrouwde offlineproces.
De meest voorkomende gebruiksvoorbeeld voor dit scenario is wanneer een persoonlijke galerie beschikbaar ter ondersteuning van een geïsoleerde omgeving.

Nadat u het proces hierboven voor een Internet verbonden machine bootstrap, vindt u provider-bestanden in de locatie:
```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

De map/bestand structuur van de NuGet-provider zijn (mogelijk met een andere versienummer):

NuGet<br>
--2.8.5.208<br>
---Microsoft.PackageManagement.NuGetProvider.dll

Kopieer deze mappen en het bestand met een vertrouwd proces op de virtuele machines offline.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Bewerkingen op een machine die niet is verbonden met Internet NuGet.exe ter ondersteuning van handmatig uitvoeren van de bootstrap publiceren

Naast het proces van de provider NuGet handmatig bootstrap als de computer wordt gebruikt voor het publiceren van modules of scripts in een persoonlijke galerie met de *publiceren-Module* of *publiceren Script* -cmdlets het NuGet.exe binaire uitvoerbare bestand is vereist.
De meest voorkomende gebruiksvoorbeeld voor dit scenario is wanneer een persoonlijke galerie beschikbaar ter ondersteuning van een geïsoleerde omgeving.
Er zijn twee opties om op te halen van het bestand NuGet.exe.

Een mogelijkheid is het bootstrap van een machine die is verbonden met Internet en kopieer de bestanden naar de offline-machines met een vertrouwd proces.
Na het uitvoeren van de bootstrap de Internet verbonden machine, zich het binaire NuGet.exe bevindt in een van twee mappen:

Als de *publiceren-Module* of *publiceren Script* cmdlets zijn uitgevoerd met verhoogde machtigingen (als een Administrator):
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Als de cmdlets zijn uitgevoerd als een gebruiker zonder verhoogde machtigingen:
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Een tweede mogelijkheid is NuGet.exe downloaden van de website NuGet.Org: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)<br>
Als u een Nuget-versie voor productiemachines, zorg ervoor dat deze later is dan 2.8.5.208 en identificeren van de versie die zijn gelabeld 'aanbevolen'.
Vergeet niet om de blokkering van het bestand als het is gedownload via een browser te.
Dit kan worden uitgevoerd met behulp van de *blokkering bestand* cmdlet.

In beide gevallen wordt het bestand NuGet.exe kan worden gekopieerd naar een locatie in *$env: pad*, maar de standaardlocaties zijn:

Het uitvoerbare bestand om beschikbaar te maken zodat alle gebruikers kunnen gebruiken *publiceren-Module* en *publiceren Script* cmdlets:
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Als u het uitvoerbare bestand voor een specifieke gebruiker, kopiëren naar de locatie binnen alleen die gebruiker profiel:
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

