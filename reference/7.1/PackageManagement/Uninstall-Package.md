---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 4da97d9643483db0eae4fc7d34e0e6997d16bd04
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250883"
---
# <span data-ttu-id="3e279-103">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="3e279-103">Uninstall-Package</span></span>

## <span data-ttu-id="3e279-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3e279-104">SYNOPSIS</span></span>
<span data-ttu-id="3e279-105">Hiermee verwijdert u een of meer software pakketten.</span><span class="sxs-lookup"><span data-stu-id="3e279-105">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="3e279-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3e279-106">SYNTAX</span></span>

### <span data-ttu-id="3e279-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="3e279-107">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3e279-108">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="3e279-108">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3e279-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="3e279-109">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="3e279-110">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="3e279-110">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="3e279-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="3e279-111">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="3e279-112">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="3e279-112">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="3e279-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3e279-113">DESCRIPTION</span></span>

<span data-ttu-id="3e279-114">De `Uninstall-Package` cmdlet verwijdert een of meer software pakketten van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3e279-114">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="3e279-115">Gebruik de cmdlet om geïnstalleerde pakketten te vinden `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e279-115">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="3e279-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3e279-116">EXAMPLES</span></span>

### <span data-ttu-id="3e279-117">Voor beeld 1: een pakket verwijderen</span><span class="sxs-lookup"><span data-stu-id="3e279-117">Example 1: Uninstall a package</span></span>

<span data-ttu-id="3e279-118">De `Uninstall-Package` cmdlet verwijdert het verwijderen van pakketten.</span><span class="sxs-lookup"><span data-stu-id="3e279-118">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="3e279-119">De para meter **name** geeft het pakket op dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3e279-119">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="3e279-120">Als er meerdere versies van een pakket zijn geïnstalleerd, wordt de nieuwste versie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3e279-120">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="3e279-121">Voor beeld 2: de pijp lijn gebruiken om een pakket te verwijderen</span><span class="sxs-lookup"><span data-stu-id="3e279-121">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="3e279-122">`Get-Package` zoekt een specifiek pakket en verzendt het **SoftwareIdentity** -object omlaag in de pijp lijn naar de `Uninsall-Package` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e279-122">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="3e279-123">De `Get-Package` cmdlet maakt gebruik van de para meters **name** en **RequiredVersion** om een pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="3e279-123">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="3e279-124">Er wordt een **SoftwareIdentity** -object verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="3e279-124">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="3e279-125">De `Uninstall-Package` cmdlet ontvangt het object als een **input object** en verwijdert het pakket.</span><span class="sxs-lookup"><span data-stu-id="3e279-125">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="3e279-126">Als alternatief `Uninstall-Package` kan de cmdlet een waarde opgeven voor de para meter **input object** :</span><span class="sxs-lookup"><span data-stu-id="3e279-126">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="3e279-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e279-127">PARAMETERS</span></span>

### <span data-ttu-id="3e279-128">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="3e279-128">-AllowClobber</span></span>

<span data-ttu-id="3e279-129">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="3e279-129">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="3e279-130">Overschrijft bestaande opdrachten die dezelfde naam hebben als de opdrachten die worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3e279-130">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-131">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="3e279-131">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="3e279-132">Toestaan dat pakketten die zijn gemarkeerd als Prerelease, worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3e279-132">Allows packages marked as prerelease to be uninstalled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-133">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="3e279-133">-AllVersions</span></span>

<span data-ttu-id="3e279-134">Geeft aan dat met deze cmdlet alle versies van het pakket worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3e279-134">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="3e279-135">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="3e279-135">-Destination</span></span>

<span data-ttu-id="3e279-136">Hiermee geeft u een teken reeks van het pad naar het invoer object.</span><span class="sxs-lookup"><span data-stu-id="3e279-136">Specifies a string of the path to the input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-137">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="3e279-137">-ExcludeVersion</span></span>

<span data-ttu-id="3e279-138">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="3e279-138">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-139">-Force</span><span class="sxs-lookup"><span data-stu-id="3e279-139">-Force</span></span>

<span data-ttu-id="3e279-140">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="3e279-140">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="3e279-141">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="3e279-141">-ForceBootstrap</span></span>

<span data-ttu-id="3e279-142">Forceert **Package Management** de pakket provider automatisch te installeren voor het opgegeven pakket.</span><span class="sxs-lookup"><span data-stu-id="3e279-142">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="3e279-143">-Input object</span><span class="sxs-lookup"><span data-stu-id="3e279-143">-InputObject</span></span>

<span data-ttu-id="3e279-144">Hiermee wordt een pijplijn invoer geaccepteerd waarmee het **SoftwareIdentity** -object van het pakket wordt opgegeven vanuit de `Get-Package` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e279-144">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="3e279-145">**Input object** accepteert het **SoftwareIdentity** -object als een `Get-Package` waarde of een variabele die het object bevat.</span><span class="sxs-lookup"><span data-stu-id="3e279-145">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-146">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="3e279-146">-InstallUpdate</span></span>

