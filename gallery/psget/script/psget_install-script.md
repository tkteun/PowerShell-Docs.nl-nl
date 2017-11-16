---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Script voor installatie
ms.openlocfilehash: 4c3fd9393ccb7ee5c3b010f1114b6596a74fdee2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="install-script"></a><span data-ttu-id="d9bc6-103">Script voor installatie</span><span class="sxs-lookup"><span data-stu-id="d9bc6-103">Install-Script</span></span>

<span data-ttu-id="d9bc6-104">Installeert de PowerShell-script-bestanden van online opslagplaatsen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-104">Installs the PowerShell script files from online repositories to the local computer.</span></span>


## <a name="description"></a><span data-ttu-id="d9bc6-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d9bc6-105">Description</span></span>

<span data-ttu-id="d9bc6-106">De cmdlet Install-Script verkrijgt de nettolading van een script van een opslagplaats, wordt gecontroleerd of de nettolading een geldig PowerShell-script is en het scriptbestand naar een opgegeven installatielocatie kopieert.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-106">The Install-Script cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="d9bc6-107">De standaard-opslagplaatsen die script voor installatie werkt tegen kunnen worden geconfigureerd via het Register PSRepository, Set PSRepository, Unregister-PSRepository en Get-PSRepository-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-107">The default repositories Install-Script operates against are configurable through the Register-PSRepository, Set-PSRepository, Unregister-PSRepository, and Get-PSRepository cmdlets.</span></span> <span data-ttu-id="d9bc6-108">Als het wordt uitgevoerd tegen meerdere opslagplaatsen, wordt het eerste script die overeenkomt met de opgegeven zoekcriteria (naam, MinimumVersion of MaximumVersion) uit de opslagplaats eerste zonder fouten in Script voor installatie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-108">When operating against multiple repositories, Install-Script installs the first script that matches the specified search criteria (Name, MinimumVersion, or MaximumVersion) from the first repository without any error.</span></span>


<span data-ttu-id="d9bc6-109">Script voor installatie cmdlet downloadt van een of meer modules van een online galerie, valideert en installeert ze op de lokale computer aan het bereik van de gespecificeerde installatie.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-109">Install-Script cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="d9bc6-110">De cmdlet Install-Script een of meer modules die voldoen aan opgegeven criteria vanuit een online-galerie ontvangt, controleert of de zoekresultaten zijn geldige modules en kopieën module mappen naar de installatielocatie.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-110">The Install-Script cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="d9bc6-111">Als er geen bereik is gedefinieerd, of wanneer de waarde van de bereikparameter AllUsers is, wordt de module naar %systemdrive%:\Program Files\WindowsPowerShell\Modules geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-111">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="d9bc6-112">Wanneer de waarde van bereik CurrentUser is, wordt de module geïnstalleerd in $home\Documents\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-112">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="d9bc6-113">U kunt uw resultaten op basis van de minimale en de exacte versie van de opgegeven modules filteren.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-113">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="d9bc6-114">Er is geen Side-by-side-Versieondersteuning voor bestanden met PowerShell-Script</span><span class="sxs-lookup"><span data-stu-id="d9bc6-114">No Side-by-side version support for PowerShell Script files</span></span>
- <span data-ttu-id="d9bc6-115">Ondersteuning voor de installatie van script afhankelijkheid</span><span class="sxs-lookup"><span data-stu-id="d9bc6-115">Script dependency installation support</span></span>
- <span data-ttu-id="d9bc6-116">**Niet-vertrouwde prompt:** acceptatie van de gebruiker is vereist voor het installeren van de modules van een niet-vertrouwde opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-116">**Untrusted prompt:** User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="d9bc6-117">-Force opnieuw installeren van de geïnstalleerde module</span><span class="sxs-lookup"><span data-stu-id="d9bc6-117">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="d9bc6-118">RequiredVersion installeert de opgegeven versie in SxS met bestaande versies op PowerShell versie 5.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-118">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

