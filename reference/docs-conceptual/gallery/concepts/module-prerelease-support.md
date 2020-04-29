---
ms.date: 09/26/2017
contributor: keithb
keywords: Galerie, Power shell, cmdlet, psget
title: Versies van de module Prerelease
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328936"
---
# <a name="prerelease-module-versions"></a>Versies van de module Prerelease

Vanaf versie 1.6.0, PowerShellGet en de PowerShell Gallery bieden ondersteuning voor coderings versies die groter zijn dan 1.0.0 als een voorlopige versie. Vóór deze functie werden voorlopige pakketten beperkt tot een versie die begint met 0. Het doel van deze functies is om meer ondersteuning te bieden voor [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) versie beheer, zonder achterwaartse compatibiliteit te verbreken met Power shell-versies 3 en hoger, of bestaande versies van PowerShellGet. Dit onderwerp richt zich op de module-specifieke functies. De equivalente functies voor scripts vindt u in het onderwerp [voorlopige versies van scripts](script-prerelease-support.md) . Met behulp van deze functies kunnen uitgevers een module of script identificeren als versie 2.5.0-alpha en later een productie versie-2.5.0 vrijgeven die de voorlopige versie vervangt.

Op hoog niveau zijn de functies van de prerelease-module onder andere:

- Als u een prerelease-teken reeks toevoegt aan de sectie PSData van het module manifest, wordt de module geïdentificeerd als een voorlopige versie. Wanneer de module wordt gepubliceerd naar de PowerShell Gallery, worden deze gegevens geëxtraheerd uit het manifest en gebruikt om voorlopige pakketten te identificeren.
- Voor het verkrijgen van voorlopige pakketten moet `-AllowPrerelease` u een markering toevoegen aan `Find-Module`de `Install-Module`PowerShellGet `Update-Module`-opdrachten `Save-Module`,, en. Als de vlag niet is opgegeven, worden er geen voorlopige pakketten weer gegeven.
- Module versies die worden `Find-Module`weer `Get-InstalledModule`gegeven door, en in de PowerShell Gallery worden weer gegeven als één teken reeks met de teken reeks Prerelease toegevoegd, zoals in 2.5.0-alpha.

Hieronder vindt u meer informatie over de functies.

Deze wijzigingen hebben geen invloed op de ondersteuning van module versies die in Power shell is ingebouwd en zijn compatibel met Power Shell 3,0, 4,0 en 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Een module versie identificeren als Prerelease

Voor PowerShellGet-ondersteuning voor voorlopige versies is het gebruik van twee velden in het module manifest vereist:

- De ModuleVersion die is opgenomen in het module manifest, moet een versie van 3 onderdelen zijn als een prerelease-versie wordt gebruikt en moet voldoen aan bestaande Power shell-versies. De versie-indeling zou A. B. C zijn, waarbij A, B en C alle gehele getallen zijn.
- De teken reeks voor Prerelease is opgegeven in het module manifest in het gedeelte PSData van PrivateData.

Gedetailleerde vereisten voor de voorlopige versie van de teken reeks vindt u hieronder.

Een voor beeld van een module manifest dat een module definieert als een prerelease, ziet er als volgt uit:

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

De gedetailleerde vereisten voor de prerelease-teken reeks zijn:

- Prerelease-teken reeks kan alleen worden opgegeven als ModuleVersion 3 segmenten is voor Major. minor. build. Dit komt overeen met SemVer v 1.0.0.
- Een afbreek streepje is het scheidings teken tussen het buildnummer en de voorlopige versie. Een afbreek streepje kan alleen worden opgenomen in de teken reeks Prerelease als het eerste teken.
- De voorlopige teken reeks mag alleen ASCII-alfanumerieke tekens [0-9-Za-z-] bevatten. Het is een best practice om de voorlopige teken reeks met een Alfa teken te starten, omdat het gemakkelijker is om te identificeren dat dit een voorlopige versie is bij het scannen van een lijst met pakketten.
- Er worden op dit moment alleen SemVer v 1.0.0-Prerelease-teken reeksen ondersteund. De teken reeks voor Prerelease **mag geen** punt of + [. +] bevatten, die zijn toegestaan in SemVer 2,0.
- Voor beelden van ondersteunde Prerelease-teken reeksen zijn:-alpha,-alpha1,-BETA,-update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impact op de versie voor de sorteer volgorde en installatie mappen

