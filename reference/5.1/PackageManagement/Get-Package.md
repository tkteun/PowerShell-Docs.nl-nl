---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: aad8b6f033674c65b4cc56708e09e5320bb046dd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250283"
---
# <span data-ttu-id="f0328-103">Get-Package</span><span class="sxs-lookup"><span data-stu-id="f0328-103">Get-Package</span></span>

## <span data-ttu-id="f0328-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f0328-104">SYNOPSIS</span></span>
<span data-ttu-id="f0328-105">Retourneert een lijst met alle software pakketten die zijn geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="f0328-105">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="f0328-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f0328-106">SYNTAX</span></span>

### <span data-ttu-id="f0328-107">MSI</span><span class="sxs-lookup"><span data-stu-id="f0328-107">msi</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-AdditionalArguments <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f0328-108">Programma's</span><span class="sxs-lookup"><span data-stu-id="f0328-108">Programs</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-IncludeWindowsInstaller] [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="f0328-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="f0328-109">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="f0328-110">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f0328-110">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="f0328-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f0328-111">DESCRIPTION</span></span>

<span data-ttu-id="f0328-112">De `Get-Package` cmdlet retourneert een lijst met alle software pakketten op de lokale computer die is geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="f0328-112">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="f0328-113">U kunt uitvoeren `Get-Package` op externe computers door deze uit te voeren als onderdeel van een `Invoke-Command` `Enter-PSSession` opdracht of script.</span><span class="sxs-lookup"><span data-stu-id="f0328-113">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="f0328-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f0328-114">EXAMPLES</span></span>

### <span data-ttu-id="f0328-115">Voor beeld 1: alle geïnstalleerde pakketten ophalen</span><span class="sxs-lookup"><span data-stu-id="f0328-115">Example 1: Get all installed packages</span></span>

<span data-ttu-id="f0328-116">De `Get-Package` cmdlet haalt alle pakketten op die zijn geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f0328-116">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="f0328-117">Voor beeld 2: pakketten ophalen die zijn geïnstalleerd op een externe computer</span><span class="sxs-lookup"><span data-stu-id="f0328-117">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="f0328-118">Met deze opdracht wordt een lijst opgehaald met pakketten die zijn geïnstalleerd door **Package Management** op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f0328-118">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="f0328-119">Met deze opdracht wordt u gevraagd het wacht woord van de opgegeven gebruiker op te geven.</span><span class="sxs-lookup"><span data-stu-id="f0328-119">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="f0328-120">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om een externe computer op te geven, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="f0328-120">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="f0328-121">De **referentie** parameter bevat een domein-en gebruikers naam met machtigingen voor het uitvoeren van opdrachten op de computer.</span><span class="sxs-lookup"><span data-stu-id="f0328-121">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="f0328-122">De para meter **script Block** voert de `Get-Package` cmdlet uit op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f0328-122">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="f0328-123">Voor beeld 3: pakketten voor een opgegeven provider ophalen</span><span class="sxs-lookup"><span data-stu-id="f0328-123">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="f0328-124">Met deze opdracht worden software pakketten die zijn geïnstalleerd op de lokale computer van een specifieke provider opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0328-124">This command gets software packages installed on the local computer from a specific provider.</span></span>

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

<span data-ttu-id="f0328-125">`Get-Package` maakt gebruik van de para meter **ProviderName** om een specifieke provider op te geven, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="f0328-125">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="f0328-126">In de para meter **all-versions** wordt elke geïnstalleerde versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f0328-126">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="f0328-127">Voor beeld 4: een exacte versie van een specifiek pakket ophalen</span><span class="sxs-lookup"><span data-stu-id="f0328-127">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="f0328-128">Met deze opdracht wordt een specifieke versie van een geïnstalleerd pakket opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f0328-128">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="f0328-129">Er kan meer dan één versie van een pakket worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f0328-129">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="f0328-130">`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="f0328-130">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="f0328-131">De para meter **ProviderName** specificeert de provider, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="f0328-131">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="f0328-132">De **vereiste-versie** parameter geeft een geïnstalleerde versie op.</span><span class="sxs-lookup"><span data-stu-id="f0328-132">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="f0328-133">Voor beeld 5: een pakket verwijderen</span><span class="sxs-lookup"><span data-stu-id="f0328-133">Example 5: Uninstall a package</span></span>