<span data-ttu-id="d9bc6-119">Jokertekens worden niet ondersteund in - Name op installatie-Module, opslaan-Module verwijderen-Module, installatiescript, opslaan-Script en Uninstall-Script cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-119">Wildcards are not supported in -Name on Install-Module, Save-Module, Uninstall-Module, Install-Script, Save-Script, and Uninstall-Script cmdlets.</span></span>

### <a name="scope"></a><span data-ttu-id="d9bc6-120">Bereik</span><span class="sxs-lookup"><span data-stu-id="d9bc6-120">Scope</span></span>
<span data-ttu-id="d9bc6-121">Hiermee geeft u het bereik van de installatie van de module.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-121">Specifies the installation scope of the module.</span></span> <span data-ttu-id="d9bc6-122">De acceptabele waarden voor deze parameter zijn: AllUsers en CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-122">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="d9bc6-123">Het bereik van de installatie standaard is AllUsers.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-123">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="d9bc6-124">Het bereik AllUsers kunt modules worden geïnstalleerd op een locatie die toegankelijk is voor alle gebruikers van de computer, dat wil zeggen, "$env: SystemDrive\Program Files\WindowsPowerShell\Modules '.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-124">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="d9bc6-125">Het bereik CurrentUser kunt modules worden geïnstalleerd tot '$home\Documents\WindowsPowerShell\Modules', zodat de module alleen beschikbaar voor de huidige gebruiker is.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-125">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>


<span data-ttu-id="d9bc6-126">Hiermee geeft u het bereik van de installatie van het script.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-126">Specifies the installation scope of the script.</span></span> <span data-ttu-id="d9bc6-127">Geldige waarden zijn: AllUsers en CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-127">Valid values are: AllUsers and CurrentUser.</span></span> <span data-ttu-id="d9bc6-128">De standaardwaarde is CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-128">The default is CurrentUser.</span></span>

<span data-ttu-id="d9bc6-129">Het bereik AllUsers Hiermee geeft u een script om %systemdrive%:\ProgramFiles\WindowsPowerShell\Scripts te installeren, zodat het script beschikbaar voor alle gebruikers is.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-129">The AllUsers scope specifies to install a script to %systemdrive%:\ProgramFiles\WindowsPowerShell\Scripts so that the script is available to all users.</span></span> <span data-ttu-id="d9bc6-130">Het bereik CurrentUser Hiermee geeft u het script in $home\Documents\WindowsPowerShell\Scripts installeren, zodat het script alleen beschikbaar voor de huidige gebruiker is.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-130">The CurrentUser scope specifies to install the script in $home\Documents\WindowsPowerShell\Scripts so that the script is available only to the current user.</span></span>


## <a name="nopathupdate"></a><span data-ttu-id="d9bc6-131">NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="d9bc6-131">NoPathUpdate</span></span>

- <span data-ttu-id="d9bc6-132">NoPathUpdate switch parameter bij de cmdlet Install-Script omzeilt de prompt voor de locatie van het script install toe te voegen aan de omgevingsvariabele PATH.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-132">NoPathUpdate switch parameter on Install-Script cmdlet bypasses the prompt for adding the script install location to the PATH environment variable.</span></span>
- <span data-ttu-id="d9bc6-133">Gebruik van de opdracht met – NoPathUpdate opgegeven leidt ertoe dat geen vraag en het pad niet wordt bijgewerkt (force is negeerbare hier).</span><span class="sxs-lookup"><span data-stu-id="d9bc6-133">Any use of the command WITH –NoPathUpdate specified will result in no prompt and the PATH NOT being updated (force is ignorable here).</span></span>
- <span data-ttu-id="d9bc6-134">-Force zonder – NoPathUpdate leidt ertoe dat geen vraag en het pad wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-134">-Force without –NoPathUpdate will result in no prompt and the PATH will be updated.</span></span>
- <span data-ttu-id="d9bc6-135">Als noch – Force of – NoPathUpdate worden opgegeven, wordt de gebruiker de volgende prompt verschijnt.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-135">If neither –Force or –NoPathUpdate are specified, the user will see the prompt.</span></span>
- <span data-ttu-id="d9bc6-136">Dit alles is alleen van toepassing de eerste keer Script voor installatie wordt gebruikt in een bepaald bereik.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-136">All of this only applies the first time Install-Script is used in a given scope.</span></span>


