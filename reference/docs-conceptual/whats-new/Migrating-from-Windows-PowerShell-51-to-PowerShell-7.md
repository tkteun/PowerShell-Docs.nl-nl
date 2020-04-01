---
title: Migreren van Windows PowerShell 5.1 naar PowerShell 7
description: Update van Power shell 5,1 naar Power shell 7 voor uw Windows-platforms.
ms.date: 03/25/2020
ms.openlocfilehash: e3881b1758f50119444969ad39541aec694cebe5
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500492"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="eacb3-103">Migreren van Windows PowerShell 5.1 naar PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="eacb3-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="eacb3-104">Power shell 7 is ontworpen voor Cloud-, on-premises en hybride omgevingen en is voorzien van verbeteringen en [nieuwe functies](What-s-New-in-PowerShell-70.md).</span><span class="sxs-lookup"><span data-stu-id="eacb3-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="eacb3-105">Installeert en voert side-by-side uit met Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="eacb3-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="eacb3-106">Verbeterde compatibiliteit met bestaande Windows Power shell-modules</span><span class="sxs-lookup"><span data-stu-id="eacb3-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="eacb3-107">Nieuwe taal functies, zoals ternaire Opera tors en `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="eacb3-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="eacb3-108">Verbeterde prestaties</span><span class="sxs-lookup"><span data-stu-id="eacb3-108">Improved performance</span></span>
- <span data-ttu-id="eacb3-109">Externe toegang op basis van SSH</span><span class="sxs-lookup"><span data-stu-id="eacb3-109">SSH-based remoting</span></span>
- <span data-ttu-id="eacb3-110">Interoperabiliteit tussen verschillende platforms</span><span class="sxs-lookup"><span data-stu-id="eacb3-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="eacb3-111">Ondersteuning voor docker-containers</span><span class="sxs-lookup"><span data-stu-id="eacb3-111">Support for Docker containers</span></span>

<span data-ttu-id="eacb3-112">Power shell 7 werkt naast Windows Power shell eenvoudig te testen en vergelijken van edities vóór de implementatie.</span><span class="sxs-lookup"><span data-stu-id="eacb3-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="eacb3-113">Migratie is eenvoudig, snel en veilig.</span><span class="sxs-lookup"><span data-stu-id="eacb3-113">Migration is simple, quick, and safe.</span></span> <span data-ttu-id="eacb3-114">veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="eacb3-114">failure.</span></span>

