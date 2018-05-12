---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Prerelease-moduleversies
ms.openlocfilehash: e663a42092556ef1c43a7cf236616bf420171af6
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-module-versions"></a>Prerelease-moduleversies

Vanaf versie 1.6.0 bieden PowerShellGet en de PowerShell-galerie ondersteuning voor versies die groter zijn dan 1.0.0 als een prerelease-tagging. Voorafgaand aan deze functie zijn prerelease-items beperkt tot een versie die begint met 0 hebben. Het doel van deze functies is het bieden meer ondersteuning voor [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning aanroepconventie zonder te verbreken achterwaartse compatibiliteit met PowerShell versies 3 en hoger of bestaande versies van PowerShellGet. Dit onderwerp richt zich op de module-specifieke functies. De equivalente functies voor scripts zijn in de [Prerelease-versies van Scripts](script-prerelease-support.md) onderwerp. Deze functies gebruikt, kunnen uitgevers identificeren module of script als versie 2.5.0-alpha en later een versie gereed is voor productie 2.5.0 die de prerelease versie vervangt.

Op een hoog niveau: de prerelease modulefuncties

- Een Prerelease-reeks toevoegen aan de sectie PSData van de module-manifest verwijst naar de module als een prerelease-versie. Wanneer de module wordt gepubliceerd naar de PowerShell-galerie, is deze gegevens opgehaald uit het manifest en gebruikt om deze items te identificeren.
- Ophalen van een prerelease-items vereist - AllowPrerelease vlag toe te voegen aan de PowerShellGet opdrachten Find-Module installeren-Module, Update-Module en opslaan-Module. Als de vlag niet is opgegeven, wordt deze items niet worden weergegeven.
- Moduleversies weergegeven door Find-Module, Get-InstalledModule en in de galerie met PowerShell wordt weergegeven als één tekenreeks met de Prerelease tekenreeks toegevoegd, zoals in 2.5.0-alpha.

Hieronder vindt u details voor de functies.

Deze wijzigingen hebben geen invloed op de ondersteuning van de module-versie die is ingebouwd in PowerShell en compatibel zijn met PowerShell 3.0 en 4.0 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Een moduleversie identificeren als een voorlopige versie

Ondersteuning voor voorlopige versies PowerShellGet vereist het gebruik van twee velden in de Module-Manifest:

- De ModuleVersion opgenomen in het manifest van de module moet een versie 3-onderdeel als een prerelease-versie wordt gebruikt en aan de bestaande PowerShell versiebeheer voldoen moet. De indeling van versie zou A.B.C, waarbij A, B en C alle gehele getallen zijn zijn.
- De Prerelease tekenreeks is opgegeven in het manifest module in de sectie PSData van PrivateData.

Gedetailleerde vereisten voor de Prerelease tekenreeks zijn hieronder.

Een voorbeeld van een module-manifest dat definieert een module als een voorlopige versie in deze sectie eruit als het volgende:

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

De gedetailleerde vereisten voor voorlopige tekenreeks zijn:

- Deze tekenreeks kan alleen worden opgegeven wanneer de ModuleVersion 3 segmenten voor Major.Minor.Build. Dit wordt uitgelijnd met SemVer v1.0.0.
- Een afbreekstreepje is het scheidingsteken tussen het Build-nummer en de Prerelease tekenreeks. Een afbreekstreepje kan worden opgenomen in de Prerelease tekenreeks als het eerste teken alleen.
- De Prerelease tekenreeks mag alleen ASCII-letters en cijfers bevatten [0-9A-Za - z-]. Het is een best practice om te beginnen met de voorlopige versie tekenreeks met een alfanumerieke tekens, omdat deze gemakkelijker te identificeren dat dit een prerelease-versie is bij het scannen van een lijst met items.
- Alleen SemVer v1.0.0 prerelease tekenreeksen worden ondersteund op dit moment. Prerelease tekenreeks __moet niet__ beide punt bevatten of + [. +], die zijn toegestaan in SemVer 2.0.
- Voorbeelden van ondersteunde Prerelease tekenreeks zijn:-alpha, -a1,-bèta, -update20171020

__Voorlopige versies gevolgen voor de mappen en de installatie sorteren__

Sorteervolgorde verandert wanneer u een prerelease-versie, wat belangrijk bij het publiceren van de PowerShell-galerie, en modules met behulp van PowerShellGet opdrachten installeren. Als de Prerelease tekenreeks is opgegeven voor twee modules, wordt de sorteervolgorde is gebaseerd op het volgende op het afbreekstreepje tekenreeksdeel. Dus is versie 2.5.0-alpha kleiner dan 2.5.0-beta, dat is minder dan 2.5.0-gamma. Als twee modules de dezelfde ModuleVersion hebben en slechts één een Prerelease tekenreeks heeft, de module zonder de Prerelease tekenreeks wordt ervan uitgegaan dat de versie gereed is voor productie en worden gesorteerd als een hogere versie dan de prerelease versie (waaronder de voorlopige versie tekenreeks). Als u bijvoorbeeld bij het vergelijken van releases 2.5.0 en 2.5.0-beta, de 2.5.0 versie wordt beschouwd als de grootste van de twee.

Bij het publiceren van de PowerShell-galerie, moet de versie van de module wordt gepubliceerd hebben standaard een hogere versie dan eventuele eerder gepubliceerde versie die in de PowerShell-galerie.

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Zoeken en ophalen van een prerelease-items met PowerShellGet opdrachten

Omgaan met prerelease items met PowerShellGet Find-Module, installatie-Module, Update-Module, en de opdrachten opslaan-Module vereist de vlag - AllowPrerelease toe te voegen. Als - AllowPrerelease is opgegeven, wordt deze prerelease-items worden opgenomen als deze aanwezig zijn. Als de vlag - AllowPrerelease niet is opgegeven, wordt deze items niet weergegeven.

De enige uitzonderingen op dit in de module PowerShellGet opdrachten zijn Get-InstalledModule en in sommige gevallen met Uninstall-Module.

- Get-InstalledModule weergegeven altijd automatisch de prerelease-informatie in de tekenreeks voor modules.
- Verwijderen van de Module standaard verwijdert de meest recente versie van een module als __geen versie__ is opgegeven. Dit gedrag is niet gewijzigd. Echter, als een prerelease-versie wordt opgegeven met - RequiredVersion, - AllowPrerelease is vereist.

## <a name="examples"></a>Voorbeelden

```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Side-by-side-installatie van versies van een module die alleen als gevolg van de voorlopige versie opgegeven verschillen, wordt niet ondersteund. Als u een module met behulp van PowerShellGet installeert, zijn verschillende versies van dezelfde module geïnstalleerde side-by-side door het maken van de naam van een map met de ModuleVersion. De ModuleVersion, zonder de prerelease tekenreeks wordt gebruikt voor naam van de map. Als een gebruiker MyModule versie 2.5.0-alpha installeert, wordt deze naar de map MyModule\2.5.0 worden geïnstalleerd. Als de gebruiker vervolgens 2.5.0-beta installeert, de versie 2.5.0-beta wordt __te veel schrijven__ de inhoud van de map MyModule\2.5.0. Een voordeel hiervan is dat er hoeft te verwijderen de prerelease versie na de installatie van de versie gereed is voor productie. Het volgende voorbeeld ziet u wat ze kunnen verwachten:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Verwijderen-Module kan de meest recente versie van een module wordt verwijderd wanneer - RequiredVersion wordt niet meegeleverd.
-RequiredVersion is opgegeven, en een voorlopige versie, moet - AllowPrerelease worden toegevoegd aan de opdracht.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```

## <a name="more-details"></a>meer informatie

- [Script prerelease-versies](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Installatie-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [Verwijderen-Module](/powershell/gallery/psget/module/psget_uninstall-module)