## <a name="notes"></a><span data-ttu-id="d9bc6-137">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d9bc6-137">Notes</span></span>

<span data-ttu-id="d9bc6-138">Deze cmdlet wordt uitgevoerd op Windows PowerShell 3.0 of latere versies van Windows PowerShell op Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-138">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="d9bc6-139">Als een geïnstalleerde module kan niet worden geïmporteerd (dat wil zeggen, als er geen een psm1-, .psd1- of DLL-bestand met dezelfde naam in de map), mislukt de installatie tenzij u de parameter Force aan de opdracht toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-139">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="d9bc6-140">Als een versie van de module op de computer overeenkomt met de opgegeven waarde voor de parameter Name en u de parameter MinimumVersion of RequiredVersion niet hebt toegevoegd, blijft het Script voor installatie achtergrond zonder deze module te installeren.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-140">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Script silently continues without installing that module.</span></span> <span data-ttu-id="d9bc6-141">Als de MinimumVersion of RequiredVersion parameters worden opgegeven en de bestaande module komt niet overeen met de waarden in die parameter, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-141">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="d9bc6-142">Meer specifiek: als de versie van de momenteel geïnstalleerde module lager is dan de waarde van de parameter MinimumVersion of niet gelijk zijn aan de waarde van de parameter RequiredVersion is een fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-142">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="d9bc6-143">Als de versie van de geïnstalleerde module groter dan de waarde van de parameter MinimumVersion of gelijk zijn aan de waarde van de parameter RequiredVersion is, blijft het Script voor installatie achtergrond zonder deze module te installeren.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-143">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Script silently continues without installing that module.</span></span>

<span data-ttu-id="d9bc6-144">Script voor installatie, wordt er een fout geretourneerd als er geen module in de on line galerie die overeenkomt met de opgegeven naam bestaat.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-144">Install-Script returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="d9bc6-145">Geef een matrix met de modulenamen van de, gescheiden door komma's voor het installeren van meerdere modules.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-145">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="d9bc6-146">U kunt MinimumVersion of RequiredVersion niet toevoegen als u meerdere modulenamen opgeeft.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-146">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="d9bc6-147">Standaard worden modules geïnstalleerd in de map Program Files om verwarring te voorkomen dat tijdens de installatie van Windows PowerShell Desired State Configuration (DSC) resources. U kunt meerdere PSGetItemInfo objecten installatiescript; overbrengen Dit is een andere manier voor het opgeven van meerdere modules installeren in één opdracht.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-147">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Script; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="d9bc6-148">Om te voorkomen dat de actieve modules die schadelijke code, geïnstalleerd bevatten worden modules niet automatisch geïmporteerd door de installatie.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-148">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="d9bc6-149">Als een best practice, module code evalueren voordat u cmdlets of functies voor de eerste keer uitgevoerd in een module.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-149">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="d9bc6-150">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="d9bc6-150">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Install-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d9bc6-151">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="d9bc6-151">Cmdlet online help reference</span></span>

[<span data-ttu-id="d9bc6-152">Script voor installatie</span><span class="sxs-lookup"><span data-stu-id="d9bc6-152">Install-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619784)

## <a name="example-commands"></a><span data-ttu-id="d9bc6-153">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="d9bc6-153">Example commands</span></span>

