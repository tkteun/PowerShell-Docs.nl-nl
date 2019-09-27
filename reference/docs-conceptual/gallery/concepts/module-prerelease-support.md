---
ms.date: 09/26/2017
contributor: keithb
keywords: Galerie, Power shell, cmdlet, psget
title: Versies van de module Prerelease
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328936"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="d7841-103">Versies van de module Prerelease</span><span class="sxs-lookup"><span data-stu-id="d7841-103">Prerelease Module Versions</span></span>

<span data-ttu-id="d7841-104">Vanaf versie 1.6.0, PowerShellGet en de PowerShell Gallery bieden ondersteuning voor coderings versies die groter zijn dan 1.0.0 als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="d7841-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="d7841-105">Vóór deze functie werden voorlopige pakketten beperkt tot een versie die begint met 0.</span><span class="sxs-lookup"><span data-stu-id="d7841-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="d7841-106">Het doel van deze functies is om meer ondersteuning te bieden voor [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) versie beheer, zonder achterwaartse compatibiliteit te verbreken met Power shell-versies 3 en hoger, of bestaande versies van PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d7841-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="d7841-107">Dit onderwerp richt zich op de module-specifieke functies.</span><span class="sxs-lookup"><span data-stu-id="d7841-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="d7841-108">De equivalente functies voor scripts vindt u in het onderwerp [voorlopige versies van scripts](script-prerelease-support.md) .</span><span class="sxs-lookup"><span data-stu-id="d7841-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="d7841-109">Met behulp van deze functies kunnen uitgevers een module of script identificeren als versie 2.5.0-alpha en later een productie versie-2.5.0 vrijgeven die de voorlopige versie vervangt.</span><span class="sxs-lookup"><span data-stu-id="d7841-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="d7841-110">Op hoog niveau zijn de functies van de prerelease-module onder andere:</span><span class="sxs-lookup"><span data-stu-id="d7841-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="d7841-111">Als u een prerelease-teken reeks toevoegt aan de sectie PSData van het module manifest, wordt de module geïdentificeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="d7841-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="d7841-112">Wanneer de module wordt gepubliceerd naar de PowerShell Gallery, worden deze gegevens geëxtraheerd uit het manifest en gebruikt om voorlopige pakketten te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d7841-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="d7841-113">Voor het verkrijgen van voorlopige pakketten moet `-AllowPrerelease` u een markering toevoegen aan `Find-Module`de PowerShellGet `Update-Module`-opdrachten `Save-Module`, `Install-Module`, en.</span><span class="sxs-lookup"><span data-stu-id="d7841-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="d7841-114">Als de vlag niet is opgegeven, worden er geen voorlopige pakketten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7841-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="d7841-115">Module versies die worden `Find-Module`weer `Get-InstalledModule`gegeven door, en in de PowerShell Gallery worden weer gegeven als één teken reeks met de teken reeks Prerelease toegevoegd, zoals in 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="d7841-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="d7841-116">Hieronder vindt u meer informatie over de functies.</span><span class="sxs-lookup"><span data-stu-id="d7841-116">Details for the features are included below.</span></span>

