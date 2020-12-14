---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: d635a1f037194380c143190e48d654e828f88bc8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890161"
---
# <span data-ttu-id="77dec-103">Get-Package</span><span class="sxs-lookup"><span data-stu-id="77dec-103">Get-Package</span></span>

## <span data-ttu-id="77dec-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="77dec-104">SYNOPSIS</span></span>
<span data-ttu-id="77dec-105">Retourneert een lijst met alle software pakketten die zijn geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="77dec-105">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="77dec-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="77dec-106">SYNTAX</span></span>

### <span data-ttu-id="77dec-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="77dec-107">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="77dec-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="77dec-108">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="77dec-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="77dec-109">DESCRIPTION</span></span>

<span data-ttu-id="77dec-110">De `Get-Package` cmdlet retourneert een lijst met alle software pakketten op de lokale computer die is geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="77dec-110">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="77dec-111">U kunt uitvoeren `Get-Package` op externe computers door deze uit te voeren als onderdeel van een `Invoke-Command` `Enter-PSSession` opdracht of script.</span><span class="sxs-lookup"><span data-stu-id="77dec-111">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="77dec-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="77dec-112">EXAMPLES</span></span>

### <span data-ttu-id="77dec-113">Voor beeld 1: alle geïnstalleerde pakketten ophalen</span><span class="sxs-lookup"><span data-stu-id="77dec-113">Example 1: Get all installed packages</span></span>

<span data-ttu-id="77dec-114">De `Get-Package` cmdlet haalt alle pakketten op die zijn geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="77dec-114">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="77dec-115">Voor beeld 2: pakketten ophalen die zijn geïnstalleerd op een externe computer</span><span class="sxs-lookup"><span data-stu-id="77dec-115">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="77dec-116">Met deze opdracht wordt een lijst opgehaald met pakketten die zijn geïnstalleerd door **Package Management** op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="77dec-116">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="77dec-117">Met deze opdracht wordt u gevraagd het wacht woord van de opgegeven gebruiker op te geven.</span><span class="sxs-lookup"><span data-stu-id="77dec-117">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="77dec-118">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om een externe computer op te geven, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="77dec-118">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="77dec-119">De **referentie** parameter bevat een domein-en gebruikers naam met machtigingen voor het uitvoeren van opdrachten op de computer.</span><span class="sxs-lookup"><span data-stu-id="77dec-119">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="77dec-120">De para meter **script Block** voert de `Get-Package` cmdlet uit op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="77dec-120">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="77dec-121">Voor beeld 3: pakketten voor een opgegeven provider ophalen</span><span class="sxs-lookup"><span data-stu-id="77dec-121">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="77dec-122">Met deze opdracht worden software pakketten die zijn geïnstalleerd op de lokale computer van een specifieke provider opgehaald.</span><span class="sxs-lookup"><span data-stu-id="77dec-122">This command gets software packages installed on the local computer from a specific provider.</span></span>

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="77dec-123">`Get-Package` maakt gebruik van de para meter **ProviderName** om een specifieke provider op te geven, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="77dec-123">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="77dec-124">In de para meter **all-versions** wordt elke geïnstalleerde versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="77dec-124">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="77dec-125">Voor beeld 4: een exacte versie van een specifiek pakket ophalen</span><span class="sxs-lookup"><span data-stu-id="77dec-125">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="77dec-126">Met deze opdracht wordt een specifieke versie van een geïnstalleerd pakket opgehaald.</span><span class="sxs-lookup"><span data-stu-id="77dec-126">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="77dec-127">Er kan meer dan één versie van een pakket worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="77dec-127">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="77dec-128">`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="77dec-128">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="77dec-129">De para meter **ProviderName** specificeert de provider, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="77dec-129">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="77dec-130">De **vereiste-versie** parameter geeft een geïnstalleerde versie op.</span><span class="sxs-lookup"><span data-stu-id="77dec-130">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="77dec-131">Voor beeld 5: een pakket verwijderen</span><span class="sxs-lookup"><span data-stu-id="77dec-131">Example 5: Uninstall a package</span></span>

<span data-ttu-id="77dec-132">In dit voor beeld worden pakket gegevens opgehaald en wordt het pakket vervolgens verwijderd.</span><span class="sxs-lookup"><span data-stu-id="77dec-132">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="77dec-133">`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **posh-Git**.</span><span class="sxs-lookup"><span data-stu-id="77dec-133">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="77dec-134">De **RequiredVersion** -para meter is een specifieke versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="77dec-134">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="77dec-135">Het object wordt vanuit de pijp lijn naar de `Uninstall-Package` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="77dec-135">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="77dec-136">`Uninstall-Package` Hiermee verwijdert u het pakket.</span><span class="sxs-lookup"><span data-stu-id="77dec-136">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="77dec-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="77dec-137">PARAMETERS</span></span>

### <span data-ttu-id="77dec-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="77dec-138">-AllowClobber</span></span>

<span data-ttu-id="77dec-139">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="77dec-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="77dec-140">Overschrijft bestaande opdrachten die dezelfde naam hebben als opdrachten die door een module worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="77dec-140">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="77dec-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="77dec-142">Bevat pakketten die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="77dec-142">Includes packages marked as a prerelease in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="77dec-143">-AllVersions</span></span>

<span data-ttu-id="77dec-144">Hiermee wordt aangegeven dat `Get-Package` alle beschik bare versies van het pakket worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="77dec-144">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="77dec-145">`Get-Package`Retourneert standaard alleen de nieuwste beschik bare versie.</span><span class="sxs-lookup"><span data-stu-id="77dec-145">By default, `Get-Package` only returns the newest available version.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-146">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="77dec-146">-Destination</span></span>

