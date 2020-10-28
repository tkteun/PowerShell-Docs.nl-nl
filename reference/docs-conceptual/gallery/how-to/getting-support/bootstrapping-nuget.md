---
ms.date: 06/12/2017
title: Boots trap-NuGet
description: In dit artikel wordt uitgelegd hoe u de NuGet-onderdelen installeert die nodig zijn voor de ondersteuning van het werken met de PowerShell Gallery.
ms.openlocfilehash: eddbe15e7a765ad8b6df2b317a090269f06661d5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661118"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Boots trap de NuGet-provider en NuGet.exe

NuGet.exe is niet opgenomen in de meest recente NuGet-provider. Voor publicatie bewerkingen van een module of script is voor PowerShellGet de binaire uitvoer bare **NuGet.exe** vereist. Alleen de NuGet-provider is vereist voor alle andere bewerkingen, zoals **zoeken** , **installeren** , **Opslaan** en **verwijderen** .
PowerShellGet bevat logica voor het verwerken van een gecombineerde Boots trap van de NuGet-provider en NuGet.exe, of Boots trap van alleen de NuGet-provider. In beide gevallen moet er slechts één prompt bericht worden weer gegeven. Als de computer niet is verbonden met internet, moet de gebruiker of een beheerder een vertrouwd exemplaar van de NuGet-provider en/of het NuGet.exe bestand naar de niet-verbonden computer kopiëren.

> [!NOTE]
> Vanaf versie 6 wordt de NuGet-provider opgenomen in de installatie van Power shell.

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Fout oplossen wanneer de NuGet-provider niet is geïnstalleerd op een computer die is verbonden met Internet

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet
provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you
want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure
that '2.8.5.201' or newer version of NuGet provider is installed.
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
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet
provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you
want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Fout bij het oplossen van het probleem wanneer de NuGet-provider beschikbaar is en NuGet.exe niet beschikbaar is tijdens de publicatie bewerking op een computer die is verbonden met Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must
be available under one of the paths specified in PATH environment variable value. Do you want
PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure
that NuGet.exe is available under one of the paths specified in PATH environment variable value.
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
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must
be available under one of the paths specified in PATH environment variable value. Do you want
PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'.
Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Fout bij het oplossen van problemen wanneer zowel de NuGet-provider als de NuGet.exe niet beschikbaar zijn tijdens de publicatie bewerking op een computer die is verbonden met Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with
the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer
to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of
NuGet provider is installed and NuGet.exe is available under one of the paths specified in PATH
environment variable value.
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
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with
the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'.
 Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>De NuGet-provider hand matig Boots trappen op een computer die niet is verbonden met Internet

In de processen die hierboven worden beschreven, wordt ervan uitgegaan dat de machine is verbonden met internet en dat er bestanden kunnen worden gedownload vanaf een open bare locatie. Als dat niet mogelijk is, kunt u het beste een Boots trap uitvoeren op een machine met behulp van de hierboven genoemde processen en de provider hand matig kopiëren naar het geïsoleerde knoop punt via een offline vertrouwd proces. De meest voorkomende use-case voor dit scenario is wanneer een persoonlijke galerie beschikbaar is voor de ondersteuning van een geïsoleerde omgeving.

Nadat u het bovenstaande proces hebt uitgevoerd om een computer met een Internet verbinding te Boots trappen, vindt u de bestanden van de provider op de volgende locatie:

`C:\Program Files\PackageManagement\ProviderAssemblies\`

De structuur van de map of het bestand van de NuGet-provider is (mogelijk met een ander versie nummer):

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Kopieer deze mappen en dit bestand met behulp van een vertrouwd proces naar de offline machines. Als u de provider op de offline computer wilt gebruiken, moet u deze importeren. Voer de volgende opdracht uit op de offline computer:

```powershell
Import-PackageProvider -Name NuGet
```

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Hand matig Boots trappen NuGet.exe voor het ondersteunen van publicatie bewerkingen op een computer die niet is verbonden met Internet

Naast het proces om de NuGet-provider hand matig te Boots trapn, als de computer wordt gebruikt voor het publiceren van modules of scripts in een persoonlijke galerie met behulp van de `Publish-Module` `Publish-Script` cmdlets of, is het NuGet.exe binaire uitvoer bare bestand vereist.

De meest voorkomende use-case voor dit scenario is wanneer een persoonlijke galerie beschikbaar is voor de ondersteuning van een geïsoleerde omgeving. Er zijn twee opties om het NuGet.exe-bestand te verkrijgen.

Een optie is een Boots trap uitvoeren van een computer die is verbonden met internet en de bestanden kopiëren naar de offline machines met behulp van een vertrouwd proces. Na het Boots trapen van de met internet verbonden computer, bevindt het NuGet.exe binaire bestand zich in een van de twee mappen:

- Als de `Publish-Module` `Publish-Script` cmdlets of zijn uitgevoerd met verhoogde machtigingen (als beheerder):

   ```powershell
   $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
   ```

- Als de cmdlets zijn uitgevoerd als een gebruiker zonder verhoogde machtigingen:

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```

Een tweede optie is om NuGet.exe te downloaden van de NuGet.Org-website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) Wanneer u een Brok-versie voor productie machines selecteert, moet u ervoor zorgen dat deze later is dan 2.8.5.208 en de versie identificeren die wordt aanbevolen. Vergeet niet om het bestand te deblokkeren als dit is gedownload met behulp van een browser. Dit kan worden uitgevoerd met behulp van de- `Unblock-File` cmdlet.

In beide gevallen kan het NuGet.exe bestand naar een wille keurige locatie in worden gekopieerd `$env:path` , maar de standaard locaties zijn:

- Om het uitvoer bare bestand beschikbaar te maken zodat alle gebruikers `Publish-Module` `Publish-Script` cmdlets kunnen gebruiken:

  ```powershell
  $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
  ```

- Als u het uitvoer bare bestand alleen beschikbaar wilt maken voor een specifieke gebruiker, kopieert u op de locatie alleen binnen het profiel van de gebruiker:

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```
