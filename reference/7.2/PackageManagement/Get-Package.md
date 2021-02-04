---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: c26365eb5b4833c4982fa54e742521cf72307e99
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889494"
---
# <span data-ttu-id="e1af1-102">Get-Package</span><span class="sxs-lookup"><span data-stu-id="e1af1-102">Get-Package</span></span>

## <span data-ttu-id="e1af1-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e1af1-103">SYNOPSIS</span></span>
<span data-ttu-id="e1af1-104">Retourneert een lijst met alle software pakketten die zijn geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="e1af1-104">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="e1af1-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e1af1-105">SYNTAX</span></span>

### <span data-ttu-id="e1af1-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="e1af1-106">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="e1af1-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e1af1-107">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="e1af1-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e1af1-108">DESCRIPTION</span></span>

<span data-ttu-id="e1af1-109">De `Get-Package` cmdlet retourneert een lijst met alle software pakketten op de lokale computer die is geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="e1af1-109">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="e1af1-110">U kunt uitvoeren `Get-Package` op externe computers door deze uit te voeren als onderdeel van een `Invoke-Command` `Enter-PSSession` opdracht of script.</span><span class="sxs-lookup"><span data-stu-id="e1af1-110">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="e1af1-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e1af1-111">EXAMPLES</span></span>

### <span data-ttu-id="e1af1-112">Voor beeld 1: alle geïnstalleerde pakketten ophalen</span><span class="sxs-lookup"><span data-stu-id="e1af1-112">Example 1: Get all installed packages</span></span>

<span data-ttu-id="e1af1-113">De `Get-Package` cmdlet haalt alle pakketten op die zijn geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e1af1-113">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="e1af1-114">Voor beeld 2: pakketten ophalen die zijn geïnstalleerd op een externe computer</span><span class="sxs-lookup"><span data-stu-id="e1af1-114">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="e1af1-115">Met deze opdracht wordt een lijst opgehaald met pakketten die zijn geïnstalleerd door **Package Management** op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="e1af1-115">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="e1af1-116">Met deze opdracht wordt u gevraagd het wacht woord van de opgegeven gebruiker op te geven.</span><span class="sxs-lookup"><span data-stu-id="e1af1-116">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="e1af1-117">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om een externe computer op te geven, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="e1af1-117">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="e1af1-118">De **referentie** parameter bevat een domein-en gebruikers naam met machtigingen voor het uitvoeren van opdrachten op de computer.</span><span class="sxs-lookup"><span data-stu-id="e1af1-118">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="e1af1-119">De para meter **script Block** voert de `Get-Package` cmdlet uit op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="e1af1-119">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="e1af1-120">Voor beeld 3: pakketten voor een opgegeven provider ophalen</span><span class="sxs-lookup"><span data-stu-id="e1af1-120">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="e1af1-121">Met deze opdracht worden software pakketten die zijn geïnstalleerd op de lokale computer van een specifieke provider opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e1af1-121">This command gets software packages installed on the local computer from a specific provider.</span></span>

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

<span data-ttu-id="e1af1-122">`Get-Package` maakt gebruik van de para meter **ProviderName** om een specifieke provider op te geven, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="e1af1-122">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="e1af1-123">In de para meter **all-versions** wordt elke geïnstalleerde versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e1af1-123">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="e1af1-124">Voor beeld 4: een exacte versie van een specifiek pakket ophalen</span><span class="sxs-lookup"><span data-stu-id="e1af1-124">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="e1af1-125">Met deze opdracht wordt een specifieke versie van een geïnstalleerd pakket opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e1af1-125">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="e1af1-126">Er kan meer dan één versie van een pakket worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e1af1-126">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="e1af1-127">`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="e1af1-127">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="e1af1-128">De para meter **ProviderName** specificeert de provider, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="e1af1-128">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="e1af1-129">De **vereiste-versie** parameter geeft een geïnstalleerde versie op.</span><span class="sxs-lookup"><span data-stu-id="e1af1-129">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="e1af1-130">Voor beeld 5: een pakket verwijderen</span><span class="sxs-lookup"><span data-stu-id="e1af1-130">Example 5: Uninstall a package</span></span>

<span data-ttu-id="e1af1-131">In dit voor beeld worden pakket gegevens opgehaald en wordt het pakket vervolgens verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e1af1-131">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="e1af1-132">`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **posh-Git**.</span><span class="sxs-lookup"><span data-stu-id="e1af1-132">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="e1af1-133">De **RequiredVersion** -para meter is een specifieke versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="e1af1-133">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="e1af1-134">Het object wordt vanuit de pijp lijn naar de `Uninstall-Package` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="e1af1-134">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="e1af1-135">`Uninstall-Package` Hiermee verwijdert u het pakket.</span><span class="sxs-lookup"><span data-stu-id="e1af1-135">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="e1af1-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1af1-136">PARAMETERS</span></span>

### <span data-ttu-id="e1af1-137">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="e1af1-137">-AllowClobber</span></span>

<span data-ttu-id="e1af1-138">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="e1af1-138">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="e1af1-139">Overschrijft bestaande opdrachten die dezelfde naam hebben als opdrachten die door een module worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e1af1-139">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

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

### <span data-ttu-id="e1af1-140">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="e1af1-140">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="e1af1-141">Bevat pakketten die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="e1af1-141">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="e1af1-142">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="e1af1-142">-AllVersions</span></span>

<span data-ttu-id="e1af1-143">Hiermee wordt aangegeven dat `Get-Package` alle beschik bare versies van het pakket worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e1af1-143">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="e1af1-144">`Get-Package`Retourneert standaard alleen de nieuwste beschik bare versie.</span><span class="sxs-lookup"><span data-stu-id="e1af1-144">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="e1af1-145">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="e1af1-145">-Destination</span></span>

