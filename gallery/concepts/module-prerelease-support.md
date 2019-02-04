---
ms.date: 09/26/2017
contributor: keithb
keywords: Galerie, powershell, cmdlet, psget
title: Voor voorlopige moduleversies
ms.openlocfilehash: f58b5adfeba7ed06d231c76accbd52508c7d67d6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684274"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="2cab8-103">Voor voorlopige moduleversies</span><span class="sxs-lookup"><span data-stu-id="2cab8-103">Prerelease Module Versions</span></span>

<span data-ttu-id="2cab8-104">Vanaf versie 1.6.0, bieden powershellget hebt en de PowerShell Gallery ondersteuning voor het labelen van versies die groter zijn dan 1.0.0 als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="2cab8-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="2cab8-105">Voorlopige pakketten zijn voordat u deze functie beperkt tot het met een versie die begint met 0.</span><span class="sxs-lookup"><span data-stu-id="2cab8-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="2cab8-106">Het doel van deze functies is te bieden meer ondersteuning voor [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versiebeheer Verdrag zonder dat belangrijke achterwaartse compatibiliteit met PowerShell 3 en hoger of bestaande versie van PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="2cab8-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="2cab8-107">In dit onderwerp richt zich op de module-specifieke functies.</span><span class="sxs-lookup"><span data-stu-id="2cab8-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="2cab8-108">De equivalente functies voor scripts zijn de [voorlopige versies van Scripts](script-prerelease-support.md) onderwerp.</span><span class="sxs-lookup"><span data-stu-id="2cab8-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="2cab8-109">Met behulp van deze functies, kunnen uitgevers identificeren van een module of script als versie 2.5.0-alpha en later een versie gereed is voor productie 2.5.0 die de prerelease versie vervangt.</span><span class="sxs-lookup"><span data-stu-id="2cab8-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="2cab8-110">Op hoog niveau, de prerelease modulefuncties zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="2cab8-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="2cab8-111">Een Prerelease-tekenreeks toe te voegen aan de sectie PSData van de module-manifest geeft aan dat de module een prerelease-versie.</span><span class="sxs-lookup"><span data-stu-id="2cab8-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="2cab8-112">Wanneer de module is gepubliceerd naar de PowerShell Gallery, is deze gegevens opgehaald uit het manifest en gebruikt voor het identificeren van prerelease-pakketten.</span><span class="sxs-lookup"><span data-stu-id="2cab8-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="2cab8-113">Ophalen van prerelease-pakketten vereist toe te voegen `-AllowPrerelease` vlag voor de PowerShellGet-opdrachten `Find-Module`, `Install-Module`, `Update-Module`, en `Save-Module`.</span><span class="sxs-lookup"><span data-stu-id="2cab8-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="2cab8-114">Als de vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="2cab8-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="2cab8-115">Moduleversies weergegeven door `Find-Module`, `Get-InstalledModule`, en in de PowerShell Gallery wordt weergegeven als een enkele tekenreeks met de Prerelease tekenreeks toegevoegd, zoals in 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="2cab8-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="2cab8-116">Details voor de functies zijn hieronder vermeld.</span><span class="sxs-lookup"><span data-stu-id="2cab8-116">Details for the features are included below.</span></span>

<span data-ttu-id="2cab8-117">Deze wijzigingen hebben geen invloed op de ondersteuning van de module-versie die is ingebouwd in PowerShell en compatibel zijn met PowerShell 3.0 en 4.0 5.</span><span class="sxs-lookup"><span data-stu-id="2cab8-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="2cab8-118">De versie van een module te identificeren als een voorlopige versie</span><span class="sxs-lookup"><span data-stu-id="2cab8-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="2cab8-119">PowerShellGet-ondersteuning voor voorlopige versies vereist het gebruik van twee velden die in de Module-Manifest:</span><span class="sxs-lookup"><span data-stu-id="2cab8-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="2cab8-120">De opgenomen in de module-manifest ModuleVersion moet een versie 3-onderdeel als een prerelease-versie wordt gebruikt en aan de bestaande versiebeheer in PowerShell voldoen moet.</span><span class="sxs-lookup"><span data-stu-id="2cab8-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="2cab8-121">De indeling van versie zou A.B.C, waarbij A, B en C gehele getallen zijn zijn.</span><span class="sxs-lookup"><span data-stu-id="2cab8-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="2cab8-122">De Prerelease tekenreeks is opgegeven in de module-manifest, in de sectie PSData van PrivateData.</span><span class="sxs-lookup"><span data-stu-id="2cab8-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="2cab8-123">Gedetailleerde vereisten voor de Prerelease tekenreeks staan hieronder.</span><span class="sxs-lookup"><span data-stu-id="2cab8-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="2cab8-124">Een voorbeeld van een modulemanifest dat een module als een voorlopige versie definieert in deze sectie eruit als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="2cab8-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="2cab8-125">De gedetailleerde vereisten voor voorlopige tekenreeks zijn:</span><span class="sxs-lookup"><span data-stu-id="2cab8-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="2cab8-126">Deze tekenreeks kan alleen worden opgegeven wanneer de ModuleVersion 3 segmenten voor Major.Minor.Build is.</span><span class="sxs-lookup"><span data-stu-id="2cab8-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="2cab8-127">Deze correspondeert met SemVer versie 1.0.0 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2cab8-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="2cab8-128">Een koppelteken is het scheidingsteken tussen de Build-nummer en de Prerelease tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="2cab8-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="2cab8-129">Een koppelteken mag worden opgenomen in de Prerelease tekenreeks als het eerste teken, alleen.</span><span class="sxs-lookup"><span data-stu-id="2cab8-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="2cab8-130">De Prerelease tekenreeks mag alleen ASCII-letters [0-9 bis-Za - z-].</span><span class="sxs-lookup"><span data-stu-id="2cab8-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="2cab8-131">Het is een best practice om te beginnen met de voorlopige versie tekenreeks met een alpha-teken, zoals het eenvoudiger om te identificeren dat dit een voorlopige versie is bij het scannen van een lijst met pakketten.</span><span class="sxs-lookup"><span data-stu-id="2cab8-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="2cab8-132">Alleen SemVer v1.0.0 prerelease tekenreeksen worden ondersteund op dit moment.</span><span class="sxs-lookup"><span data-stu-id="2cab8-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="2cab8-133">Voorlopige tekenreeks **moet niet** beide punt bevatten of + [. +], die zijn toegestaan in SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="2cab8-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="2cab8-134">Voorbeelden van ondersteunde Prerelease tekenreeks zijn:-alpha, a1,-bèta, -update20171020</span><span class="sxs-lookup"><span data-stu-id="2cab8-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="2cab8-135">Voorlopige versies gevolgen voor sorteren en de installatie-mappen</span><span class="sxs-lookup"><span data-stu-id="2cab8-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="2cab8-136">Sorteervolgorde wordt gewijzigd wanneer u een prerelease-versie, dit belangrijk is bij het publiceren naar de PowerShell Gallery, en bij het installeren van modules met PowerShellGet-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="2cab8-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="2cab8-137">Als de Prerelease tekenreeks is opgegeven voor de twee modules, de sorteervolgorde is op basis van de tekenreeks deel afbreekstreepjes te volgen.</span><span class="sxs-lookup"><span data-stu-id="2cab8-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="2cab8-138">Dus, versie 2.5.0-alpha is kleiner dan 2.5.0-beta, die kleiner is dan 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="2cab8-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="2cab8-139">Als twee modules de dezelfde ModuleVersion hebben en slechts één een voorlopige tekenreeks is, de module zonder de Prerelease tekenreeks wordt ervan uitgegaan dat de versie gereed is voor productie en als een hogere versie dan de prerelease-versie (waaronder de voorlopige versie worden gesorteerd tekenreeks).</span><span class="sxs-lookup"><span data-stu-id="2cab8-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="2cab8-140">Een voorbeeld: bij het vergelijken van releases 2.5.0 en 2.5.0-beta, de 2.5.0 versie wordt beschouwd als de hoogste waarde van de twee.</span><span class="sxs-lookup"><span data-stu-id="2cab8-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="2cab8-141">Bij het publiceren naar de PowerShell Gallery, moet de versie van de module worden gepubliceerd hebben standaard een hogere versie dan alle eerder gepubliceerde versie die in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="2cab8-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="2cab8-142">Zoeken en ophalen van prerelease pakketten met PowerShellGet-opdrachten</span><span class="sxs-lookup"><span data-stu-id="2cab8-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="2cab8-143">Omgaan met prerelease-pakketten zoeken van de PowerShellGet-Module, Install-Module, Update-Module, gebruikt en opdrachten Save-Module vereist de vlag - AllowPrerelease toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="2cab8-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="2cab8-144">Als - AllowPrerelease is opgegeven, wordt deze prerelease-pakketten worden opgenomen als deze aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="2cab8-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="2cab8-145">Als AllowPrerelease - vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="2cab8-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="2cab8-146">De enige uitzonderingen op deze in de PowerShellGet-module-opdrachten zijn Get-InstalledModule en soms met Uninstall-Module.</span><span class="sxs-lookup"><span data-stu-id="2cab8-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="2cab8-147">Get-InstalledModule weergegeven altijd automatisch de prerelease-informatie in de tekenreeks voor modules.</span><span class="sxs-lookup"><span data-stu-id="2cab8-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="2cab8-148">Verwijderen van de Module wordt standaard verwijderen van de meest recente versie van een module als __geen versie__ is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2cab8-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="2cab8-149">Dit gedrag is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2cab8-149">That behavior has not changed.</span></span> <span data-ttu-id="2cab8-150">Echter, als een prerelease-versie is opgegeven met behulp van - RequiredVersion, - AllowPrerelease is vereist.</span><span class="sxs-lookup"><span data-stu-id="2cab8-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="2cab8-151">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="2cab8-151">Examples</span></span>

<span data-ttu-id="2cab8-152">Stel dat de PowerShell Gallery heeft TestPackage moduleversies 1.8.0 en 1.9.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="2cab8-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="2cab8-153">Als `-AllowPrerelease` is niet opgegeven, worden alleen versie 1.8.0 geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2cab8-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

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

<span data-ttu-id="2cab8-154">Voor het installeren van een voorlopige versie, moet u altijd - AllowPrerelease opgeven.</span><span class="sxs-lookup"><span data-stu-id="2cab8-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="2cab8-155">Opgeven van een prerelease-versie-tekenreeks is niet voldoende.</span><span class="sxs-lookup"><span data-stu-id="2cab8-155">Specifying a prerelease version string is not sufficient.</span></span>

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

<span data-ttu-id="2cab8-156">De vorige opdracht is mislukt omdat - AllowPrerelease is niet opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2cab8-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="2cab8-157">Toe te voegen `-AllowPrerelease` leidt tot succes.</span><span class="sxs-lookup"><span data-stu-id="2cab8-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="2cab8-158">Side-by-side-installatie van de versies van een module die alleen vanwege de voorlopige versie opgegeven verschillen wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="2cab8-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="2cab8-159">Bij het installeren van een module met PowerShellGet, zijn verschillende versies van dezelfde module geïnstalleerd side-by-side met het maken van de naam van een map met behulp van de ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="2cab8-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="2cab8-160">De ModuleVersion, zonder de prerelease tekenreeks wordt gebruikt voor naam van de map.</span><span class="sxs-lookup"><span data-stu-id="2cab8-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="2cab8-161">Als een gebruiker MyModule versie 2.5.0-alpha installeert, wordt deze geïnstalleerd op de `MyModule\2.5.0` map.</span><span class="sxs-lookup"><span data-stu-id="2cab8-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="2cab8-162">Als de gebruiker wordt vervolgens geïnstalleerd 2.5.0-beta, de versie 2.5.0-beta wordt **overschrijven** de inhoud van de map `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="2cab8-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="2cab8-163">Een voordeel van deze benadering is dat er niet nodig voor ongedaan maken-installatie de prerelease versie na de installatie van de versie gereed is voor productie.</span><span class="sxs-lookup"><span data-stu-id="2cab8-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="2cab8-164">Het volgende voorbeeld ziet u wat u kunt verwachten:</span><span class="sxs-lookup"><span data-stu-id="2cab8-164">The example below shows what to expect:</span></span>

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

<span data-ttu-id="2cab8-165">Verwijderen-Module worden de meest recente versie van een module verwijderen wanneer - RequiredVersion is niet opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2cab8-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="2cab8-166">Als - RequiredVersion is opgegeven, en een voorlopige versie is, moet - AllowPrerelease worden toegevoegd aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="2cab8-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module

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

## <a name="more-details"></a><span data-ttu-id="2cab8-167">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="2cab8-167">More details</span></span>

- [<span data-ttu-id="2cab8-168">Script voor voorlopige versies</span><span class="sxs-lookup"><span data-stu-id="2cab8-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="2cab8-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="2cab8-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="2cab8-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="2cab8-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="2cab8-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="2cab8-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="2cab8-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="2cab8-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="2cab8-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="2cab8-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="2cab8-174">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="2cab8-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
