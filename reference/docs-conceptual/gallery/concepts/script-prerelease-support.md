---
ms.date: 10/17/2017
contributor: keithb
keywords: Galerie, Power shell, cmdlet, psget
title: Voorlopige versies van scripts
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71329174"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="c7d48-103">Voorlopige versies van scripts</span><span class="sxs-lookup"><span data-stu-id="c7d48-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="c7d48-104">Vanaf versie 1.6.0, PowerShellGet en de PowerShell Gallery bieden ondersteuning voor coderings versies die groter zijn dan 1.0.0 als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="c7d48-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="c7d48-105">Vóór deze functie werden voorlopige pakketten beperkt tot een versie die begint met 0.</span><span class="sxs-lookup"><span data-stu-id="c7d48-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="c7d48-106">Het doel van deze functies is om meer ondersteuning te bieden voor [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) versie beheer, zonder achterwaartse compatibiliteit te verbreken met Power shell-versies 3 en hoger, of bestaande versies van PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="c7d48-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="c7d48-107">Dit onderwerp richt zich op de script-specifieke functies.</span><span class="sxs-lookup"><span data-stu-id="c7d48-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="c7d48-108">De equivalente functies voor modules vindt u in het onderwerp versies van de [module Prerelease](module-prerelease-support.md) .</span><span class="sxs-lookup"><span data-stu-id="c7d48-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="c7d48-109">Met behulp van deze functies kunnen uitgevers een script identificeren als versie 2.5.0-alpha en later een productie versie-2.5.0 vrijgeven die de voorlopige versie vervangt.</span><span class="sxs-lookup"><span data-stu-id="c7d48-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="c7d48-110">Op hoog niveau zijn de functies van het voorlopige script:</span><span class="sxs-lookup"><span data-stu-id="c7d48-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="c7d48-111">Een PrereleaseString-achtervoegsel toevoegen aan de versie teken reeks in het script manifest.</span><span class="sxs-lookup"><span data-stu-id="c7d48-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="c7d48-112">Wanneer de scripts worden gepubliceerd op de PowerShell Gallery, worden deze gegevens geëxtraheerd uit het manifest en gebruikt om voorlopige pakketten te identificeren.</span><span class="sxs-lookup"><span data-stu-id="c7d48-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="c7d48-113">Voor het verkrijgen van voorlopige pakketten moet u de vlag AllowPrerelease toevoegen aan de PowerShellGet-opdrachten Zoek-script, install-script, update script en Save-script.</span><span class="sxs-lookup"><span data-stu-id="c7d48-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="c7d48-114">Als de vlag niet is opgegeven, worden er geen voorlopige pakketten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7d48-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="c7d48-115">Script versies die worden weer gegeven door Find-script, Get-InstalledScript en in de PowerShell Gallery worden weer gegeven met de PrereleaseString, zoals in 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="c7d48-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="c7d48-116">Hieronder vindt u meer informatie over de functies.</span><span class="sxs-lookup"><span data-stu-id="c7d48-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="c7d48-117">Een script versie als een voorlopige versie identificeren</span><span class="sxs-lookup"><span data-stu-id="c7d48-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="c7d48-118">PowerShellGet-ondersteuning voor voorlopige versies is gemakkelijker voor scripts dan modules.</span><span class="sxs-lookup"><span data-stu-id="c7d48-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="c7d48-119">Script versie beheer wordt alleen ondersteund door PowerShellGet, waardoor er geen compatibiliteits problemen zijn veroorzaakt door het toevoegen van de teken reeks voor de voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="c7d48-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="c7d48-120">Als u een script in de PowerShell Gallery als Prerelease wilt identificeren, voegt u een prerelease-achtervoegsel toe aan een correct opgemaakte versie teken reeks in de meta gegevens van het script.</span><span class="sxs-lookup"><span data-stu-id="c7d48-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="c7d48-121">Een voorbeeld sectie van een script manifest met een voorlopige versie ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="c7d48-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="c7d48-122">Als u een prerelease-achtervoegsel wilt gebruiken, moet de versie teken reeks voldoen aan de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="c7d48-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="c7d48-123">Een prerelease-achtervoegsel mag alleen worden opgegeven als de versie 3 segmenten is voor Major. minor. build.</span><span class="sxs-lookup"><span data-stu-id="c7d48-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="c7d48-124">Dit wordt uitgelijnd met SemVer v 1.0.0</span><span class="sxs-lookup"><span data-stu-id="c7d48-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="c7d48-125">Het voor voegsel van de prerelease is een teken reeks die begint met een afbreek streepje en ASCII-alfanumerieke tekens kan bevatten [0-9 bis-Za-z-]</span><span class="sxs-lookup"><span data-stu-id="c7d48-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="c7d48-126">Er worden op dit moment alleen SemVer v 1.0.0-Prerelease-teken reeksen ondersteund, dus het achtervoegsel van de prerelease **mag geen** punt of + [. +] bevatten, dat is toegestaan in SemVer 2,0</span><span class="sxs-lookup"><span data-stu-id="c7d48-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="c7d48-127">Voor beelden van ondersteunde PrereleaseString-teken reeksen zijn:-alpha,-alpha1,-BETA,-update20171020</span><span class="sxs-lookup"><span data-stu-id="c7d48-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="c7d48-128">Impact op de versie voor de sorteer volgorde en installatie mappen</span><span class="sxs-lookup"><span data-stu-id="c7d48-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="c7d48-129">Wijzigingen in de sorteer volgorde worden gesorteerd wanneer u een prerelease-versie gebruikt. Dit is belang rijk wanneer u naar de PowerShell Gallery publiceert en wanneer u scripts installeert met behulp van PowerShellGet-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="c7d48-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="c7d48-130">Als er twee script versies met het versie nummer bestaan, is de sorteer volgorde gebaseerd op het teken reeks gedeelte na het afbreek streepje.</span><span class="sxs-lookup"><span data-stu-id="c7d48-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="c7d48-131">Versie 2.5.0-alpha is dus kleiner dan 2.5.0-Beta, wat kleiner is dan 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="c7d48-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="c7d48-132">Als twee scripts hetzelfde versie nummer hebben en er slechts één een PrereleaseString heeft, wordt aangenomen dat het script **zonder** het Prerelease-achtervoegsel de productie-gereede versie is en wordt deze als een grotere versie gesorteerd dan de voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="c7d48-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="c7d48-133">Als voor beeld bij het vergelijken van Releases 2.5.0 en 2.5.0-Beta, wordt de 2.5.0-versie als een groter van beide beschouwd.</span><span class="sxs-lookup"><span data-stu-id="c7d48-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="c7d48-134">Wanneer u publiceert naar de PowerShell Gallery, moet de versie van het script dat wordt gepubliceerd, standaard een grotere versie hebben dan een eerder gepubliceerde versie in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c7d48-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="c7d48-135">Een uitgever kan versie 2.5.0-alpha met 2.5.0-Beta of met 2.5.0 (zonder Prerelease-achtervoegsel) bijwerken.</span><span class="sxs-lookup"><span data-stu-id="c7d48-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="c7d48-136">Voorlopige pakketten zoeken en ophalen met behulp van PowerShellGet-opdrachten</span><span class="sxs-lookup"><span data-stu-id="c7d48-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="c7d48-137">Voor het verwerken van prerelease-pakketten met behulp van PowerShellGet zoeken-script, install-script, update-script en Save-script opdrachten moet u de vlag-AllowPrerelease toevoegen.</span><span class="sxs-lookup"><span data-stu-id="c7d48-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="c7d48-138">Als-AllowPrerelease is opgegeven, worden voorlopige pakketten opgenomen als deze aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="c7d48-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="c7d48-139">Als u de vlag-AllowPrerelease niet opgeeft, worden er geen voorlopige pakketten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7d48-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="c7d48-140">De enige uitzonde ringen hierop in de PowerShellGet-script opdrachten zijn Get-InstalledScript en sommige gevallen met uninstall-script.</span><span class="sxs-lookup"><span data-stu-id="c7d48-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="c7d48-141">Get-InstalledScript toont altijd automatisch de voorlopige gegevens in de versie teken reeks als deze aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="c7d48-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="c7d48-142">Uninstall-script wordt standaard de meest recente versie van een script verwijderd als **er geen versie** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c7d48-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="c7d48-143">Dat gedrag is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c7d48-143">That behavior has not changed.</span></span> <span data-ttu-id="c7d48-144">Als er echter een prerelease-versie is opgegeven met behulp van `-RequiredVersion`, is `-AllowPrerelease` vereist.</span><span class="sxs-lookup"><span data-stu-id="c7d48-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="c7d48-145">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="c7d48-145">Examples</span></span>

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

<span data-ttu-id="c7d48-146">Uninstall-script verwijdert de huidige versie van een script wanneer-RequiredVersion niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c7d48-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="c7d48-147">Als-RequiredVersion is opgegeven en een prerelease is, moet-AllowPrerelease worden toegevoegd aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c7d48-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="c7d48-148">Meer details</span><span class="sxs-lookup"><span data-stu-id="c7d48-148">More details</span></span>

- [<span data-ttu-id="c7d48-149">Versies van de module Prerelease</span><span class="sxs-lookup"><span data-stu-id="c7d48-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="c7d48-150">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="c7d48-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="c7d48-151">Install-script</span><span class="sxs-lookup"><span data-stu-id="c7d48-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="c7d48-152">Opslaan-script</span><span class="sxs-lookup"><span data-stu-id="c7d48-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="c7d48-153">Update-script</span><span class="sxs-lookup"><span data-stu-id="c7d48-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="c7d48-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="c7d48-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="c7d48-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="c7d48-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
