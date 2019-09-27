---
ms.date: 10/17/2017
contributor: keithb
keywords: Galerie, Power shell, cmdlet, psget
title: Voorlopige versies van scripts
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329174"
---
# <a name="prerelease-versions-of-scripts"></a>Voorlopige versies van scripts

Vanaf versie 1.6.0, PowerShellGet en de PowerShell Gallery bieden ondersteuning voor coderings versies die groter zijn dan 1.0.0 als een voorlopige versie. Vóór deze functie werden voorlopige pakketten beperkt tot een versie die begint met 0. Het doel van deze functies is om meer ondersteuning te bieden voor [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) versie beheer, zonder achterwaartse compatibiliteit te verbreken met Power shell-versies 3 en hoger, of bestaande versies van PowerShellGet. Dit onderwerp richt zich op de script-specifieke functies. De equivalente functies voor modules vindt u in het onderwerp versies van de [module Prerelease](module-prerelease-support.md) . Met behulp van deze functies kunnen uitgevers een script identificeren als versie 2.5.0-alpha en later een productie versie-2.5.0 vrijgeven die de voorlopige versie vervangt.

Op hoog niveau zijn de functies van het voorlopige script:

- Een PrereleaseString-achtervoegsel toevoegen aan de versie teken reeks in het script manifest. Wanneer de scripts worden gepubliceerd op de PowerShell Gallery, worden deze gegevens geëxtraheerd uit het manifest en gebruikt om voorlopige pakketten te identificeren.
- Voor het verkrijgen van voorlopige pakketten moet u de vlag AllowPrerelease toevoegen aan de PowerShellGet-opdrachten Zoek-script, install-script, update script en Save-script. Als de vlag niet is opgegeven, worden er geen voorlopige pakketten weer gegeven.
- Script versies die worden weer gegeven door Find-script, Get-InstalledScript en in de PowerShell Gallery worden weer gegeven met de PrereleaseString, zoals in 2.5.0-alpha.

Hieronder vindt u meer informatie over de functies.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Een script versie als een voorlopige versie identificeren

PowerShellGet-ondersteuning voor voorlopige versies is gemakkelijker voor scripts dan modules. Script versie beheer wordt alleen ondersteund door PowerShellGet, waardoor er geen compatibiliteits problemen zijn veroorzaakt door het toevoegen van de teken reeks voor de voorlopige versie. Als u een script in de PowerShell Gallery als Prerelease wilt identificeren, voegt u een prerelease-achtervoegsel toe aan een correct opgemaakte versie teken reeks in de meta gegevens van het script.

Een voorbeeld sectie van een script manifest met een voorlopige versie ziet er als volgt uit:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Als u een prerelease-achtervoegsel wilt gebruiken, moet de versie teken reeks voldoen aan de volgende vereisten:

- Een prerelease-achtervoegsel mag alleen worden opgegeven als de versie 3 segmenten is voor Major. minor. build.
  Dit wordt uitgelijnd met SemVer v 1.0.0
- Het voor voegsel van de prerelease is een teken reeks die begint met een afbreek streepje en ASCII-alfanumerieke tekens kan bevatten [0-9 bis-Za-z-]
- Er worden op dit moment alleen SemVer v 1.0.0-Prerelease-teken reeksen ondersteund, dus het achtervoegsel van de prerelease **mag geen** punt of + [. +] bevatten, dat is toegestaan in SemVer 2,0
- Voor beelden van ondersteunde PrereleaseString-teken reeksen zijn:-alpha,-alpha1,-BETA,-update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impact op de versie voor de sorteer volgorde en installatie mappen

Wijzigingen in de sorteer volgorde worden gesorteerd wanneer u een prerelease-versie gebruikt. Dit is belang rijk wanneer u naar de PowerShell Gallery publiceert en wanneer u scripts installeert met behulp van PowerShellGet-opdrachten. Als er twee script versies met het versie nummer bestaan, is de sorteer volgorde gebaseerd op het teken reeks gedeelte na het afbreek streepje. Versie 2.5.0-alpha is dus kleiner dan 2.5.0-Beta, wat kleiner is dan 2.5.0-gamma. Als twee scripts hetzelfde versie nummer hebben en er slechts één een PrereleaseString heeft, wordt aangenomen dat het script **zonder** het Prerelease-achtervoegsel de productie-gereede versie is en wordt deze als een grotere versie gesorteerd dan de voorlopige versie. Als voor beeld bij het vergelijken van Releases 2.5.0 en 2.5.0-Beta, wordt de 2.5.0-versie als een groter van beide beschouwd.

Wanneer u publiceert naar de PowerShell Gallery, moet de versie van het script dat wordt gepubliceerd, standaard een grotere versie hebben dan een eerder gepubliceerde versie in de PowerShell Gallery. Een uitgever kan versie 2.5.0-alpha met 2.5.0-Beta of met 2.5.0 (zonder Prerelease-achtervoegsel) bijwerken.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Voorlopige pakketten zoeken en ophalen met behulp van PowerShellGet-opdrachten

Voor het verwerken van prerelease-pakketten met behulp van PowerShellGet zoeken-script, install-script, update-script en Save-script opdrachten moet u de vlag-AllowPrerelease toevoegen. Als-AllowPrerelease is opgegeven, worden voorlopige pakketten opgenomen als deze aanwezig zijn. Als u de vlag-AllowPrerelease niet opgeeft, worden er geen voorlopige pakketten weer gegeven.

De enige uitzonde ringen hierop in de PowerShellGet-script opdrachten zijn Get-InstalledScript en sommige gevallen met uninstall-script.

- Get-InstalledScript toont altijd automatisch de voorlopige gegevens in de versie teken reeks als deze aanwezig is.
- Uninstall-script wordt standaard de meest recente versie van een script verwijderd als **er geen versie** is opgegeven. Dat gedrag is niet gewijzigd. Als er echter een prerelease-versie is opgegeven `-RequiredVersion`met `-AllowPrerelease` , is vereist.

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

Uninstall-script verwijdert de huidige versie van een script wanneer-RequiredVersion niet is opgegeven.
Als-RequiredVersion is opgegeven en een prerelease is, moet-AllowPrerelease worden toegevoegd aan de opdracht.

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

## <a name="more-details"></a>Meer Details

- [Versies van de module Prerelease](module-prerelease-support.md)
- [Zoeken-script](/powershell/module/powershellget/find-script)
- [Install-script](/powershell/module/powershellget/install-script)
- [Opslaan-script](/powershell/module/powershellget/save-script)
- [Update-script](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)
