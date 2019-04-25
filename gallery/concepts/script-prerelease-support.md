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
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="ae08c-103">Voorlopige versies van scripts</span><span class="sxs-lookup"><span data-stu-id="ae08c-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="ae08c-104">Vanaf versie 1.6.0, bieden powershellget hebt en de PowerShell Gallery ondersteuning voor het labelen van versies die groter zijn dan 1.0.0 als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="ae08c-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="ae08c-105">Voorlopige pakketten zijn voordat u deze functie beperkt tot het met een versie die begint met 0.</span><span class="sxs-lookup"><span data-stu-id="ae08c-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="ae08c-106">Het doel van deze functies is te bieden meer ondersteuning voor [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versiebeheer Verdrag zonder dat belangrijke achterwaartse compatibiliteit met PowerShell 3 en hoger of bestaande versie van PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="ae08c-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="ae08c-107">In dit onderwerp richt zich op de script-specifieke functies.</span><span class="sxs-lookup"><span data-stu-id="ae08c-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="ae08c-108">De equivalente functies voor modules die zich in de [voorlopige versie moduleversies](module-prerelease-support.md) onderwerp.</span><span class="sxs-lookup"><span data-stu-id="ae08c-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="ae08c-109">Met behulp van deze functies, kunnen uitgevers een script op als versie 2.5.0-alpha identificeren en later een versie gereed is voor productie 2.5.0 die de prerelease versie vervangt.</span><span class="sxs-lookup"><span data-stu-id="ae08c-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="ae08c-110">Op hoog niveau, de prerelease-script-functies zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="ae08c-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="ae08c-111">Een PrereleaseString achtervoegsel toevoegen aan de tekenreeks in het manifest van het script.</span><span class="sxs-lookup"><span data-stu-id="ae08c-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="ae08c-112">Wanneer de scripts is gepubliceerd naar de PowerShell Gallery, is deze gegevens opgehaald uit het manifest en gebruikt voor het identificeren van prerelease-pakketten.</span><span class="sxs-lookup"><span data-stu-id="ae08c-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="ae08c-113">Verkrijgen van prerelease pakketten vereist - AllowPrerelease vlag toe te voegen aan de PowerShellGet-opdrachten Find-Script Install-Script, Update-Script en Save-Script.</span><span class="sxs-lookup"><span data-stu-id="ae08c-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="ae08c-114">Als de vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ae08c-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="ae08c-115">Script-versies weergegeven door Find-Script Get-InstalledScript, en in de PowerShell Gallery weergegeven met de PrereleaseString, zoals in 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="ae08c-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="ae08c-116">Details voor de functies zijn hieronder vermeld.</span><span class="sxs-lookup"><span data-stu-id="ae08c-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="ae08c-117">De versie van een script te identificeren als een voorlopige versie</span><span class="sxs-lookup"><span data-stu-id="ae08c-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="ae08c-118">PowerShellGet-ondersteuning voor voorlopige versies is geweest voor scripts modules.</span><span class="sxs-lookup"><span data-stu-id="ae08c-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="ae08c-119">Script versiebeheer wordt alleen ondersteund door PowerShellGet, dus er geen compatibiliteitsproblemen veroorzaakt zijn door het toevoegen van de voorlopige tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="ae08c-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="ae08c-120">Voor het identificeren van een script in de PowerShell Gallery als een voorlopige versie, moet u een prerelease achtervoegsel toegevoegd aan een goed ingedeelde versietekenreeks in de scriptmetagegevens.</span><span class="sxs-lookup"><span data-stu-id="ae08c-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="ae08c-121">Een voorbeeld van een manifest script met een prerelease-versie in deze sectie eruit als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="ae08c-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="ae08c-122">De tekenreeks moet voldoen aan de volgende vereisten voor het gebruik van een prerelease-achtervoegsel:</span><span class="sxs-lookup"><span data-stu-id="ae08c-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="ae08c-123">Een prerelease-achtervoegsel kan alleen worden opgegeven als de versie 3 segmenten voor Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="ae08c-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="ae08c-124">Deze correspondeert met SemVer versie 1.0.0 gebruikt</span><span class="sxs-lookup"><span data-stu-id="ae08c-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="ae08c-125">De prerelease-achtervoegsel is een tekenreeks die begint met een afbreekstreepje en mag de ASCII-letters [0-9 bis-Za - z-]</span><span class="sxs-lookup"><span data-stu-id="ae08c-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="ae08c-126">Alleen SemVer v1.0.0 prerelease tekenreeksen worden ondersteund op dit moment is het achtervoegsel van de voorlopige **moet niet** beide punt bevatten of + [. +], die zijn toegestaan in SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="ae08c-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="ae08c-127">Voorbeelden van ondersteunde PrereleaseString tekenreeksen zijn:-alpha, a1,-bèta, -update20171020</span><span class="sxs-lookup"><span data-stu-id="ae08c-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="ae08c-128">Voorlopige versies gevolgen voor sorteren en de installatie-mappen</span><span class="sxs-lookup"><span data-stu-id="ae08c-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="ae08c-129">Sorteervolgorde wordt gewijzigd wanneer u een prerelease-versie, dit belangrijk is bij het publiceren naar de PowerShell Gallery, en bij het installeren van scripts met PowerShellGet-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="ae08c-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="ae08c-130">Als twee versies met het versienummer scripts bestaat, de sorteervolgorde is op basis van de tekenreeks deel afbreekstreepjes te volgen.</span><span class="sxs-lookup"><span data-stu-id="ae08c-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="ae08c-131">Dus, versie 2.5.0-alpha is kleiner dan 2.5.0-beta, die kleiner is dan 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="ae08c-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="ae08c-132">Als twee scripts de dezelfde versienummer hebben en slechts één een PrereleaseString, het script heeft **zonder** de prerelease-achtervoegsel wordt ervan uitgegaan dat de versie gereed is voor productie en als een hogere versie dan de voorlopige versie worden gesorteerd Versie.</span><span class="sxs-lookup"><span data-stu-id="ae08c-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="ae08c-133">Een voorbeeld: bij het vergelijken van releases 2.5.0 en 2.5.0-beta, de 2.5.0 versie wordt beschouwd als de hoogste waarde van de twee.</span><span class="sxs-lookup"><span data-stu-id="ae08c-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="ae08c-134">Bij het publiceren naar de PowerShell Gallery, moet de versie van het script wordt gepubliceerd hebben standaard een hogere versie dan alle eerder gepubliceerde versie die in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="ae08c-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="ae08c-135">Een uitgever kan versie 2.5.0-alpha bijwerken met 2.5.0-beta of 2.5.0 (met geen voorvoegsel prerelease).</span><span class="sxs-lookup"><span data-stu-id="ae08c-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="ae08c-136">Zoeken en ophalen van prerelease pakketten met PowerShellGet-opdrachten</span><span class="sxs-lookup"><span data-stu-id="ae08c-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="ae08c-137">Omgaan met prerelease pakketten met PowerShellGet Find-Script, installatiescript, Update-Script, en Save-Script-opdrachten moet de vlag - AllowPrerelease toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="ae08c-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="ae08c-138">Als - AllowPrerelease is opgegeven, wordt deze prerelease-pakketten worden opgenomen als deze aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="ae08c-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="ae08c-139">Als AllowPrerelease - vlag niet opgegeven is, wordt deze pakketten niet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ae08c-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="ae08c-140">De enige uitzonderingen op deze in de PowerShellGet-script-opdrachten zijn Get-InstalledScript en soms met Uninstall-Script.</span><span class="sxs-lookup"><span data-stu-id="ae08c-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="ae08c-141">Get-InstalledScript weergegeven altijd automatisch de prerelease-informatie in de tekenreeks als deze aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="ae08c-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="ae08c-142">Uninstall-Script wordt standaard verwijderen van de meest recente versie van een script als **geen versie** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ae08c-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="ae08c-143">Dit gedrag is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="ae08c-143">That behavior has not changed.</span></span> <span data-ttu-id="ae08c-144">Echter, als een prerelease-versie is opgegeven met behulp van `-RequiredVersion`, `-AllowPrerelease` is vereist.</span><span class="sxs-lookup"><span data-stu-id="ae08c-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="ae08c-145">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="ae08c-145">Examples</span></span>

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

<span data-ttu-id="ae08c-146">Uninstall-Script wordt de huidige versie van een script verwijderen wanneer - RequiredVersion is niet opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ae08c-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="ae08c-147">Als - RequiredVersion is opgegeven, en een voorlopige versie is, moet - AllowPrerelease worden toegevoegd aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="ae08c-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="ae08c-148">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="ae08c-148">More details</span></span>

- [<span data-ttu-id="ae08c-149">Voor voorlopige moduleversies</span><span class="sxs-lookup"><span data-stu-id="ae08c-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="ae08c-150">Find-script</span><span class="sxs-lookup"><span data-stu-id="ae08c-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="ae08c-151">Script voor installatie</span><span class="sxs-lookup"><span data-stu-id="ae08c-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="ae08c-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="ae08c-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="ae08c-153">Update-script</span><span class="sxs-lookup"><span data-stu-id="ae08c-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="ae08c-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="ae08c-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="ae08c-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="ae08c-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