<span data-ttu-id="f0328-134">In dit voor beeld worden pakket gegevens opgehaald en wordt het pakket vervolgens verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f0328-134">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="f0328-135">`Get-Package` maakt gebruik van de para meter **name** om de naam van het pakket op te geven, **posh-Git**.</span><span class="sxs-lookup"><span data-stu-id="f0328-135">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="f0328-136">De **RequiredVersion** -para meter is een specifieke versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="f0328-136">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="f0328-137">Het object wordt vanuit de pijp lijn naar de `Uninstall-Package` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f0328-137">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="f0328-138">`Uninstall-Package` Hiermee verwijdert u het pakket.</span><span class="sxs-lookup"><span data-stu-id="f0328-138">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="f0328-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0328-139">PARAMETERS</span></span>

### <span data-ttu-id="f0328-140">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="f0328-140">-AllowClobber</span></span>

<span data-ttu-id="f0328-141">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f0328-141">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="f0328-142">Overschrijft bestaande opdrachten die dezelfde naam hebben als opdrachten die door een module worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f0328-142">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

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

### <span data-ttu-id="f0328-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="f0328-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="f0328-144">Bevat pakketten die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="f0328-144">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="f0328-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="f0328-145">-AllVersions</span></span>

<span data-ttu-id="f0328-146">Hiermee wordt aangegeven dat `Get-Package` alle beschik bare versies van het pakket worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f0328-146">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="f0328-147">`Get-Package`Retourneert standaard alleen de nieuwste beschik bare versie.</span><span class="sxs-lookup"><span data-stu-id="f0328-147">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="f0328-148">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="f0328-148">-Destination</span></span>

<span data-ttu-id="f0328-149">Hiermee geeft u het pad op naar een map die uitgepakte pakket bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="f0328-149">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="f0328-150">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="f0328-150">-ExcludeVersion</span></span>

<span data-ttu-id="f0328-151">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="f0328-151">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="f0328-152">-Force</span><span class="sxs-lookup"><span data-stu-id="f0328-152">-Force</span></span>

<span data-ttu-id="f0328-153">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="f0328-153">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f0328-154">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="f0328-154">-ForceBootstrap</span></span>

<span data-ttu-id="f0328-155">Geeft aan `Get-Package` dat **Package Management** automatisch de pakket provider installeert.</span><span class="sxs-lookup"><span data-stu-id="f0328-155">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="f0328-156">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="f0328-156">-InstallUpdate</span></span>

<span data-ttu-id="f0328-157">Geeft aan dat met deze cmdlet updates worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f0328-157">Indicates that this cmdlet installs updates.</span></span>

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

### <span data-ttu-id="f0328-158">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f0328-158">-MaximumVersion</span></span>

<span data-ttu-id="f0328-159">Hiermee geeft u de maximale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="f0328-159">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="f0328-160">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f0328-160">-MinimumVersion</span></span>

<span data-ttu-id="f0328-161">Hiermee geeft u de minimale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="f0328-161">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="f0328-162">Als er een hogere versie beschikbaar is, wordt die versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f0328-162">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="f0328-163">-Name</span><span class="sxs-lookup"><span data-stu-id="f0328-163">-Name</span></span>

<span data-ttu-id="f0328-164">Hiermee geeft u een of meer pakket namen of pakket namen met Joker tekens op.</span><span class="sxs-lookup"><span data-stu-id="f0328-164">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="f0328-165">Scheid meerdere pakket namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="f0328-165">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="f0328-166">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="f0328-166">-NoPathUpdate</span></span>

<span data-ttu-id="f0328-167">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0328-167">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="f0328-168">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="f0328-168">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

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

