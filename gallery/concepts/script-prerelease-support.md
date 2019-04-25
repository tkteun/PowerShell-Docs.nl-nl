---
ms.date: 10/17/2017
contributor: keithb
keywords: Galerie, powershell, cmdlet, psget
title: Voorlopige versies van scripts
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084637"
---
# <a name="prerelease-versions-of-scripts"></a>Voorlopige versies van scripts

Vanaf versie 1.6.0, bieden powershellget hebt en de PowerShell Gallery ondersteuning voor het labelen van versies die groter zijn dan 1.0.0 als een voorlopige versie. Voorlopige pakketten zijn voordat u deze functie beperkt tot het met een versie die begint met 0. Het doel van deze functies is te bieden meer ondersteuning voor [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versiebeheer Verdrag zonder dat belangrijke achterwaartse compatibiliteit met PowerShell 3 en hoger of bestaande versie van PowerShellGet. In dit onderwerp richt zich op de script-specifieke functies. De equivalente functies voor modules die zich in de [voorlopige versie moduleversies](module-prerelease-support.md) onderwerp. Met behulp van deze functies, kunnen uitgevers een script op als versie 2.5.0-alpha identificeren en later een versie gereed is voor productie 2.5.0 die de prerelease versie vervangt.

Op hoog niveau, de prerelease-script-functies zijn onder andere:

- Een PrereleaseString achtervoegsel toevoegen aan de tekenreeks in het manifest van het script. Wanneer de scripts is gepubliceerd naar de PowerShell Gallery, is deze gegevens opgehaald uit het manifest en gebruikt voor het identificeren van prerelease-pakketten.
- Verkrijgen van prerelease pakketten vereist - AllowPrerelease vlag toe te voegen aan de PowerShellGet-opdrachten Find-Script Install-Script, Update-Script en Save-Script. Als de vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.
- Script-versies weergegeven door Find-Script Get-InstalledScript, en in de PowerShell Gallery weergegeven met de PrereleaseString, zoals in 2.5.0-alpha.

Details voor de functies zijn hieronder vermeld.

## <a name="identifying-a-script-version-as-a-prerelease"></a>De versie van een script te identificeren als een voorlopige versie

PowerShellGet-ondersteuning voor voorlopige versies is geweest voor scripts modules. Script versiebeheer wordt alleen ondersteund door PowerShellGet, dus er geen compatibiliteitsproblemen veroorzaakt zijn door het toevoegen van de voorlopige tekenreeks. Voor het identificeren van een script in de PowerShell Gallery als een voorlopige versie, moet u een prerelease achtervoegsel toegevoegd aan een goed ingedeelde versietekenreeks in de scriptmetagegevens.

Een voorbeeld van een manifest script met een prerelease-versie in deze sectie eruit als volgt uit:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

De tekenreeks moet voldoen aan de volgende vereisten voor het gebruik van een prerelease-achtervoegsel:

- Een prerelease-achtervoegsel kan alleen worden opgegeven als de versie 3 segmenten voor Major.Minor.Build.
  Deze correspondeert met SemVer versie 1.0.0 gebruikt
- De prerelease-achtervoegsel is een tekenreeks die begint met een afbreekstreepje en mag de ASCII-letters [0-9 bis-Za - z-]
- Alleen SemVer v1.0.0 prerelease tekenreeksen worden ondersteund op dit moment is het achtervoegsel van de voorlopige **moet niet** beide punt bevatten of + [. +], die zijn toegestaan in SemVer 2.0
- Voorbeelden van ondersteunde PrereleaseString tekenreeksen zijn:-alpha, a1,-bèta, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Voorlopige versies gevolgen voor sorteren en de installatie-mappen

Sorteervolgorde wordt gewijzigd wanneer u een prerelease-versie, dit belangrijk is bij het publiceren naar de PowerShell Gallery, en bij het installeren van scripts met PowerShellGet-opdrachten. Als twee versies met het versienummer scripts bestaat, de sorteervolgorde is op basis van de tekenreeks deel afbreekstreepjes te volgen. Dus, versie 2.5.0-alpha is kleiner dan 2.5.0-beta, die kleiner is dan 2.5.0-gamma. Als twee scripts de dezelfde versienummer hebben en slechts één een PrereleaseString, het script heeft **zonder** de prerelease-achtervoegsel wordt ervan uitgegaan dat de versie gereed is voor productie en als een hogere versie dan de voorlopige versie worden gesorteerd Versie. Een voorbeeld: bij het vergelijken van releases 2.5.0 en 2.5.0-beta, de 2.5.0 versie wordt beschouwd als de hoogste waarde van de twee.

Bij het publiceren naar de PowerShell Gallery, moet de versie van het script wordt gepubliceerd hebben standaard een hogere versie dan alle eerder gepubliceerde versie die in de PowerShell Gallery. Een uitgever kan versie 2.5.0-alpha bijwerken met 2.5.0-beta of 2.5.0 (met geen voorvoegsel prerelease).

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Zoeken en ophalen van prerelease pakketten met PowerShellGet-opdrachten

Omgaan met prerelease pakketten met PowerShellGet Find-Script, installatiescript, Update-Script, en Save-Script-opdrachten moet de vlag - AllowPrerelease toe te voegen. Als - AllowPrerelease is opgegeven, wordt deze prerelease-pakketten worden opgenomen als deze aanwezig zijn. Als AllowPrerelease - vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.

De enige uitzonderingen op deze in de PowerShellGet-script-opdrachten zijn Get-InstalledScript en soms met Uninstall-Script.

- Get-InstalledScript weergegeven altijd automatisch de prerelease-informatie in de tekenreeks als deze aanwezig is.
- Uninstall-Script wordt standaard verwijderen van de meest recente versie van een script als **geen versie** is opgegeven. Dit gedrag is niet gewijzigd. Echter, als een prerelease-versie is opgegeven met behulp van `-RequiredVersion`, `-AllowPrerelease` is vereist.

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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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
Als - RequiredVersion is opgegeven, en een voorlopige versie is, moet - AllowPrerelease worden toegevoegd aan de opdracht.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-script


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

## <a name="more-details"></a>Meer informatie

- [Voor voorlopige moduleversies](module-prerelease-support.md)
- [Find-script](/powershell/module/powershellget/find-script)
- [Script voor installatie](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Update-script](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)
