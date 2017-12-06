---
ms.date: 2017-09-26
contributor: keithb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: PrereleaseModule
ms.openlocfilehash: d2c629d0e0ec0d4a4adafe5994a37d3985d13a06
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2017
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="3e4fc-103">Prerelease-moduleversies</span><span class="sxs-lookup"><span data-stu-id="3e4fc-103">Prerelease Module Versions</span></span>
<span data-ttu-id="3e4fc-104">Vanaf versie 1.6.0 bieden PowerShellGet en de PowerShell-galerie ondersteuning voor versies die groter zijn dan 1.0.0 als een prerelease-tagging.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="3e4fc-105">Voorafgaand aan deze functie zijn prerelease-items beperkt tot een versie die begint met 0 hebben.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="3e4fc-106">Het doel van deze functies is het bieden meer ondersteuning voor [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning aanroepconventie zonder te verbreken achterwaartse compatibiliteit met PowerShell versies 3 en hoger of bestaande versies van PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="3e4fc-107">Dit onderwerp richt zich op de module-specifieke functies.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="3e4fc-108">De equivalente functies voor scripts zijn in de [Prerelease-versies van Scripts](../script/PrereleaseScript.md) onderwerp.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](../script/PrereleaseScript.md) topic.</span></span> <span data-ttu-id="3e4fc-109">Deze functies gebruikt, kunnen uitgevers identificeren module of script als versie 2.5.0-alpha en later een versie gereed is voor productie 2.5.0 die de prerelease versie vervangt.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span> 

<span data-ttu-id="3e4fc-110">Op een hoog niveau: de prerelease modulefuncties</span><span class="sxs-lookup"><span data-stu-id="3e4fc-110">At a high level, the prerelease module features include:</span></span>

* <span data-ttu-id="3e4fc-111">Een Prerelease-reeks toevoegen aan de sectie PSData van de module-manifest verwijst naar de module als een prerelease-versie.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="3e4fc-112">Wanneer de module wordt gepubliceerd naar de PowerShell-galerie, is deze gegevens opgehaald uit het manifest en gebruikt om deze items te identificeren.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
* <span data-ttu-id="3e4fc-113">Ophalen van een prerelease-items vereist - AllowPrerelease vlag toe te voegen aan de PowerShellGet opdrachten Find-Module installeren-Module, Update-Module en opslaan-Module.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span> <span data-ttu-id="3e4fc-114">Als de vlag niet is opgegeven, wordt deze items niet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-114">If the flag is not specified, prerelease items will not be shown.</span></span>  
* <span data-ttu-id="3e4fc-115">Moduleversies weergegeven door Find-Module, Get-InstalledModule en in de galerie met PowerShell wordt weergegeven als één tekenreeks met de Prerelease tekenreeks toegevoegd, zoals in 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span> 

<span data-ttu-id="3e4fc-116">Hieronder vindt u details voor de functies.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-116">Details for the features are included below.</span></span> 

<span data-ttu-id="3e4fc-117">Deze wijzigingen hebben geen invloed op de ondersteuning van de module-versie die is ingebouwd in PowerShell en compatibel zijn met PowerShell 3.0 en 4.0 5.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span> 

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="3e4fc-118">Een moduleversie identificeren als een voorlopige versie</span><span class="sxs-lookup"><span data-stu-id="3e4fc-118">Identifying a module version as a prerelease</span></span> 

<span data-ttu-id="3e4fc-119">Ondersteuning voor voorlopige versies PowerShellGet vereist het gebruik van twee velden in de Module-Manifest:</span><span class="sxs-lookup"><span data-stu-id="3e4fc-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

* <span data-ttu-id="3e4fc-120">De ModuleVersion opgenomen in het manifest van de module moet een versie 3-onderdeel als een prerelease-versie wordt gebruikt en aan de bestaande PowerShell versiebeheer voldoen moet.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="3e4fc-121">De indeling van versie zou A.B.C, waarbij A, B en C alle gehele getallen zijn zijn.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span> 
* <span data-ttu-id="3e4fc-122">De Prerelease tekenreeks is opgegeven in het manifest module in de sectie PSData van PrivateData.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span> <span data-ttu-id="3e4fc-123">Gedetailleerde vereisten voor de Prerelease tekenreeks zijn hieronder.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-123">Detailed requirements on the Prerelease string are below.</span></span> 