```powershell


# Piping Find-Script output to Install-Script cmdlet

Find-Script -Repository Local1 -Name Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Find-Script -Repository Local1 -Name Required-Script2 | Install-Script

Get-Command Required-Script2

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
ExternalScript  Required-Script2.ps1                                2.0       C:\Users\manikb\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1


Get-InstalledScript Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Get-InstalledScript Required-Script2 | fl * -Force


Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\manikb\Documents\WindowsPowerShell\Scripts


# Installing a script to AllUsers scope

Install-Script -Repository Local1 -Name Required-Script3 -Scope AllUsers
Get-InstalledScript -Name Required-Script3

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Get-InstalledScript -Name Required-Script3  | fl * -Force


Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


# Installing a script with dependent scripts and modules

Find-Script -Repository Local1 -Name Script-WithDependencies2 -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Script-WithDependencies2
Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script


Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module


Find-Script -Repository Local1 -Name Required-Script*

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Required-Script*

Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


# Find a script and install it

# The first command finds the script named Required-Script2 from the Local1 repository and displays the results.
# The second command finds the Required-Script2 script, and then uses the pipeline operator to pass it to the Install-Script cmdlet to install it.
# The third command uses the Get-Command cmdlet to get Required-Script2, and then displays the results.
# The fourth command uses the Get-InstalledScript cmdlet to get Required-Script2 and display the results.
# The fifth command gets RequiredScript2 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Find-Script -Repository "Local1" -Name "Required-Script2"

Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
Get-Command -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2" | Format-List * 


# Install a script with AllUsers scope

# The first command installs the script named Required-Script3 and assigns it AllUsers scope.
# The second command gets the installed script Required-Script3 and displays information about it.
# The third command gets Required-Script3 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
Get-InstalledScript -Name "Required-Script3"
Get-InstalledScript -Name "Required-Script3" | Format-List * 


# Install a script with its dependent scripts and modules

# The first command finds the script named Script-WithDependencies2 and its dependencies in the Local1 repository and displays the results.
# The second command installs Script-WithDependencies2.
# The third command uses the Get-InstalledScript script cmdlet to get installed scripts and display the results.
# The fourth command uses the Get-InstalledModule cmdlet to get installed modules and display the results.
# The fifth command uses the Find-Script cmdlet to find scripts where the name begins with Required-Script and display the results.
# The sixth command installs the scripts where the name begins with Required-Script in the Local1 repository. 
# The final command gets installed scripts and displays the results.

Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
Get-InstalledScript
Get-InstalledModule
Find-Script -Repository "Local1" -Name "Required-Script*"
Install-Script -Repository "Local1" -Name "Required-Script*"
Get-InstalledScript

```

<span data-ttu-id="d9bc6-154">U kunt ook de Get-Command – naam <InstalledScriptFileName> downloaden.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-154">You can also use Get-Command –Name <InstalledScriptFileName> to get it.</span></span> <span data-ttu-id="d9bc6-155">Installatie op twee locaties worden toegevoegd aan de omgevingsvariabele PATH op het eerste gebruik van een opgegeven bereik.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-155">Two install locations are added to the PATH environment variable on first use of a specified scope.</span></span>
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1
```

```powershell

# Install a module by name
Install-Script -Name MyDscModule

# Install multiple modules
Install-Script ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Script -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Script -Name ContosoServer -RequiredVersion 1.1.3

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Script -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Script ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Script ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Script ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Script ContosoClient -Force

# Install a module with dependencies
Install-Script -Name 


# Install a script from the registered repository with ScriptSourceLocation
Install-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Install-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Install-Script -Name *Azure*

# Find all versions of a script
Install-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Install-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Install-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Install-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Install-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Install-Script

# Find available scripts from few registered repositories
Install-Script -Repository PSGallery, PrivatePSGallery

```

```powershell
 Added the logic for checking and failing the install script operation when there is a command with same name is already available on the system.
Also updated the prompt message.

 Examples:
PS C:\WINDOWS\system32> install-script get-childitem -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 
 
 PS C:\WINDOWS\system32> install-script get-childitem,contosos -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem,contosos -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 PackageManagement\Install-Package : No match was found for the specified search criteria and script name 'contosos'. Try Get-ScriptRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\powershellget\1.0.0.1\PSModule.psm1:2891 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : ObjectNotFound: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
     + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage

 PS C:\WINDOWS\system32>

 
 
 PS C:\WINDOWS\system32> find-script get-childitem -Repository localrepo | install-script
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:51
+ find-script get-childitem -Repository localrepo | install-script
+                                                   ~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 
 PS C:\WINDOWS\system32>

 PS C:\WINDOWS\system32> Install-Package -Name Get-ChildItem -source LocalRepo  -ProviderName powershellget -Type Script