<span data-ttu-id="eacb3-115">Power shell 7 wordt ondersteund op de volgende Windows-besturings systemen:</span><span class="sxs-lookup"><span data-stu-id="eacb3-115">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="eacb3-116">Windows 8,1 en 10</span><span class="sxs-lookup"><span data-stu-id="eacb3-116">Windows 8.1 and 10</span></span>
- <span data-ttu-id="eacb3-117">Windows Server 2012, 2012 R2, 2016 en 2019</span><span class="sxs-lookup"><span data-stu-id="eacb3-117">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="eacb3-118">Power shell 7 wordt ook uitgevoerd op macOS en verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="eacb3-118">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="eacb3-119">Voor een lijst met ondersteunde besturings systemen en informatie over de ondersteunings levenscyclus raadpleegt u de [levens cyclus van Power Shell-ondersteuning](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="eacb3-119">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="eacb3-120">Power shell 7 installeren</span><span class="sxs-lookup"><span data-stu-id="eacb3-120">Installing PowerShell 7</span></span>

<span data-ttu-id="eacb3-121">Voor flexibiliteit en het ondersteunen van de behoeften van IT, DevOps engineers en ontwikkel aars zijn er verschillende opties beschikbaar om Power shell 7 te installeren.</span><span class="sxs-lookup"><span data-stu-id="eacb3-121">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="eacb3-122">In de meeste gevallen kunnen de installatie opties worden beperkt tot de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="eacb3-122">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="eacb3-123">Power shell implementeren met het [MSI-pakket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span><span class="sxs-lookup"><span data-stu-id="eacb3-123">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="eacb3-124">Power shell implementeren met behulp van het [zip-pakket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span><span class="sxs-lookup"><span data-stu-id="eacb3-124">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="eacb3-125">Het MSI-pakket kan worden geïmplementeerd en bijgewerkt met beheer producten als [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span><span class="sxs-lookup"><span data-stu-id="eacb3-125">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="eacb3-126">Down load de pakketten van [github release pagina](https://github.com/PowerShell/PowerShell/releases).</span><span class="sxs-lookup"><span data-stu-id="eacb3-126">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="eacb3-127">Voor het implementeren van het MSI-pakket is beheerders machtigingen vereist.</span><span class="sxs-lookup"><span data-stu-id="eacb3-127">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="eacb3-128">Het ZIP-pakket kan door elke gebruiker worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="eacb3-128">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="eacb3-129">Het ZIP-pakket is de eenvoudigste manier om Power shell 7 te installeren voor tests voordat een volledige installatie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eacb3-129">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="eacb3-130">Power shell 7 side-by-side gebruiken met Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="eacb3-130">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="eacb3-131">Power shell 7 is ontworpen om samen te bestaan met Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="eacb3-131">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="eacb3-132">De volgende functies zorgen ervoor dat uw investering in Power shell is beveiligd en dat de migratie naar Power shell 7 eenvoudig is.</span><span class="sxs-lookup"><span data-stu-id="eacb3-132">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="eacb3-133">Afzonderlijk installatiepad en uitvoer bare naam</span><span class="sxs-lookup"><span data-stu-id="eacb3-133">Separate installation path and executable name</span></span>
- <span data-ttu-id="eacb3-134">Afzonderlijke PSModulePath</span><span class="sxs-lookup"><span data-stu-id="eacb3-134">Separate PSModulePath</span></span>
- <span data-ttu-id="eacb3-135">Afzonderlijke profielen voor elke versie</span><span class="sxs-lookup"><span data-stu-id="eacb3-135">Separate profiles for each version</span></span>
- <span data-ttu-id="eacb3-136">Verbeterde module compatibiliteit</span><span class="sxs-lookup"><span data-stu-id="eacb3-136">Improved module compatibility</span></span>
- <span data-ttu-id="eacb3-137">Nieuwe externe eind punten</span><span class="sxs-lookup"><span data-stu-id="eacb3-137">New remoting endpoints</span></span>
- <span data-ttu-id="eacb3-138">Ondersteuning voor groeps beleid</span><span class="sxs-lookup"><span data-stu-id="eacb3-138">Group policy support</span></span>
- <span data-ttu-id="eacb3-139">Afzonderlijke gebeurtenis logboeken</span><span class="sxs-lookup"><span data-stu-id="eacb3-139">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="eacb3-140">Afzonderlijk installatiepad en uitvoer bare naam</span><span class="sxs-lookup"><span data-stu-id="eacb3-140">Separate installation path and executable name</span></span>

<span data-ttu-id="eacb3-141">Power shell 7 wordt geïnstalleerd in een nieuwe map, waardoor gelijktijdige uitvoering kan worden uitgevoerd met Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="eacb3-141">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="eacb3-142">Locaties installeren op versie:</span><span class="sxs-lookup"><span data-stu-id="eacb3-142">Install locations by version:</span></span>

- <span data-ttu-id="eacb3-143">Windows Power shell 5,1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="eacb3-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="eacb3-144">Power shell Core 6. x: `$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="eacb3-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="eacb3-145">Power shell 7: `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="eacb3-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="eacb3-146">De nieuwe locatie wordt toegevoegd aan het pad, zodat u Windows Power shell 5,1 en Power shell 7 kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="eacb3-146">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="eacb3-147">Als u migreert van Power shell Core 6. x naar Power shell 7, wordt Power shell 6 verwijderd en wordt het pad vervangen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-147">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="eacb3-148">In Windows Power Shell heeft het uitvoer bare Power shell-bestand de naam `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="eacb3-148">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="eacb3-149">In versie 6 en hoger wordt het uitvoer bare bestand de naam `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="eacb3-149">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="eacb3-150">De nieuwe naam maakt het eenvoudig om gelijktijdige uitvoering van beide versies te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-150">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="eacb3-151">Afzonderlijke PSModulePath</span><span class="sxs-lookup"><span data-stu-id="eacb3-151">Separate PSModulePath</span></span>

<span data-ttu-id="eacb3-152">Standaard worden modules voor Windows Power shell en Power shell 7 opgeslagen op verschillende locaties.</span><span class="sxs-lookup"><span data-stu-id="eacb3-152">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="eacb3-153">Power shell 7 combineert die locaties in de omgevings variabele `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="eacb3-153">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="eacb3-154">Wanneer u een module op naam importeert, controleert Power shell de locatie die is opgegeven door `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="eacb3-154">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="eacb3-155">Hierdoor kan Power shell 7 zowel de kern-als bureaublad modules laden.</span><span class="sxs-lookup"><span data-stu-id="eacb3-155">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="eacb3-156">Installatie bereik</span><span class="sxs-lookup"><span data-stu-id="eacb3-156">Install Scope</span></span>            |                <span data-ttu-id="eacb3-157">Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="eacb3-157">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="eacb3-158">Power shell 7,0</span><span class="sxs-lookup"><span data-stu-id="eacb3-158">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="eacb3-159">PowerShell-modules</span><span class="sxs-lookup"><span data-stu-id="eacb3-159">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="eacb3-160">Gebruiker geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="eacb3-160">User installed</span></span><br><span data-ttu-id="eacb3-161">AllUsers-bereik</span><span class="sxs-lookup"><span data-stu-id="eacb3-161">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="eacb3-162">Gebruiker geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="eacb3-162">User installed</span></span><br><span data-ttu-id="eacb3-163">Het bereik CurrentUser</span><span class="sxs-lookup"><span data-stu-id="eacb3-163">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="eacb3-164">In de volgende voor beelden ziet u de standaard waarden van `$Env:PSModulePath` voor elke versie.</span><span class="sxs-lookup"><span data-stu-id="eacb3-164">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="eacb3-165">Voor Windows Power shell 5,1:</span><span class="sxs-lookup"><span data-stu-id="eacb3-165">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="eacb3-166">Voor Power shell 7:</span><span class="sxs-lookup"><span data-stu-id="eacb3-166">For PowerShell 7:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

<span data-ttu-id="eacb3-167">Power shell 7 bevat de Windows Power shell-paden en de Power shell 7-paden om modules te kunnen laden.</span><span class="sxs-lookup"><span data-stu-id="eacb3-167">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="eacb3-168">Er kunnen extra paden bestaan als u de omgevings variabele PSModulePath of geïnstalleerde aangepaste modules of toepassingen hebt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="eacb3-168">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="eacb3-169">Zie `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eacb3-169">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="eacb3-170">Zie [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="eacb3-170">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="eacb3-171">Afzonderlijke profielen</span><span class="sxs-lookup"><span data-stu-id="eacb3-171">Separate profiles</span></span>

<span data-ttu-id="eacb3-172">Een Power shell-profiel is een script dat wordt uitgevoerd wanneer Power shell wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="eacb3-172">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="eacb3-173">Met dit script past u uw omgeving aan door opdrachten, aliassen, functies, variabelen, modules en Power Shell-stations toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-173">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="eacb3-174">Het profiel script maakt deze aanpassingen beschikbaar in elke sessie, zonder dat u ze hand matig opnieuw hoeft te maken.</span><span class="sxs-lookup"><span data-stu-id="eacb3-174">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="eacb3-175">Het pad naar de locatie van het profiel is gewijzigd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="eacb3-175">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="eacb3-176">In Windows Power shell 5,1 is de locatie van het profiel `$HOME\Documents\WindowsPowerShell`.</span><span class="sxs-lookup"><span data-stu-id="eacb3-176">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="eacb3-177">In Power shell 7 is de locatie van het profiel `$HOME\Documents\PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="eacb3-177">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="eacb3-178">De bestands namen van het profiel zijn ook gewijzigd:</span><span class="sxs-lookup"><span data-stu-id="eacb3-178">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="eacb3-179">[About_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eacb3-179">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="eacb3-180">Compatibiliteit met Power shell 7 met Windows Power shell 5,1-modules</span><span class="sxs-lookup"><span data-stu-id="eacb3-180">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="eacb3-181">De meeste modules die u in Windows Power shell 5,1 gebruikt, werken al met Power shell 7, met inbegrip van Azure PowerShell en Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eacb3-181">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="eacb3-182">We blijven samen werken met andere teams om native Power shell 7-ondersteuning toe te voegen voor meer modules, waaronder Microsoft Graph, Office 365 en anderen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-182">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="eacb3-183">Voor de huidige lijst met ondersteunde modules raadpleegt u compatibiliteit met de [module Power shell 7](/powershell/scripting/whats-new/module-compatibility).</span><span class="sxs-lookup"><span data-stu-id="eacb3-183">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="eacb3-184">In Windows hebben we ook een **UseWindowsPowerShell** -Schakel optie toegevoegd aan `Import-Module` om de overgang naar Power shell 7 te vereenvoudigen voor degenen die gebruikmaken van incompatibele modules.</span><span class="sxs-lookup"><span data-stu-id="eacb3-184">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="eacb3-185">Zie [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility)voor meer informatie over deze functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="eacb3-185">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="eacb3-186">Externe communicatie met Power shell</span><span class="sxs-lookup"><span data-stu-id="eacb3-186">PowerShell Remoting</span></span>

<span data-ttu-id="eacb3-187">Met externe communicatie van Power shell kunt u elke Power shell-opdracht op een of meer externe computers uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="eacb3-187">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="eacb3-188">U kunt permanente verbindingen tot stand brengen, interactieve sessies starten en scripts uitvoeren op externe computers.</span><span class="sxs-lookup"><span data-stu-id="eacb3-188">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="eacb3-189">Externe communicatie van WS-Management</span><span class="sxs-lookup"><span data-stu-id="eacb3-189">WS-Management remoting</span></span>

<span data-ttu-id="eacb3-190">Windows Power shell 5,1 en lager gebruiken het WS-Management-Protocol (WSMAN) voor verbindings onderhandeling en gegevens overdracht.</span><span class="sxs-lookup"><span data-stu-id="eacb3-190">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="eacb3-191">Windows Remote Management (WinRM) maakt gebruik van het WSMAN-protocol.</span><span class="sxs-lookup"><span data-stu-id="eacb3-191">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="eacb3-192">Als WinRM is ingeschakeld, gebruikt Power shell 7 het bestaande Windows Power shell 5,1-eind punt met de naam `Microsoft.PowerShell` voor externe verbindingen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-192">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="eacb3-193">Als u Power shell 7 wilt bijwerken om een eigen eind punt op te halen, voert u de `Enable-PSRemoting`-cmdlet uit.</span><span class="sxs-lookup"><span data-stu-id="eacb3-193">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="eacb3-194">Zie voor meer informatie over het maken van verbinding met specifieke eind punten [WS-Management Remoting in Power shell core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="eacb3-194">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="eacb3-195">Als u externe toegang tot Windows Power shell wilt gebruiken, moet u de computer configureren voor extern beheer.</span><span class="sxs-lookup"><span data-stu-id="eacb3-195">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="eacb3-196">Zie [over externe vereisten](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)voor meer informatie, waaronder instructies.</span><span class="sxs-lookup"><span data-stu-id="eacb3-196">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="eacb3-197">Zie voor meer informatie over het werken met externe communicatie [over externe](/powershell/module/microsoft.powershell.core/about/about_remote)</span><span class="sxs-lookup"><span data-stu-id="eacb3-197">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="eacb3-198">Externe toegang op basis van SSH</span><span class="sxs-lookup"><span data-stu-id="eacb3-198">SSH-based remoting</span></span>

<span data-ttu-id="eacb3-199">Op SSH gebaseerde externe toegang is toegevoegd aan Power shell Core 6. x ter ondersteuning van andere besturings systemen die geen Windows systeem eigen onderdelen zoals **WinRM**kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="eacb3-199">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="eacb3-200">Externe SSH-processen maken een Power shell-hostproces op de doel computer als een SSH-subsysteem.</span><span class="sxs-lookup"><span data-stu-id="eacb3-200">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="eacb3-201">Zie voor meer informatie en voor beelden over het instellen van op SSH gebaseerde externe toegang op Windows of Linux: [Power shell Remoting via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="eacb3-201">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="eacb3-202">De PowerShell Gallery (PSGallery) bevat een module en cmdlet waarmee op SSH gebaseerde externe toegang automatisch wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="eacb3-202">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="eacb3-203">Installeer de `Microsoft.PowerShell.RemotingTools`-module van de [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) en voer de `Enable-SSH`-cmdlet uit.</span><span class="sxs-lookup"><span data-stu-id="eacb3-203">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="eacb3-204">De cmdlets `New-PSSession`, `Enter-PSSession`en `Invoke-Command` hebben nieuwe parameter sets voor de ondersteuning van SSH-verbindingen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-204">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="eacb3-205">Als u een externe sessie wilt maken, geeft u de doel computer op met de para meter **hostname** en geeft u de gebruikers naam met de **naam**van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="eacb3-205">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="eacb3-206">Wanneer de cmdlets interactief worden uitgevoerd, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-206">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="eacb3-207">U kunt ook bij het gebruik van de para meter **hostname** de gebruikers naam gegevens opgeven, gevolgd door het apen staartje (@), gevolgd door de naam van de computer.</span><span class="sxs-lookup"><span data-stu-id="eacb3-207">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign ('@'), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="eacb3-208">U kunt SSH-sleutel verificatie instellen met behulp van een persoonlijke-sleutel bestand **met de para** meter sleutelpad.</span><span class="sxs-lookup"><span data-stu-id="eacb3-208">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="eacb3-209">Zie [OpenSSH key management](/windows-server/administration/openssh/openssh_keymanagement)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eacb3-209">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="eacb3-210">groepsbeleid ondersteund</span><span class="sxs-lookup"><span data-stu-id="eacb3-210">Group Policy supported</span></span>

<span data-ttu-id="eacb3-211">Power shell bevat groepsbeleid instellingen die u helpen bij het definiëren van consistente optie waarden voor servers in een bedrijfs omgeving.</span><span class="sxs-lookup"><span data-stu-id="eacb3-211">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="eacb3-212">Deze instellingen omvatten:</span><span class="sxs-lookup"><span data-stu-id="eacb3-212">These settings include:</span></span>

- <span data-ttu-id="eacb3-213">Console sessie configuratie: Hiermee stelt u een configuratie-eind punt in waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eacb3-213">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="eacb3-214">Module logboek registratie inschakelen: Hiermee wordt de eigenschap LogPipelineExecutionDetails van modules ingesteld.</span><span class="sxs-lookup"><span data-stu-id="eacb3-214">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="eacb3-215">Power shell-script blok logboek registratie inschakelen: Hiermee wordt gedetailleerde logboek registratie van alle Power shell-scripts ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="eacb3-215">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="eacb3-216">Script uitvoering inschakelen: Hiermee stelt u het Power shell-uitvoerings beleid in.</span><span class="sxs-lookup"><span data-stu-id="eacb3-216">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="eacb3-217">Power shell transcriptie inschakelen: Hiermee wordt de invoer en uitvoer van Power shell-opdrachten vastgelegd in Transcripten op basis van tekst.</span><span class="sxs-lookup"><span data-stu-id="eacb3-217">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="eacb3-218">Het standaardpad instellen voor update-Help: Hiermee stelt u de bron in op Help-informatie voor een directory, niet via internet.</span><span class="sxs-lookup"><span data-stu-id="eacb3-218">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="eacb3-219">Zie [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eacb3-219">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="eacb3-220">Power shell 7 bevat groepsbeleid sjablonen en een installatie script in `$PSHOME`.</span><span class="sxs-lookup"><span data-stu-id="eacb3-220">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="eacb3-221">Groepsbeleid-hulpprogram ma's gebruiken beheer sjabloon bestanden (`.admx`, `.adml`) om beleids instellingen in de gebruikers interface in te vullen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-221">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="eacb3-222">Hiermee kunnen beheerders beleids instellingen op basis van het REGI ster beheren.</span><span class="sxs-lookup"><span data-stu-id="eacb3-222">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="eacb3-223">Met het script `InstallPSCorePolicyDefinitions.ps1` wordt Power shell core-Beheersjablonen geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="eacb3-223">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a><span data-ttu-id="eacb3-224">Afzonderlijke gebeurtenis logboeken</span><span class="sxs-lookup"><span data-stu-id="eacb3-224">Separate Event Logs</span></span>

<span data-ttu-id="eacb3-225">Windows Power shell en Power shell 7-logboek gebeurtenissen voor het scheiden van gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="eacb3-225">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="eacb3-226">Gebruik de volgende opdracht om een lijst met de Power shell-logboeken op te halen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-226">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="eacb3-227">Zie [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eacb3-227">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="eacb3-228">Verbeterde bewerkings ervaring met Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="eacb3-228">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="eacb3-229">[Visual Studio code (VSCode)](https://code.visualstudio.com/) met de [Power shell-extensie](https://code.visualstudio.com/docs/languages/powershell) is de ondersteunde script omgeving voor Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="eacb3-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="eacb3-230">De Windows Power shell Integrated Scripting Environment (ISE) biedt alleen ondersteuning voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="eacb3-230">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="eacb3-231">De bijgewerkte Power shell-extensie bevat:</span><span class="sxs-lookup"><span data-stu-id="eacb3-231">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="eacb3-232">Nieuwe ISE-compatibiliteits modus</span><span class="sxs-lookup"><span data-stu-id="eacb3-232">New ISE compatibility mode</span></span>
- <span data-ttu-id="eacb3-233">PSReadLine in de geïntegreerde console, met inbegrip van syntaxis markering, meerdere regels bewerken en terug zoeken</span><span class="sxs-lookup"><span data-stu-id="eacb3-233">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="eacb3-234">Verbeteringen in stabiliteit en prestaties</span><span class="sxs-lookup"><span data-stu-id="eacb3-234">Stability and performance improvements</span></span>
- <span data-ttu-id="eacb3-235">Nieuwe code lens-integratie</span><span class="sxs-lookup"><span data-stu-id="eacb3-235">New CodeLens integration</span></span>
- <span data-ttu-id="eacb3-236">Verbeterde automatische aanvulling van paden</span><span class="sxs-lookup"><span data-stu-id="eacb3-236">Improved path auto-completion</span></span>

<span data-ttu-id="eacb3-237">Als u de overgang naar Visual Studio code eenvoudiger wilt maken, gebruikt u de functie **ISE-modus inschakelen** die beschikbaar is in het **opdracht palet**.</span><span class="sxs-lookup"><span data-stu-id="eacb3-237">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="eacb3-238">Deze functie schakelt VSCode in een ISE-opmaak.</span><span class="sxs-lookup"><span data-stu-id="eacb3-238">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="eacb3-239">De ISE-indeling biedt u alle nieuwe functies en mogelijkheden van Power shell in een vertrouwde gebruikers ervaring.</span><span class="sxs-lookup"><span data-stu-id="eacb3-239">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="eacb3-240">Als u wilt overschakelen naar de nieuwe ISE-indeling, drukt u op <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> om het **opdracht palet**te openen, typt u `PowerShell` en selecteert u **Power shell: modus ISE inschakelen**.</span><span class="sxs-lookup"><span data-stu-id="eacb3-240">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="eacb3-241">Als u de indeling wilt instellen op de oorspronkelijke indeling, opent u het **opdracht palet**en selecteert u **Power shell: de modus ISE uitschakelen (standaard instellingen herstellen)** .</span><span class="sxs-lookup"><span data-stu-id="eacb3-241">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="eacb3-242">Zie [de ISE-ervaring repliceren in Visual Studio code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode) voor meer informatie over het aanpassen van de VSCode-indeling naar ISE.</span><span class="sxs-lookup"><span data-stu-id="eacb3-242">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="eacb3-243">Er zijn geen plannen om de ISE bij te werken met nieuwe functies.</span><span class="sxs-lookup"><span data-stu-id="eacb3-243">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="eacb3-244">De ISE is nu een functie die door de gebruiker kan worden verwijderd in de nieuwste versies van Windows 10 en Windows Server.</span><span class="sxs-lookup"><span data-stu-id="eacb3-244">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="eacb3-245">Er zijn geen plannen om de ISE permanent te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="eacb3-245">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="eacb3-246">Het Power shell-team en de bijbehorende partners zijn gericht op het verbeteren van de scripting ervaring in de Power shell-extensie voor Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="eacb3-246">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="eacb3-247">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="eacb3-247">Next Steps</span></span>

<span data-ttu-id="eacb3-248">U kunt met de kennis die effectief kan worden gemigreerd, [Power shell 7 nu installeren](/powershell/scripting/install/installing-powershell-core-on-windows) .</span><span class="sxs-lookup"><span data-stu-id="eacb3-248">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