<span data-ttu-id="3e4fc-124">Een voorbeeld van een module-manifest dat definieert een module als een voorlopige versie in deze sectie eruit als het volgende:</span><span class="sxs-lookup"><span data-stu-id="3e4fc-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>
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

<span data-ttu-id="3e4fc-125">De gedetailleerde vereisten voor voorlopige tekenreeks zijn:</span><span class="sxs-lookup"><span data-stu-id="3e4fc-125">The detailed requirements for Prerelease string are:</span></span> 

* <span data-ttu-id="3e4fc-126">Deze tekenreeks kan alleen worden opgegeven wanneer de ModuleVersion 3 segmenten voor Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="3e4fc-127">Dit wordt uitgelijnd met SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-127">This aligns with SemVer v1.0.0.</span></span>
* <span data-ttu-id="3e4fc-128">Een afbreekstreepje is het scheidingsteken tussen het Build-nummer en de Prerelease tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="3e4fc-129">Een afbreekstreepje kan worden opgenomen in de Prerelease tekenreeks als het eerste teken alleen.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
* <span data-ttu-id="3e4fc-130">De Prerelease tekenreeks mag alleen ASCII-letters en cijfers bevatten [0-9A-Za - z-].</span><span class="sxs-lookup"><span data-stu-id="3e4fc-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="3e4fc-131">Het is een best practice om te beginnen met de voorlopige versie tekenreeks met een alfanumerieke tekens, omdat deze gemakkelijker te identificeren dat dit een prerelease-versie is bij het scannen van een lijst met items.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span> 
* <span data-ttu-id="3e4fc-132">Alleen SemVer v1.0.0 prerelease tekenreeksen worden ondersteund op dit moment.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="3e4fc-133">Prerelease tekenreeks __moet niet__ beide punt bevatten of + [. +], die zijn toegestaan in SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span> 
* <span data-ttu-id="3e4fc-134">Voorbeelden van ondersteunde Prerelease tekenreeks zijn:-alpha, -a1,-bèta, -update20171020</span><span class="sxs-lookup"><span data-stu-id="3e4fc-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="3e4fc-135">__Voorlopige versies gevolgen voor de mappen en de installatie sorteren__</span><span class="sxs-lookup"><span data-stu-id="3e4fc-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="3e4fc-136">Sorteervolgorde verandert wanneer u een prerelease-versie, wat belangrijk bij het publiceren van de PowerShell-galerie, en modules met behulp van PowerShellGet opdrachten installeren.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="3e4fc-137">Als de Prerelease tekenreeks is opgegeven voor twee modules, wordt de sorteervolgorde is gebaseerd op het volgende op het afbreekstreepje tekenreeksdeel.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="3e4fc-138">Dus is versie 2.5.0-alpha kleiner dan 2.5.0-beta, dat is minder dan 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="3e4fc-139">Als twee modules de dezelfde ModuleVersion hebben en slechts één een Prerelease tekenreeks heeft, de module zonder de Prerelease tekenreeks wordt ervan uitgegaan dat de versie gereed is voor productie en worden gesorteerd als een hogere versie dan de prerelease versie (waaronder de voorlopige versie tekenreeks).</span><span class="sxs-lookup"><span data-stu-id="3e4fc-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="3e4fc-140">Als u bijvoorbeeld bij het vergelijken van releases 2.5.0 en 2.5.0-beta, de 2.5.0 versie wordt beschouwd als de grootste van de twee.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span> 

<span data-ttu-id="3e4fc-141">Bij het publiceren van de PowerShell-galerie, moet de versie van de module wordt gepubliceerd hebben standaard een hogere versie dan eventuele eerder gepubliceerde versie die in de PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> 

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="3e4fc-142">Zoeken en ophalen van een prerelease-items met PowerShellGet opdrachten</span><span class="sxs-lookup"><span data-stu-id="3e4fc-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="3e4fc-143">Omgaan met prerelease items met PowerShellGet Find-Module, installatie-Module, Update-Module, en de opdrachten opslaan-Module vereist de vlag - AllowPrerelease toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="3e4fc-144">Als - AllowPrerelease is opgegeven, wordt deze prerelease-items worden opgenomen als deze aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span>
<span data-ttu-id="3e4fc-145">Als de vlag - AllowPrerelease niet is opgegeven, wordt deze items niet weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span> 

<span data-ttu-id="3e4fc-146">De enige uitzonderingen op dit in de module PowerShellGet opdrachten zijn Get-InstalledModule en in sommige gevallen met Uninstall-Module.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span> 