De sorteer volgorde verandert wanneer u een prerelease-versie gebruikt. Dit is belang rijk bij het publiceren naar de PowerShell Gallery en wanneer u modules installeert met behulp van PowerShellGet-opdrachten. Als de teken reeks voor Prerelease is opgegeven voor twee modules, is de sorteer volgorde gebaseerd op het teken reeks gedeelte na het afbreek streepje. Versie 2.5.0-alpha is dus kleiner dan 2.5.0-Beta, wat kleiner is dan 2.5.0-gamma. Als twee modules dezelfde ModuleVersion hebben en er slechts één van een voorlopige versie teken reeks is, wordt ervan uitgegaan dat de module zonder de prerelease-teken reeks de productie-gereedheid is en worden gesorteerd als een grotere versie dan de voorlopige versie (die de prerelease-teken reeks bevat). Als voor beeld bij het vergelijken van Releases 2.5.0 en 2.5.0-Beta, wordt de 2.5.0-versie als een groter van beide beschouwd.

Wanneer u publiceert naar de PowerShell Gallery, moet de versie van de module die wordt gepubliceerd, standaard een grotere versie hebben dan een eerder gepubliceerde versie in de PowerShell Gallery.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Voorlopige pakketten zoeken en ophalen met behulp van PowerShellGet-opdrachten

Voor het verwerken van pakketten die gebruikmaken van de PowerShellGet find-module, install-module, update-module en Save-module-opdrachten moet u de vlag-AllowPrerelease toevoegen. Als-AllowPrerelease is opgegeven, worden voorlopige pakketten opgenomen als deze aanwezig zijn. Als u de vlag-AllowPrerelease niet opgeeft, worden er geen voorlopige pakketten weer gegeven.

De enige uitzonde ringen hierop in de PowerShellGet-module opdrachten zijn Get-InstalledModule en sommige gevallen met Uninstall-module.

- Get-InstalledModule toont altijd automatisch de voorlopige gegevens in de versie teken reeks voor modules.
- Uninstall: als __er geen versie__ is opgegeven, wordt de meest recente versie van een module standaard verwijderd. Dat gedrag is niet gewijzigd. Als er echter een prerelease-versie is opgegeven met-RequiredVersion,-AllowPrerelease is vereist.

## <a name="examples"></a>Voorbeelden

Stel dat de PowerShell Gallery TestPackage module versies 1.8.0 en 1.9.0-alpha heeft. Als `-AllowPrerelease` niet wordt opgegeven, wordt alleen versie 1.8.0 geretourneerd.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

Als u een prerelease wilt installeren, moet u altijd-AllowPrerelease opgeven. Het opgeven van een teken reeks voor de voorlopige versie is niet voldoende.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

De vorige opdracht is mislukt omdat-AllowPrerelease niet is opgegeven. Toevoegen `-AllowPrerelease` resulteert in geslaagde pogingen.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Gelijktijdige installatie van versies van een module die alleen verschillen als gevolg van de opgegeven Prerelease, wordt niet ondersteund. Wanneer u een module installeert met behulp van PowerShellGet, worden verschillende versies van dezelfde module naast elkaar geïnstalleerd door de naam van een map te maken met behulp van de ModuleVersion. De ModuleVersion, zonder de voorlopige release teken reeks, wordt gebruikt voor de mapnaam. Als een gebruiker MyModule-versie 2.5.0-alpha installeert, wordt deze in de `MyModule\2.5.0` map geïnstalleerd. Als de gebruiker vervolgens 2.5.0-beta installeert, wordt de inhoud van de `MyModule\2.5.0`map **overschreven** door de versie van de 2.5.0-Beta. Een voor deel van deze benadering is dat het niet nodig is om de installatie van de voorlopige versie ongedaan te maken na installatie van de productie-gereede versie. In het voor beeld hieronder ziet u wat u kunt verwachten:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

Uninstall-module verwijdert de meest recente versie van een module als-RequiredVersion niet is opgegeven.
Als-RequiredVersion is opgegeven en een prerelease is, moet-AllowPrerelease worden toegevoegd aan de opdracht.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>Meer informatie

- [Voorlopige script versies](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Installatie-module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-module](/powershell/module/powershellget/uninstall-module)