<span data-ttu-id="d7841-117">Deze wijzigingen hebben geen invloed op de ondersteuning van module versies die in Power shell is ingebouwd en zijn compatibel met Power Shell 3,0, 4,0 en 5.</span><span class="sxs-lookup"><span data-stu-id="d7841-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="d7841-118">Een module versie identificeren als Prerelease</span><span class="sxs-lookup"><span data-stu-id="d7841-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="d7841-119">Voor PowerShellGet-ondersteuning voor voorlopige versies is het gebruik van twee velden in het module manifest vereist:</span><span class="sxs-lookup"><span data-stu-id="d7841-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="d7841-120">De ModuleVersion die is opgenomen in het module manifest, moet een versie van 3 onderdelen zijn als een prerelease-versie wordt gebruikt en moet voldoen aan bestaande Power shell-versies.</span><span class="sxs-lookup"><span data-stu-id="d7841-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="d7841-121">De versie-indeling zou A. B. C zijn, waarbij A, B en C alle gehele getallen zijn.</span><span class="sxs-lookup"><span data-stu-id="d7841-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="d7841-122">De teken reeks voor Prerelease is opgegeven in het module manifest in het gedeelte PSData van PrivateData.</span><span class="sxs-lookup"><span data-stu-id="d7841-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="d7841-123">Gedetailleerde vereisten voor de voorlopige versie van de teken reeks vindt u hieronder.</span><span class="sxs-lookup"><span data-stu-id="d7841-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="d7841-124">Een voor beeld van een module manifest dat een module definieert als een prerelease, ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="d7841-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="d7841-125">De gedetailleerde vereisten voor de prerelease-teken reeks zijn:</span><span class="sxs-lookup"><span data-stu-id="d7841-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="d7841-126">Prerelease-teken reeks kan alleen worden opgegeven als ModuleVersion 3 segmenten is voor Major. minor. build.</span><span class="sxs-lookup"><span data-stu-id="d7841-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="d7841-127">Dit komt overeen met SemVer v 1.0.0.</span><span class="sxs-lookup"><span data-stu-id="d7841-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="d7841-128">Een afbreek streepje is het scheidings teken tussen het buildnummer en de voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="d7841-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="d7841-129">Een afbreek streepje kan alleen worden opgenomen in de teken reeks Prerelease als het eerste teken.</span><span class="sxs-lookup"><span data-stu-id="d7841-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="d7841-130">De voorlopige teken reeks mag alleen ASCII-alfanumerieke tekens [0-9-Za-z-] bevatten.</span><span class="sxs-lookup"><span data-stu-id="d7841-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="d7841-131">Het is een best practice om de voorlopige teken reeks met een Alfa teken te starten, omdat het gemakkelijker is om te identificeren dat dit een voorlopige versie is bij het scannen van een lijst met pakketten.</span><span class="sxs-lookup"><span data-stu-id="d7841-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="d7841-132">Er worden op dit moment alleen SemVer v 1.0.0-Prerelease-teken reeksen ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d7841-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="d7841-133">De teken reeks voor Prerelease **mag geen** punt of + [. +] bevatten, die zijn toegestaan in SemVer 2,0.</span><span class="sxs-lookup"><span data-stu-id="d7841-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="d7841-134">Voor beelden van ondersteunde Prerelease-teken reeksen zijn:-alpha,-alpha1,-BETA,-update20171020</span><span class="sxs-lookup"><span data-stu-id="d7841-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="d7841-135">Impact op de versie voor de sorteer volgorde en installatie mappen</span><span class="sxs-lookup"><span data-stu-id="d7841-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="d7841-136">De sorteer volgorde verandert wanneer u een prerelease-versie gebruikt. Dit is belang rijk bij het publiceren naar de PowerShell Gallery en wanneer u modules installeert met behulp van PowerShellGet-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d7841-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="d7841-137">Als de teken reeks voor Prerelease is opgegeven voor twee modules, is de sorteer volgorde gebaseerd op het teken reeks gedeelte na het afbreek streepje.</span><span class="sxs-lookup"><span data-stu-id="d7841-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="d7841-138">Versie 2.5.0-alpha is dus kleiner dan 2.5.0-Beta, wat kleiner is dan 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="d7841-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="d7841-139">Als twee modules dezelfde ModuleVersion hebben en slechts één de teken reeks voor de voorlopige versie heeft, wordt aangenomen dat de module zonder de voorlopige versie de productie-en de voor bereiding heeft en wordt gesorteerd als een grotere versie dan de voorlopige versie (inclusief de prerelease teken reeks).</span><span class="sxs-lookup"><span data-stu-id="d7841-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="d7841-140">Als voor beeld bij het vergelijken van Releases 2.5.0 en 2.5.0-Beta, wordt de 2.5.0-versie als een groter van beide beschouwd.</span><span class="sxs-lookup"><span data-stu-id="d7841-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="d7841-141">Wanneer u publiceert naar de PowerShell Gallery, moet de versie van de module die wordt gepubliceerd, standaard een grotere versie hebben dan een eerder gepubliceerde versie in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d7841-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="d7841-142">Voorlopige pakketten zoeken en ophalen met behulp van PowerShellGet-opdrachten</span><span class="sxs-lookup"><span data-stu-id="d7841-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="d7841-143">Voor het verwerken van pakketten die gebruikmaken van de PowerShellGet find-module, install-module, update-module en Save-module-opdrachten moet u de vlag-AllowPrerelease toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d7841-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="d7841-144">Als-AllowPrerelease is opgegeven, worden voorlopige pakketten opgenomen als deze aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="d7841-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="d7841-145">Als u de vlag-AllowPrerelease niet opgeeft, worden er geen voorlopige pakketten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7841-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="d7841-146">De enige uitzonde ringen hierop in de PowerShellGet-module opdrachten zijn Get-InstalledModule en sommige gevallen met Uninstall-module.</span><span class="sxs-lookup"><span data-stu-id="d7841-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="d7841-147">Get-InstalledModule toont altijd automatisch de voorlopige gegevens in de versie teken reeks voor modules.</span><span class="sxs-lookup"><span data-stu-id="d7841-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="d7841-148">Uninstall: als __er geen versie__ is opgegeven, wordt de meest recente versie van een module standaard verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d7841-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="d7841-149">Dat gedrag is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d7841-149">That behavior has not changed.</span></span> <span data-ttu-id="d7841-150">Als er echter een prerelease-versie is opgegeven met-RequiredVersion,-AllowPrerelease is vereist.</span><span class="sxs-lookup"><span data-stu-id="d7841-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="d7841-151">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d7841-151">Examples</span></span>