* <span data-ttu-id="3e4fc-147">Get-InstalledModule weergegeven altijd automatisch de prerelease-informatie in de tekenreeks voor modules.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span> 
* <span data-ttu-id="3e4fc-148">Verwijderen van de Module standaard verwijdert de meest recente versie van een module als __geen versie__ is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="3e4fc-149">Dit gedrag is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-149">That behavior has not changed.</span></span> <span data-ttu-id="3e4fc-150">Echter, als een prerelease-versie wordt opgegeven met - RequiredVersion, - AllowPrerelease is vereist.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span> 

## <a name="examples"></a><span data-ttu-id="3e4fc-151">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="3e4fc-151">Examples</span></span>
```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
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

<span data-ttu-id="3e4fc-152">Side-by-side-installatie van versies van een module die alleen als gevolg van de voorlopige versie opgegeven verschillen, wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="3e4fc-153">Als u een module met behulp van PowerShellGet installeert, zijn verschillende versies van dezelfde module geïnstalleerde side-by-side door het maken van de naam van een map met de ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="3e4fc-154">De ModuleVersion, zonder de prerelease tekenreeks wordt gebruikt voor naam van de map.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="3e4fc-155">Als een gebruiker MyModule versie 2.5.0-alpha installeert, wordt deze naar de map MyModule\2.5.0 worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span> <span data-ttu-id="3e4fc-156">Als de gebruiker vervolgens 2.5.0-beta installeert, de versie 2.5.0-beta wordt __te veel schrijven__ de inhoud van de map MyModule\2.5.0.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span> <span data-ttu-id="3e4fc-157">Een voordeel hiervan is dat er hoeft te verwijderen de prerelease versie na de installatie van de versie gereed is voor productie.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="3e4fc-158">Het volgende voorbeeld ziet u wat ze kunnen verwachten:</span><span class="sxs-lookup"><span data-stu-id="3e4fc-158">The example below shows what to expect:</span></span>


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

<span data-ttu-id="3e4fc-159">Verwijderen-Module kan de meest recente versie van een module wordt verwijderd wanneer - RequiredVersion wordt niet meegeleverd.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span> <span data-ttu-id="3e4fc-160">-RequiredVersion is opgegeven, en een voorlopige versie, moet - AllowPrerelease worden toegevoegd aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3e4fc-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span> 

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



## <a name="more-details"></a><span data-ttu-id="3e4fc-161">meer informatie</span><span class="sxs-lookup"><span data-stu-id="3e4fc-161">More details</span></span>
### <a name="prerelease-script-versionsscriptprereleasescriptmd"></a>[<span data-ttu-id="3e4fc-162">Script prerelease-versies</span><span class="sxs-lookup"><span data-stu-id="3e4fc-162">Prerelease Script Versions</span></span>](../script/PrereleaseScript.md)
### <a name="find-modulepsgetfind-modulemd"></a>[<span data-ttu-id="3e4fc-163">Zoek-Module</span><span class="sxs-lookup"><span data-stu-id="3e4fc-163">Find-Module</span></span>](./psget_find-module.md)
### <a name="install-modulepsgetinstall-modulemd"></a>[<span data-ttu-id="3e4fc-164">Installatie-Module</span><span class="sxs-lookup"><span data-stu-id="3e4fc-164">Install-Module</span></span>](./psget_install-module.md)
### <a name="save-modulepsgetsave-modulemd"></a>[<span data-ttu-id="3e4fc-165">Opslaan-Module</span><span class="sxs-lookup"><span data-stu-id="3e4fc-165">Save-Module</span></span>](./psget_save-module.md)
### <a name="update-modulepsgetupdate-modulemd"></a>[<span data-ttu-id="3e4fc-166">Update-Module</span><span class="sxs-lookup"><span data-stu-id="3e4fc-166">Update-Module</span></span>](./psget_update-module.md)
### <a name="get-installedmodulepsgetget-installedmodulemd"></a>[<span data-ttu-id="3e4fc-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="3e4fc-167">Get-InstalledModule</span></span>](./psget_get-installedmodule.md)
### <a name="uninstall-modulepsgetuninstall-modulemd"></a>[<span data-ttu-id="3e4fc-168">Verwijderen-Module</span><span class="sxs-lookup"><span data-stu-id="3e4fc-168">UnInstall-Module</span></span>](./psget_uninstall-module.md)
