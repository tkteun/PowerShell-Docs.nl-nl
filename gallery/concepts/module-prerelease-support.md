---
ms.date: 09/26/2017
contributor: keithb
keywords: Galerie, powershell, cmdlet, psget
title: Voor voorlopige moduleversies
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084858"
---
# <a name="prerelease-module-versions"></a>Voor voorlopige moduleversies

Vanaf versie 1.6.0, bieden powershellget hebt en de PowerShell Gallery ondersteuning voor het labelen van versies die groter zijn dan 1.0.0 als een voorlopige versie. Voorlopige pakketten zijn voordat u deze functie beperkt tot het met een versie die begint met 0. Het doel van deze functies is te bieden meer ondersteuning voor [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versiebeheer Verdrag zonder dat belangrijke achterwaartse compatibiliteit met PowerShell 3 en hoger of bestaande versie van PowerShellGet. In dit onderwerp richt zich op de module-specifieke functies. De equivalente functies voor scripts zijn de [voorlopige versies van Scripts](script-prerelease-support.md) onderwerp. Met behulp van deze functies, kunnen uitgevers identificeren van een module of script als versie 2.5.0-alpha en later een versie gereed is voor productie 2.5.0 die de prerelease versie vervangt.

Op hoog niveau, de prerelease modulefuncties zijn onder andere:

- Een Prerelease-tekenreeks toe te voegen aan de sectie PSData van de module-manifest geeft aan dat de module een prerelease-versie. Wanneer de module is gepubliceerd naar de PowerShell Gallery, is deze gegevens opgehaald uit het manifest en gebruikt voor het identificeren van prerelease-pakketten.
- Ophalen van prerelease-pakketten vereist toe te voegen `-AllowPrerelease` vlag voor de PowerShellGet-opdrachten `Find-Module`, `Install-Module`, `Update-Module`, en `Save-Module`. Als de vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.
- Moduleversies weergegeven door `Find-Module`, `Get-InstalledModule`, en in de PowerShell Gallery wordt weergegeven als een enkele tekenreeks met de Prerelease tekenreeks toegevoegd, zoals in 2.5.0-alpha.

Details voor de functies zijn hieronder vermeld.

Deze wijzigingen hebben geen invloed op de ondersteuning van de module-versie die is ingebouwd in PowerShell en compatibel zijn met PowerShell 3.0 en 4.0 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>De versie van een module te identificeren als een voorlopige versie

PowerShellGet-ondersteuning voor voorlopige versies vereist het gebruik van twee velden die in de Module-Manifest:

- De opgenomen in de module-manifest ModuleVersion moet een versie 3-onderdeel als een prerelease-versie wordt gebruikt en aan de bestaande versiebeheer in PowerShell voldoen moet. De indeling van versie zou A.B.C, waarbij A, B en C gehele getallen zijn zijn.
- De Prerelease tekenreeks is opgegeven in de module-manifest, in de sectie PSData van PrivateData.

Gedetailleerde vereisten voor de Prerelease tekenreeks staan hieronder.

Een voorbeeld van een modulemanifest dat een module als een voorlopige versie definieert in deze sectie eruit als volgt uit:

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

- Deze tekenreeks kan alleen worden opgegeven wanneer de ModuleVersion 3 segmenten voor Major.Minor.Build is. Deze correspondeert met SemVer versie 1.0.0 gebruikt.
- Een koppelteken is het scheidingsteken tussen de Build-nummer en de Prerelease tekenreeks. Een koppelteken mag worden opgenomen in de Prerelease tekenreeks als het eerste teken, alleen.
- De Prerelease tekenreeks mag alleen ASCII-letters [0-9 bis-Za - z-]. Het is een best practice om te beginnen met de voorlopige versie tekenreeks met een alpha-teken, zoals het eenvoudiger om te identificeren dat dit een voorlopige versie is bij het scannen van een lijst met pakketten.
- Alleen SemVer v1.0.0 prerelease tekenreeksen worden ondersteund op dit moment. Voorlopige tekenreeks **moet niet** beide punt bevatten of + [. +], die zijn toegestaan in SemVer 2.0.
- Voorbeelden van ondersteunde Prerelease tekenreeks zijn:-alpha, a1,-bèta, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Voorlopige versies gevolgen voor sorteren en de installatie-mappen

Sorteervolgorde wordt gewijzigd wanneer u een prerelease-versie, dit belangrijk is bij het publiceren naar de PowerShell Gallery, en bij het installeren van modules met PowerShellGet-opdrachten. Als de Prerelease tekenreeks is opgegeven voor de twee modules, de sorteervolgorde is op basis van de tekenreeks deel afbreekstreepjes te volgen. Dus, versie 2.5.0-alpha is kleiner dan 2.5.0-beta, die kleiner is dan 2.5.0-gamma. Als twee modules de dezelfde ModuleVersion hebben en slechts één een voorlopige tekenreeks is, de module zonder de Prerelease tekenreeks wordt ervan uitgegaan dat de versie gereed is voor productie en als een hogere versie dan de prerelease-versie (waaronder de voorlopige versie worden gesorteerd tekenreeks). Een voorbeeld: bij het vergelijken van releases 2.5.0 en 2.5.0-beta, de 2.5.0 versie wordt beschouwd als de hoogste waarde van de twee.

Bij het publiceren naar de PowerShell Gallery, moet de versie van de module worden gepubliceerd hebben standaard een hogere versie dan alle eerder gepubliceerde versie die in de PowerShell Gallery.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Zoeken en ophalen van prerelease pakketten met PowerShellGet-opdrachten

Omgaan met prerelease-pakketten zoeken van de PowerShellGet-Module, Install-Module, Update-Module, gebruikt en opdrachten Save-Module vereist de vlag - AllowPrerelease toe te voegen. Als - AllowPrerelease is opgegeven, wordt deze prerelease-pakketten worden opgenomen als deze aanwezig zijn. Als AllowPrerelease - vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.

De enige uitzonderingen op deze in de PowerShellGet-module-opdrachten zijn Get-InstalledModule en soms met Uninstall-Module.

- Get-InstalledModule weergegeven altijd automatisch de prerelease-informatie in de tekenreeks voor modules.
- Verwijderen van de Module wordt standaard verwijderen van de meest recente versie van een module als __geen versie__ is opgegeven. Dit gedrag is niet gewijzigd. Echter, als een prerelease-versie is opgegeven met behulp van - RequiredVersion, - AllowPrerelease is vereist.

## <a name="examples"></a>Voorbeelden

Stel dat de PowerShell Gallery heeft TestPackage moduleversies 1.8.0 en 1.9.0-alpha. Als `-AllowPrerelease` is niet opgegeven, worden alleen versie 1.8.0 geretourneerd.

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

Voor het installeren van een voorlopige versie, moet u altijd - AllowPrerelease opgeven. Opgeven van een prerelease-versie-tekenreeks is niet voldoende.

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

De vorige opdracht is mislukt omdat - AllowPrerelease is niet opgegeven. Toe te voegen `-AllowPrerelease` leidt tot succes.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Side-by-side-installatie van de versies van een module die alleen vanwege de voorlopige versie opgegeven verschillen wordt niet ondersteund. Bij het installeren van een module met PowerShellGet, zijn verschillende versies van dezelfde module geïnstalleerd side-by-side met het maken van de naam van een map met behulp van de ModuleVersion. De ModuleVersion, zonder de prerelease tekenreeks wordt gebruikt voor naam van de map. Als een gebruiker MyModule versie 2.5.0-alpha installeert, wordt deze geïnstalleerd op de `MyModule\2.5.0` map. Als de gebruiker wordt vervolgens geïnstalleerd 2.5.0-beta, de versie 2.5.0-beta wordt **overschrijven** de inhoud van de map `MyModule\2.5.0`. Een voordeel van deze benadering is dat er niet nodig voor ongedaan maken-installatie de prerelease versie na de installatie van de versie gereed is voor productie. Het volgende voorbeeld ziet u wat u kunt verwachten:

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

Verwijderen-Module worden de meest recente versie van een module verwijderen wanneer - RequiredVersion is niet opgegeven.
Als - RequiredVersion is opgegeven, en een voorlopige versie is, moet - AllowPrerelease worden toegevoegd aan de opdracht.

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

- [Script voor voorlopige versies](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