WARNING: A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.

```

```powershell

Prompt ONCE per USER and per SCOPE for adding the script installation location to PATH environment variable.

- Prompt message for CurrentUser scope: (Complete message will be scrubbed later)

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- Prompt message for –AllUsers scope is same as above with $env:ProgramFiles\WindowsPowerShell\Scripts .

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- To prompt only once per scope, user acceptance for PATH variable change will be added to the user specific settings file under %localappdata%\Microsoft\windows\PowerShell\PowerShellGet
%localappdata%\Microsoft\windows\PowerShell\PowerShellGet\PowerShellGetSettings.XML. 
This settings file will be used to not prompt again.

After prompting for CurrentUser scope: 
    true or false for CurrentUserScope_AllowPATHChangeForScripts key based on user input.

After prompting for AllUsers scope: 
    true or false for AllUsersScope_AllowPATHChangeForScripts key based on user input.

- If user accepts the prompt
                Check and add $home\Documents\WindowsPowerShell\Scripts to user specific PATH environment variable.
                Check and add $env:ProgramFiles\WindowsPowerShell\Scripts to system specific PATH environment variable only when Install-Script cmdlet is used in an administrator process.
                Check and add above two paths to $env:PATH variable of the current process.

- If user denies the prompt, script installation will be proceeded without making any changes to the PATH environment variable.



Example:             
PS C:\windows\system32> Install-Script -Name $scriptName -Repository $repositoryName -Scope $Scope -Verbose

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n


```

## <a name="install-script-cmdlet-in-pipeline-operations"></a><span data-ttu-id="d9bc6-156">Script voor installatie cmdlet in pipeline-bewerkingen</span><span class="sxs-lookup"><span data-stu-id="d9bc6-156">Install-Script cmdlet in pipeline operations</span></span>

```powershell

# Find a module and install it
Find-Script -Name "MyDSC*" | Install-Script

# Find a module and install it to the CurrentUser scope
Find-Script -Name "MyDSC*" | Install-Script -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Script to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Script
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Script cmdlet by using the pipeline operator. The Install-Script cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Script cmdlet from the same module, Install-Script attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Script
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Script
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="d9bc6-157">Ondersteuning voor side-by-Side-versie in PowerShell 5.0 of hoger</span><span class="sxs-lookup"><span data-stu-id="d9bc6-157">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="d9bc6-158">PowerShellGet ondersteunt de side-by-side (SxS) module versie-ondersteuning in het Script voor installatie, Update-Script en publiceren Script-cmdlets die worden uitgevoerd in Windows PowerShell 5.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-158">PowerShellGet supports the side-by-side (SxS) module version support in Install-Script, Update-Script, and Publish-Script cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-script-examples"></a><span data-ttu-id="d9bc6-159">Script voor installatie-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d9bc6-159">Install-Script examples</span></span>

```powershell
# Install a version of the module
Install-Script -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Script -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Script -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Script -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="d9bc6-160">Module met de bijbehorende afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="d9bc6-160">Install module with its dependencies</span></span>

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Script -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a><span data-ttu-id="d9bc6-161">Fout bij scenario 's</span><span class="sxs-lookup"><span data-stu-id="d9bc6-161">Error scenarios</span></span>

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Script'
Install-Script ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Script'
Install-Script ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -MinimumVersion 2.0

```

## <a name="installing-a-script-with-dependent-scripts-and-modules"></a><span data-ttu-id="d9bc6-162">Een script installeren met afhankelijke scripts en modules</span><span class="sxs-lookup"><span data-stu-id="d9bc6-162">Installing a script with dependent scripts and modules</span></span>