<span data-ttu-id="3e279-147">Hiermee wordt aangegeven dat `Uninstall-Package` updates worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3e279-147">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3e279-148">-MaximumVersion</span></span>

<span data-ttu-id="3e279-149">Hiermee geeft u de Maxi maal toegestane pakket versie op die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3e279-149">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="3e279-150">Als u deze para meter niet opgeeft, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3e279-150">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3e279-151">-MinimumVersion</span></span>

<span data-ttu-id="3e279-152">Hiermee geeft u de mini maal toegestane pakket versie op die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3e279-152">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="3e279-153">Als u deze para meter niet toevoegt, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="3e279-153">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-154">-Name</span><span class="sxs-lookup"><span data-stu-id="3e279-154">-Name</span></span>

<span data-ttu-id="3e279-155">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="3e279-155">Specifies one or more package names.</span></span> <span data-ttu-id="3e279-156">Meerdere pakket namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="3e279-156">Multiple package names must be separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-157">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="3e279-157">-NoPathUpdate</span></span>

<span data-ttu-id="3e279-158">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e279-158">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="3e279-159">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e279-159">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-160">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="3e279-160">-PackageManagementProvider</span></span>

<span data-ttu-id="3e279-161">Hiermee geeft u de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="3e279-161">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-162">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="3e279-162">-ProviderName</span></span>

<span data-ttu-id="3e279-163">Hiermee geeft u een of meer pakket provider namen op om te zoeken naar pakketten.</span><span class="sxs-lookup"><span data-stu-id="3e279-163">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="3e279-164">U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="3e279-164">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3e279-165">-RequiredVersion</span></span>

<span data-ttu-id="3e279-166">Hiermee geeft u de exacte toegestane versie van het pakket dat u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3e279-166">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="3e279-167">Als u deze para meter niet toevoegt, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="3e279-167">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-168">-Bereik</span><span class="sxs-lookup"><span data-stu-id="3e279-168">-Scope</span></span>

<span data-ttu-id="3e279-169">Hiermee geeft u het bereik op waarvoor het pakket moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3e279-169">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="3e279-170">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="3e279-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3e279-171">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="3e279-171">CurrentUser</span></span>
- <span data-ttu-id="3e279-172">AllUsers</span><span class="sxs-lookup"><span data-stu-id="3e279-172">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-173">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="3e279-173">-SkipDependencies</span></span>

<span data-ttu-id="3e279-174">Hiermee wordt de verwijdering van software-afhankelijkheden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3e279-174">Skips the uninstallation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-175">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="3e279-175">-SkipPublisherCheck</span></span>

<span data-ttu-id="3e279-176">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="3e279-176">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="3e279-177">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="3e279-177">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-178">-Type</span><span class="sxs-lookup"><span data-stu-id="3e279-178">-Type</span></span>

<span data-ttu-id="3e279-179">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of beide.</span><span class="sxs-lookup"><span data-stu-id="3e279-179">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="3e279-180">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="3e279-180">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3e279-181">Module</span><span class="sxs-lookup"><span data-stu-id="3e279-181">Module</span></span>
- <span data-ttu-id="3e279-182">Script</span><span class="sxs-lookup"><span data-stu-id="3e279-182">Script</span></span>
- <span data-ttu-id="3e279-183">Alles</span><span class="sxs-lookup"><span data-stu-id="3e279-183">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3e279-184">-Confirm</span></span>

<span data-ttu-id="3e279-185">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3e279-185">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3e279-186">-WhatIf</span></span>

<span data-ttu-id="3e279-187">Laat zien wat er zou gebeuren als de `Uninstall-Package` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3e279-187">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="3e279-188">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3e279-188">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e279-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e279-189">CommonParameters</span></span>

<span data-ttu-id="3e279-190">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e279-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e279-191">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3e279-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e279-192">INVOER</span><span class="sxs-lookup"><span data-stu-id="3e279-192">INPUTS</span></span>

### <span data-ttu-id="3e279-193">`Uninstall-Package` Hiermee worden **SoftwareIdentity** -objecten van de pijp lijn geaccepteerd als invoer.</span><span class="sxs-lookup"><span data-stu-id="3e279-193">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="3e279-194">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3e279-194">OUTPUTS</span></span>

### <span data-ttu-id="3e279-195">`Uninstall-Package` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3e279-195">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="3e279-196">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3e279-196">NOTES</span></span>

<span data-ttu-id="3e279-197">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e279-197">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="3e279-198">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="3e279-198">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="3e279-199">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="3e279-199">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="3e279-200">`Uninstall-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="3e279-200">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="3e279-201">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3e279-201">RELATED LINKS</span></span>

[<span data-ttu-id="3e279-202">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="3e279-202">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="3e279-203">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="3e279-203">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="3e279-204">Get-Package</span><span class="sxs-lookup"><span data-stu-id="3e279-204">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="3e279-205">Install-Package</span><span class="sxs-lookup"><span data-stu-id="3e279-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="3e279-206">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="3e279-206">Save-Package</span></span>](Save-Package.md)