<span data-ttu-id="e1af1-146">Hiermee geeft u het pad op naar een map die uitgepakte pakket bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="e1af1-146">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="e1af1-147">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="e1af1-147">-ExcludeVersion</span></span>

<span data-ttu-id="e1af1-148">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="e1af1-148">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="e1af1-149">-Force</span><span class="sxs-lookup"><span data-stu-id="e1af1-149">-Force</span></span>

<span data-ttu-id="e1af1-150">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="e1af1-150">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e1af1-151">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="e1af1-151">-ForceBootstrap</span></span>

<span data-ttu-id="e1af1-152">Geeft aan `Get-Package` dat **Package Management** automatisch de pakket provider installeert.</span><span class="sxs-lookup"><span data-stu-id="e1af1-152">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="e1af1-153">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="e1af1-153">-InstallUpdate</span></span>

<span data-ttu-id="e1af1-154">Geeft aan dat met deze cmdlet updates worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e1af1-154">Indicates that this cmdlet installs updates.</span></span>

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

### <span data-ttu-id="e1af1-155">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e1af1-155">-MaximumVersion</span></span>

<span data-ttu-id="e1af1-156">Hiermee geeft u de maximale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="e1af1-156">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="e1af1-157">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e1af1-157">-MinimumVersion</span></span>

<span data-ttu-id="e1af1-158">Hiermee geeft u de minimale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="e1af1-158">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="e1af1-159">Als er een hogere versie beschikbaar is, wordt die versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e1af1-159">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="e1af1-160">-Name</span><span class="sxs-lookup"><span data-stu-id="e1af1-160">-Name</span></span>

<span data-ttu-id="e1af1-161">Hiermee geeft u een of meer pakket namen of pakket namen met Joker tekens op.</span><span class="sxs-lookup"><span data-stu-id="e1af1-161">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="e1af1-162">Scheid meerdere pakket namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="e1af1-162">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="e1af1-163">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="e1af1-163">-NoPathUpdate</span></span>

<span data-ttu-id="e1af1-164">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1af1-164">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="e1af1-165">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="e1af1-165">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

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

### <span data-ttu-id="e1af1-166">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="e1af1-166">-PackageManagementProvider</span></span>

<span data-ttu-id="e1af1-167">Hiermee geeft u de naam van een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="e1af1-167">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="e1af1-168">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="e1af1-168">-ProviderName</span></span>

<span data-ttu-id="e1af1-169">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="e1af1-169">Specifies one or more package provider names.</span></span> <span data-ttu-id="e1af1-170">Scheid meerdere pakket provider namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="e1af1-170">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="e1af1-171">Gebruiken `Get-PackageProvider` om een lijst met beschik bare pakket providers op te halen.</span><span class="sxs-lookup"><span data-stu-id="e1af1-171">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="e1af1-172">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e1af1-172">-RequiredVersion</span></span>

<span data-ttu-id="e1af1-173">Hiermee geeft u de exacte versie van het pakket op dat moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="e1af1-173">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="e1af1-174">-Bereik</span><span class="sxs-lookup"><span data-stu-id="e1af1-174">-Scope</span></span>

<span data-ttu-id="e1af1-175">Hiermee geeft u het zoek bereik voor het pakket op.</span><span class="sxs-lookup"><span data-stu-id="e1af1-175">Specifies the search scope for the package.</span></span>

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

### <span data-ttu-id="e1af1-176">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="e1af1-176">-SkipDependencies</span></span>

<span data-ttu-id="e1af1-177">Switch waarmee wordt aangegeven dat er geen pakket afhankelijkheden moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="e1af1-177">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="e1af1-178">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="e1af1-178">-SkipPublisherCheck</span></span>

<span data-ttu-id="e1af1-179">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="e1af1-179">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="e1af1-180">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="e1af1-180">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="e1af1-181">-Type</span><span class="sxs-lookup"><span data-stu-id="e1af1-181">-Type</span></span>

<span data-ttu-id="e1af1-182">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.</span><span class="sxs-lookup"><span data-stu-id="e1af1-182">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="e1af1-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1af1-183">CommonParameters</span></span>

<span data-ttu-id="e1af1-184">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e1af1-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1af1-185">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e1af1-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1af1-186">INVOER</span><span class="sxs-lookup"><span data-stu-id="e1af1-186">INPUTS</span></span>

## <span data-ttu-id="e1af1-187">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e1af1-187">OUTPUTS</span></span>

### <span data-ttu-id="e1af1-188">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="e1af1-188">SoftwareIdentity[]</span></span>

## <span data-ttu-id="e1af1-189">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e1af1-189">NOTES</span></span>

<span data-ttu-id="e1af1-190">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1af1-190">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="e1af1-191">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="e1af1-191">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="e1af1-192">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="e1af1-192">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="e1af1-193">`Get-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="e1af1-193">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1af1-194">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="e1af1-194">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="e1af1-195">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e1af1-195">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="e1af1-196">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="e1af1-196">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="e1af1-197">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e1af1-197">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="e1af1-198">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e1af1-198">RELATED LINKS</span></span>

[<span data-ttu-id="e1af1-199">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e1af1-199">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="e1af1-200">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e1af1-200">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="e1af1-201">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="e1af1-201">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="e1af1-202">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e1af1-202">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="e1af1-203">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e1af1-203">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="e1af1-204">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e1af1-204">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="e1af1-205">Install-Package</span><span class="sxs-lookup"><span data-stu-id="e1af1-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="e1af1-206">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="e1af1-206">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="e1af1-207">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="e1af1-207">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="e1af1-208">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="e1af1-208">Uninstall-Package</span></span>](Uninstall-Package.md)