```powershell
# Installing a script with dependent scripts and modules
Find-Script -Repository GalleryINT -Name Script-WithDependencies2 -IncludeDependencies
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script

Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
Get-InstalledModule
Install-Script -Repository GalleryINT -Name Script-WithDependencies2 -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
Get-InstalledModule
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module

# Contents of Script-WithDependencies2 file.
<#PSScriptInfo
.VERSION 2.0
.GUID 90082fa1-0b84-49fb-a00e-0a624fbb6584
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag-Script-WithDependencies2-2.0
.LICENSEURI http://script-withdependencies2.com/license
.PROJECTURI http://script-withdependencies2.com/
.ICONURI http://script-withdependencies2.com/icon
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS Required-Script1,Required-Script2,Required-Script3
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
Script-WithDependencies2 release notes
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'}
#Requires -Module @{RequiredVersion = '2.5'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '1.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '2.0'}
#Requires -Module @{MaximumVersion = '1.5'; ModuleName = 'RequiredModule5'}
<#
.DESCRIPTION
Description for the Script-WithDependencies2 script
#>
Param()
Function Test-FunctionFromScript\_Script-WithDependencies2 { Get-Date }
Workflow Test-WorkflowFromScript\_Script-WithDependencies2 { Get-Date }
```

## <a name="install-script-and-get-installedscript-cmdlets"></a><span data-ttu-id="d9bc6-163">Script voor installatie en Get-InstalledScript-cmdlets</span><span class="sxs-lookup"><span data-stu-id="d9bc6-163">Install-Script and Get-InstalledScript cmdlets</span></span>
<span data-ttu-id="d9bc6-164">Script voor installatie-cmdlet kunt u een specifiek scriptbestand samen met de bijbehorende afhankelijkheden installeren voor het opgegeven bereik.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-164">Install-Script cmdlet lets you to install a specific script file along with its dependencies to the specified scope.</span></span> <span data-ttu-id="d9bc6-165">Scripts zijn standaard geïnstalleerd aan de scope AllUsers.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-165">By default, scripts are installed to the AllUsers scope.</span></span> <span data-ttu-id="d9bc6-166">De cmdlet Get-InstalledScript kunt u de lijst met scriptbestanden die zijn geïnstalleerd met de cmdlet Install-Script ophalen.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-166">Get-InstalledScript cmdlet lets you to get the list of script files which were installed using Install-Script cmdlet.</span></span>

<span data-ttu-id="d9bc6-167">Gebruik Opmerking: als beheer- en scripts zoeken wanneer ze zijn geïnstalleerd, script voor installatie een standaardmap voor het opslaan van scripts op $home\Documents\WindowsPowerShell\Scripts maken en die map toevoegen aan uw omgeving pad.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-167">Use note: To allow management and locating of scripts once they are installed, Install-script will create a default folder for storing scripts at $home\Documents\WindowsPowerShell\Scripts, and add that folder to your PATH environment.</span></span> <span data-ttu-id="d9bc6-168">Als het pad wijzigen belangrijk is, moet u opslaan-Script gebruiken in plaats van een Script voor installatie.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-168">If modifying the path is a concern, use Save-Script instead of Install-Script.</span></span> <span data-ttu-id="d9bc6-169">Get-InstalledScripts en Uninstall-Script kunt werken alleen met behulp van scripts op het systeem met Script voor installatie geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-169">Get-InstalledScripts and Uninstall-Script can only work with scripts placed on the system using Install-Script.</span></span>
```powershell
# Install locations for scripts:
# Default scope is AllUsers.
# AllUsers scope --> "$env:ProgramFiles\\WindowsPowerShell\\Scripts"
# CurrentUser scope -->; "$env:USERPROFILE\\Documents\\WindowsPowerShell\\Scripts"

# Piping Find-Script output to Install-Script cmdlet
Find-Script -Repository GalleryINT -Name Required-Script2 | Install-Script -Scope CurrentUser -Verbose
VERBOSE: Repository details, Name = 'GalleryINT', Location = 'https://customgallery.cloudapp.net/api/v2/'; IsTrusted = 'True'; IsRegistered = 'True'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'GalleryINT'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://customgallery.cloudapp.net/api/v2/items/psscript/' and PackageManagementProvider is 'NuGet'.
VERBOSE: Searching repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/FindPackagesById()?id='Required-Script2'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'Required-Script2'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: The installation scope is specified to be 'CurrentUser'.
VERBOSE: The specified script will be installed in 'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts' and its dependent modules will be installed in
'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading script 'Required-Script2' with version '2.5' from the repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/'.
VERBOSE: Script 'Required-Script2' was installed successfully.

Get-InstalledScript Required-Scri\*
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script

Get-InstalledScript Required-Script2 | Format-List \* -Force
Name : Required-Script2
Version : 2.5
Type : Script
Description : Description for the Required-Script2 script
Author : manikb
CompanyName :
Copyright : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate : 10/30/2015 1:25:15 AM
LicenseUri : http://required-script2.com/license
ProjectUri : http://required-script2.com/
IconUri : http://required-script2.com/icon
Tags : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript}
Includes : {Function, DscResource, Cmdlet, Workflow...}
PowerShellGetFormatVersion :
ReleaseNotes : Required-Script2 release notes
Dependencies : {}
RepositorySourceLocation : https://customgallery.cloudapp.net/api/v2/
Repository : GalleryINT
PackageManagementProvider : NuGet
AdditionalMetadata : {Type, releaseNotes, copyright, PackageManagementProvider...}
InstalledLocation : C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Installed script file is immediately available for usage.
```