<span data-ttu-id="77dec-147">Hiermee geeft u het pad op naar een map die uitgepakte pakket bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="77dec-147">Specifies the path to a directory that contains extracted package files.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-148">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="77dec-148">-ExcludeVersion</span></span>

<span data-ttu-id="77dec-149">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="77dec-149">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-150">-Force</span><span class="sxs-lookup"><span data-stu-id="77dec-150">-Force</span></span>

<span data-ttu-id="77dec-151">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="77dec-151">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-152">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="77dec-152">-ForceBootstrap</span></span>

<span data-ttu-id="77dec-153">Geeft aan `Get-Package` dat **Package Management** automatisch de pakket provider installeert.</span><span class="sxs-lookup"><span data-stu-id="77dec-153">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-154">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="77dec-154">-InstallUpdate</span></span>

<span data-ttu-id="77dec-155">Geeft aan dat met deze cmdlet updates worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="77dec-155">Indicates that this cmdlet installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-156">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="77dec-156">-MaximumVersion</span></span>

<span data-ttu-id="77dec-157">Hiermee geeft u de maximale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="77dec-157">Specifies the maximum package version that you want to find.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-158">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="77dec-158">-MinimumVersion</span></span>

<span data-ttu-id="77dec-159">Hiermee geeft u de minimale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="77dec-159">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="77dec-160">Als er een hogere versie beschikbaar is, wordt die versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="77dec-160">If a higher version is available, that version is returned.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-161">-Name</span><span class="sxs-lookup"><span data-stu-id="77dec-161">-Name</span></span>

<span data-ttu-id="77dec-162">Hiermee geeft u een of meer pakket namen of pakket namen met Joker tekens op.</span><span class="sxs-lookup"><span data-stu-id="77dec-162">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="77dec-163">Scheid meerdere pakket namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="77dec-163">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="77dec-164">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="77dec-164">-NoPathUpdate</span></span>

<span data-ttu-id="77dec-165">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="77dec-165">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="77dec-166">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="77dec-166">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-167">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="77dec-167">-PackageManagementProvider</span></span>

<span data-ttu-id="77dec-168">Hiermee geeft u de naam van een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="77dec-168">Specifies the name of a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-169">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="77dec-169">-ProviderName</span></span>

<span data-ttu-id="77dec-170">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="77dec-170">Specifies one or more package provider names.</span></span> <span data-ttu-id="77dec-171">Scheid meerdere pakket provider namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="77dec-171">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="77dec-172">Gebruiken `Get-PackageProvider` om een lijst met beschik bare pakket providers op te halen.</span><span class="sxs-lookup"><span data-stu-id="77dec-172">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-173">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="77dec-173">-RequiredVersion</span></span>

<span data-ttu-id="77dec-174">Hiermee geeft u de exacte versie van het pakket op dat moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="77dec-174">Specifies the exact version of the package to find.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-175">-Bereik</span><span class="sxs-lookup"><span data-stu-id="77dec-175">-Scope</span></span>

<span data-ttu-id="77dec-176">Hiermee geeft u het zoek bereik voor het pakket op.</span><span class="sxs-lookup"><span data-stu-id="77dec-176">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-177">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="77dec-177">-SkipDependencies</span></span>

<span data-ttu-id="77dec-178">Switch waarmee wordt aangegeven dat er geen pakket afhankelijkheden moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="77dec-178">Switch that specifies to skip finding any package dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-179">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="77dec-179">-SkipPublisherCheck</span></span>

<span data-ttu-id="77dec-180">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="77dec-180">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="77dec-181">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="77dec-181">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-182">-Type</span><span class="sxs-lookup"><span data-stu-id="77dec-182">-Type</span></span>

<span data-ttu-id="77dec-183">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.</span><span class="sxs-lookup"><span data-stu-id="77dec-183">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77dec-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77dec-184">CommonParameters</span></span>

<span data-ttu-id="77dec-185">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77dec-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77dec-186">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="77dec-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77dec-187">INVOER</span><span class="sxs-lookup"><span data-stu-id="77dec-187">INPUTS</span></span>

## <span data-ttu-id="77dec-188">UITVOER</span><span class="sxs-lookup"><span data-stu-id="77dec-188">OUTPUTS</span></span>

### <span data-ttu-id="77dec-189">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="77dec-189">SoftwareIdentity[]</span></span>

## <span data-ttu-id="77dec-190">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="77dec-190">NOTES</span></span>

<span data-ttu-id="77dec-191">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="77dec-191">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="77dec-192">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="77dec-192">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="77dec-193">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="77dec-193">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="77dec-194">`Get-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="77dec-194">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77dec-195">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="77dec-195">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="77dec-196">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="77dec-196">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="77dec-197">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="77dec-197">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="77dec-198">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="77dec-198">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="77dec-199">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="77dec-199">RELATED LINKS</span></span>

[<span data-ttu-id="77dec-200">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="77dec-200">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="77dec-201">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="77dec-201">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="77dec-202">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="77dec-202">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="77dec-203">Get-Help</span><span class="sxs-lookup"><span data-stu-id="77dec-203">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="77dec-204">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="77dec-204">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="77dec-205">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="77dec-205">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="77dec-206">Install-Package</span><span class="sxs-lookup"><span data-stu-id="77dec-206">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="77dec-207">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="77dec-207">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="77dec-208">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="77dec-208">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="77dec-209">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="77dec-209">Uninstall-Package</span></span>](Uninstall-Package.md)