### <span data-ttu-id="f0328-169">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="f0328-169">-PackageManagementProvider</span></span>

<span data-ttu-id="f0328-170">Hiermee geeft u de naam van een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="f0328-170">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="f0328-171">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="f0328-171">-ProviderName</span></span>

<span data-ttu-id="f0328-172">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="f0328-172">Specifies one or more package provider names.</span></span> <span data-ttu-id="f0328-173">Scheid meerdere pakket provider namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="f0328-173">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="f0328-174">Gebruiken `Get-PackageProvider` om een lijst met beschik bare pakket providers op te halen.</span><span class="sxs-lookup"><span data-stu-id="f0328-174">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="f0328-175">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f0328-175">-RequiredVersion</span></span>

<span data-ttu-id="f0328-176">Hiermee geeft u de exacte versie van het pakket op dat moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="f0328-176">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="f0328-177">-Bereik</span><span class="sxs-lookup"><span data-stu-id="f0328-177">-Scope</span></span>

<span data-ttu-id="f0328-178">Hiermee geeft u het zoek bereik voor het pakket op.</span><span class="sxs-lookup"><span data-stu-id="f0328-178">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet, PowerShellGet
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0328-179">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="f0328-179">-SkipDependencies</span></span>

<span data-ttu-id="f0328-180">Switch waarmee wordt aangegeven dat er geen pakket afhankelijkheden moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="f0328-180">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="f0328-181">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="f0328-181">-SkipPublisherCheck</span></span>

<span data-ttu-id="f0328-182">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="f0328-182">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="f0328-183">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="f0328-183">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="f0328-184">-Type</span><span class="sxs-lookup"><span data-stu-id="f0328-184">-Type</span></span>

<span data-ttu-id="f0328-185">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.</span><span class="sxs-lookup"><span data-stu-id="f0328-185">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="f0328-186">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="f0328-186">-AdditionalArguments</span></span>

<span data-ttu-id="f0328-187">Hiermee geeft u aanvullende argumenten op.</span><span class="sxs-lookup"><span data-stu-id="f0328-187">Specifies additional arguments.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0328-188">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="f0328-188">-IncludeSystemComponent</span></span>

<span data-ttu-id="f0328-189">Geeft aan dat deze cmdlet systeem onderdelen bevat in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="f0328-189">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0328-190">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="f0328-190">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="f0328-191">Geeft aan dat deze cmdlet de Windows Installer in de resultaten bevat.</span><span class="sxs-lookup"><span data-stu-id="f0328-191">Indicates that this cmdlet includes the Windows Installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0328-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0328-192">CommonParameters</span></span>

<span data-ttu-id="f0328-193">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0328-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0328-194">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f0328-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0328-195">INVOER</span><span class="sxs-lookup"><span data-stu-id="f0328-195">INPUTS</span></span>

## <span data-ttu-id="f0328-196">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f0328-196">OUTPUTS</span></span>

### <span data-ttu-id="f0328-197">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="f0328-197">SoftwareIdentity[]</span></span>

## <span data-ttu-id="f0328-198">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f0328-198">NOTES</span></span>

<span data-ttu-id="f0328-199">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0328-199">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="f0328-200">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="f0328-200">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="f0328-201">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="f0328-201">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="f0328-202">`Get-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="f0328-202">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="f0328-203">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f0328-203">RELATED LINKS</span></span>

[<span data-ttu-id="f0328-204">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="f0328-204">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="f0328-205">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f0328-205">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="f0328-206">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="f0328-206">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="f0328-207">Get-Help</span><span class="sxs-lookup"><span data-stu-id="f0328-207">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="f0328-208">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="f0328-208">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="f0328-209">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f0328-209">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="f0328-210">Install-Package</span><span class="sxs-lookup"><span data-stu-id="f0328-210">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="f0328-211">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="f0328-211">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="f0328-212">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="f0328-212">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="f0328-213">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="f0328-213">Uninstall-Package</span></span>](Uninstall-Package.md)