<span data-ttu-id="d9bc6-170">U kunt ook de Get-Command – naam <InstalledScriptFileName> downloaden.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-170">You can also use Get-Command –Name <InstalledScriptFileName> to get it.</span></span> <span data-ttu-id="d9bc6-171">Installatie op twee locaties worden toegevoegd aan de omgevingsvariabele PATH op het eerste gebruik van een opgegeven bereik.</span><span class="sxs-lookup"><span data-stu-id="d9bc6-171">Two install locations are added to the PATH environment variable on first use of a specified scope.</span></span>
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1

Find-Script -Repository LocalRepo1 -Name Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Find-Script -Repository LocalRepo1 -Name Demo-Script | Install-Script -Scope CurrentUser
Untrusted repository
You are installing the scripts from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the scripts from 'C:\\MyLocalRepo'?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"): Y

Get-InstalledScript Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Get-Command Demo-Script
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Demo-Script.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Demo-Script.ps1

# Using the installed script
Demo-Script
Demo-ScriptFunction
Demo-ScriptWorkflow

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Repository GalleryINT -Name Required-Script3 -RequiredVersion 2.0
Get-InstalledScript -Name Required-Script3

Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
Get-InstalledScript -Name Required-Script3 | Format-List Name,InstalledLocation -Force
Name : Required-Script3
InstalledLocation : C:\\Program Files\\WindowsPowerShell\\Scripts

Get-Command Required-Script3
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script3.ps1 C:\\Program Files\\WindowsPowerShell\\Scripts\\Required-Script3.ps1

# Installing a script with dependent scripts and modules
Find-Script -Repository GalleryINT -Name Script-WithDependencies2 -IncludeDependencies
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script

Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
Get-InstalledModule
Install-Script -Repository GalleryINT -Name Script-WithDependencies2 -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
Get-InstalledModule
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module

# Contents of Script-WithDependencies2 file.
<#PSScriptInfo
.VERSION 2.0
.GUID 90082fa1-0b84-49fb-a00e-0a624fbb6584
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag-Script-WithDependencies2-2.0
.LICENSEURI http://script-withdependencies2.com/license
.PROJECTURI http://script-withdependencies2.com/
.ICONURI http://script-withdependencies2.com/icon
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS Required-Script1,Required-Script2,Required-Script3
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
Script-WithDependencies2 release notes
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'}
#Requires -Module @{RequiredVersion = '2.5'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '1.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '2.0'}
#Requires -Module @{MaximumVersion = '1.5'; ModuleName = 'RequiredModule5'}
<#
.DESCRIPTION
Description for the Script-WithDependencies2 script
#>
Param()
Function Test-FunctionFromScript\_Script-WithDependencies2 { Get-Date }
Workflow Test-WorkflowFromScript\_Script-WithDependencies2 { Get-Date }
```

