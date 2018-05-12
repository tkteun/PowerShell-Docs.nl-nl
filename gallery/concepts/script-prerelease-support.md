---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Voorlopige versies van scripts
ms.openlocfilehash: 2c7e1cbc352f8dc39fef9cd968b2f0c1964c30b3
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-versions-of-scripts"></a>Voorlopige versies van scripts

Vanaf versie 1.6.0 bieden PowerShellGet en de PowerShell-galerie ondersteuning voor versies die groter zijn dan 1.0.0 als een prerelease-tagging. Voorafgaand aan deze functie zijn prerelease-items beperkt tot een versie die begint met 0 hebben. Het doel van deze functies is het bieden meer ondersteuning voor [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning aanroepconventie zonder te verbreken achterwaartse compatibiliteit met PowerShell versies 3 en hoger of bestaande versies van PowerShellGet. Dit onderwerp richt zich op de script-specifieke functies. De equivalente functies voor modules die zich in de [Prerelease moduleversies](module-prerelease-support.md) onderwerp. Deze functies gebruikt, kunnen uitgevers identificeren van een script als versie 2.5.0-alpha en later een versie gereed is voor productie 2.5.0 die de prerelease versie vervangt.

Op een hoog niveau: de functies van voorlopige script

- Een PrereleaseString achtervoegsel wordt toegevoegd aan de versiereeks in het manifest script. Wanneer de scripts wordt gepubliceerd naar de PowerShell-galerie, is deze gegevens opgehaald uit het manifest en gebruikt om deze items te identificeren.
- Ophalen van een prerelease-items vereist - AllowPrerelease vlag toe te voegen aan de PowerShellGet opdrachten Find-Script installatiescript-Script voor het bijwerken en opslaan-Script. Als de vlag niet is opgegeven, wordt deze items niet worden weergegeven.
- Script-versies weergegeven door Find-Script Get-InstalledScript en in de PowerShell-galerie weergegeven met de PrereleaseString, zoals in 2.5.0-alpha.

Hieronder vindt u details voor de functies.

## <a name="identifying-a-script-version-as-a-prerelease"></a>De versie van een script te identificeren als een voorlopige versie

Ondersteuning voor voorlopige versies PowerShellGet nog gemakkelijker voor scripts modules. Script versiebeheer wordt alleen ondersteund door PowerShellGet, dus er geen compatibiliteitsproblemen veroorzaakt zijn door de prerelease-tekenreeks toe te voegen. Als u wilt een script in de PowerShell-galerie als een voorlopige versie hebt geïdentificeerd, moet u een prerelease achtervoegsel toevoegen aan een correct opgemaakt versietekenreeks in de script-metagegevens.

Een voorbeeld van een script manifest met een prerelease-versie in deze sectie eruit als het volgende:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

De tekenreeks moet voldoen aan de volgende vereisten voor het gebruik van een prerelease-achtervoegsel:

- Het achtervoegsel van een prerelease kan alleen worden opgegeven als de versie 3 segmenten voor Major.Minor.Build.
  Dit wordt uitgelijnd met SemVer v1.0.0
- Het achtervoegsel voor de prerelease is een tekenreeks zijn die begint met een afbreekstreepje en mag bestaan uit ASCII-letters en cijfers [0-9A-Za - z-]
- Alleen SemVer v1.0.0 prerelease tekenreeksen worden ondersteund op dit moment is het achtervoegsel voor de prerelease __moet niet__ beide punt bevatten of + [. +], die zijn toegestaan in SemVer 2.0
- Voorbeelden van ondersteunde PrereleaseString tekenreeksen zijn:-alpha, -a1,-bèta, -update20171020

__Voorlopige versies gevolgen voor de mappen en de installatie sorteren__

Sorteervolgorde verandert wanneer u een prerelease-versie, wat belangrijk bij het publiceren van de PowerShell-galerie, en scripts met PowerShellGet opdrachten installeren. Als twee versies met het versienummer scripts bestaat, de sorteervolgorde is gebaseerd op het volgende op het afbreekstreepje tekenreeksdeel. Dus is versie 2.5.0-alpha kleiner dan 2.5.0-beta, dat is minder dan 2.5.0-gamma. Als twee scripts hetzelfde versienummer hebben en slechts één een PrereleaseString, het script heeft __zonder__ de prerelease achtervoegsel wordt ervan uitgegaan dat de versie gereed is voor productie en worden gesorteerd als een hogere versie dan de voorlopige versie Versie. Als u bijvoorbeeld bij het vergelijken van releases 2.5.0 en 2.5.0-beta, de 2.5.0 versie wordt beschouwd als de grootste van de twee.

Bij het publiceren van de PowerShell-galerie, moet de versie van het script wordt gepubliceerd hebben standaard een hogere versie dan eventuele eerder gepubliceerde versie die in de PowerShell-galerie. Een uitgever kan versie 2.5.0-alpha bijwerken 2.5.0-beta of met 2.5.0 (met geen prerelease achtervoegsel).

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Zoeken en ophalen van een prerelease-items met PowerShellGet opdrachten

Omgaan met prerelease items met PowerShellGet Find-Script, Script voor installatie, Update-Script, en opslaan scriptopdrachten vereist de vlag - AllowPrerelease toe te voegen. Als - AllowPrerelease is opgegeven, wordt deze prerelease-items worden opgenomen als deze aanwezig zijn. Als de vlag - AllowPrerelease niet is opgegeven, wordt deze items niet weergegeven.

De enige uitzonderingen op dit in de scriptopdrachten PowerShellGet zijn Get-InstalledScript en in sommige gevallen met Uninstall-Script.

- Get-InstalledScript weergegeven altijd automatisch de prerelease-informatie in de versietekenreeks indien aanwezig.
- Uninstall-Script wordt standaard verwijderd de meest recente versie van een script als __geen versie__ is opgegeven. Dit gedrag is niet gewijzigd. Echter, als een prerelease-versie wordt opgegeven met - RequiredVersion, - AllowPrerelease is vereist.

## <a name="examples"></a>Voorbeelden

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

Uninstall-Script wordt de huidige versie van een script verwijderen wanneer - RequiredVersion is niet opgegeven.
-RequiredVersion is opgegeven, en een voorlopige versie, moet - AllowPrerelease worden toegevoegd aan de opdracht.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a>meer informatie

- [Prerelease-moduleversies](module-prerelease-support.md)
- [Zoeken naar script](/powershell/module/powershellget/find-script)
- [Script voor installatie](/powershell/module/powershellget/install-script)
- [Opslaan-script](/powershell/module/powershellget/save-script)
- [Script voor het bijwerken](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)