<span data-ttu-id="d7841-152">Stel dat de PowerShell Gallery TestPackage module versies 1.8.0 en 1.9.0-alpha heeft.</span><span class="sxs-lookup"><span data-stu-id="d7841-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="d7841-153">Als `-AllowPrerelease` niet wordt opgegeven, wordt alleen versie 1.8.0 geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d7841-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

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

<span data-ttu-id="d7841-154">Als u een prerelease wilt installeren, moet u altijd-AllowPrerelease opgeven.</span><span class="sxs-lookup"><span data-stu-id="d7841-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="d7841-155">Het opgeven van een teken reeks voor de voorlopige versie is niet voldoende.</span><span class="sxs-lookup"><span data-stu-id="d7841-155">Specifying a prerelease version string is not sufficient.</span></span>

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

<span data-ttu-id="d7841-156">De vorige opdracht is mislukt omdat-AllowPrerelease niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d7841-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="d7841-157">Toevoegen `-AllowPrerelease` resulteert in geslaagde pogingen.</span><span class="sxs-lookup"><span data-stu-id="d7841-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="d7841-158">Gelijktijdige installatie van versies van een module die alleen verschillen als gevolg van de opgegeven Prerelease, wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d7841-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="d7841-159">Wanneer u een module installeert met behulp van PowerShellGet, worden verschillende versies van dezelfde module naast elkaar geïnstalleerd door de naam van een map te maken met behulp van de ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="d7841-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="d7841-160">De ModuleVersion, zonder de voorlopige release teken reeks, wordt gebruikt voor de mapnaam.</span><span class="sxs-lookup"><span data-stu-id="d7841-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="d7841-161">Als een gebruiker MyModule-versie 2.5.0-alpha installeert, wordt deze in de `MyModule\2.5.0` map geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d7841-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="d7841-162">Als de gebruiker vervolgens 2.5.0-beta installeert, wordt de inhoud van de `MyModule\2.5.0`map **overschreven** door de versie van de 2.5.0-Beta.</span><span class="sxs-lookup"><span data-stu-id="d7841-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="d7841-163">Een voor deel van deze benadering is dat het niet nodig is om de installatie van de voorlopige versie ongedaan te maken na installatie van de productie-gereede versie.</span><span class="sxs-lookup"><span data-stu-id="d7841-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="d7841-164">In het voor beeld hieronder ziet u wat u kunt verwachten:</span><span class="sxs-lookup"><span data-stu-id="d7841-164">The example below shows what to expect:</span></span>

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

<span data-ttu-id="d7841-165">Uninstall-module verwijdert de meest recente versie van een module als-RequiredVersion niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d7841-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="d7841-166">Als-RequiredVersion is opgegeven en een prerelease is, moet-AllowPrerelease worden toegevoegd aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d7841-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="d7841-167">Meer Details</span><span class="sxs-lookup"><span data-stu-id="d7841-167">More details</span></span>

- [<span data-ttu-id="d7841-168">Voorlopige script versies</span><span class="sxs-lookup"><span data-stu-id="d7841-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="d7841-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="d7841-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="d7841-170">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="d7841-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="d7841-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="d7841-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="d7841-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="d7841-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="d7841-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="d7841-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="d7841-174">UnInstall-module</span><span class="sxs-lookup"><span data-stu-id="d7841-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
