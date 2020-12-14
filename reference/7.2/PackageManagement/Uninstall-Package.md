---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: ca12f7f2118a004a6f474ae8174b04f9dbb9444d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705665"
---
# <span data-ttu-id="2f809-102">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="2f809-102">Uninstall-Package</span></span>

## <span data-ttu-id="2f809-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2f809-103">SYNOPSIS</span></span>
<span data-ttu-id="2f809-104">Hiermee verwijdert u een of meer software pakketten.</span><span class="sxs-lookup"><span data-stu-id="2f809-104">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="2f809-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2f809-105">SYNTAX</span></span>

### <span data-ttu-id="2f809-106">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="2f809-106">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2f809-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="2f809-107">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2f809-108">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="2f809-108">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="2f809-109">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="2f809-109">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="2f809-110">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="2f809-110">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="2f809-111">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="2f809-111">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="2f809-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2f809-112">DESCRIPTION</span></span>

<span data-ttu-id="2f809-113">De `Uninstall-Package` cmdlet verwijdert een of meer software pakketten van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2f809-113">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="2f809-114">Gebruik de cmdlet om geïnstalleerde pakketten te vinden `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="2f809-114">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="2f809-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2f809-115">EXAMPLES</span></span>

### <span data-ttu-id="2f809-116">Voor beeld 1: een pakket verwijderen</span><span class="sxs-lookup"><span data-stu-id="2f809-116">Example 1: Uninstall a package</span></span>

<span data-ttu-id="2f809-117">De `Uninstall-Package` cmdlet verwijdert het verwijderen van pakketten.</span><span class="sxs-lookup"><span data-stu-id="2f809-117">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="2f809-118">De para meter **name** geeft het pakket op dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f809-118">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="2f809-119">Als er meerdere versies van een pakket zijn geïnstalleerd, wordt de nieuwste versie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f809-119">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="2f809-120">Voor beeld 2: de pijp lijn gebruiken om een pakket te verwijderen</span><span class="sxs-lookup"><span data-stu-id="2f809-120">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="2f809-121">`Get-Package` zoekt een specifiek pakket en verzendt het **SoftwareIdentity** -object omlaag in de pijp lijn naar de `Uninsall-Package` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f809-121">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="2f809-122">De `Get-Package` cmdlet maakt gebruik van de para meters **name** en **RequiredVersion** om een pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="2f809-122">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="2f809-123">Er wordt een **SoftwareIdentity** -object verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="2f809-123">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="2f809-124">De `Uninstall-Package` cmdlet ontvangt het object als een **input object** en verwijdert het pakket.</span><span class="sxs-lookup"><span data-stu-id="2f809-124">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="2f809-125">Als alternatief `Uninstall-Package` kan de cmdlet een waarde opgeven voor de para meter **input object** :</span><span class="sxs-lookup"><span data-stu-id="2f809-125">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="2f809-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f809-126">PARAMETERS</span></span>

### <span data-ttu-id="2f809-127">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="2f809-127">-AllowClobber</span></span>

<span data-ttu-id="2f809-128">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="2f809-128">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="2f809-129">Overschrijft bestaande opdrachten die dezelfde naam hebben als de opdrachten die worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="2f809-129">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="2f809-130">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="2f809-130">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="2f809-131">Toestaan dat pakketten die zijn gemarkeerd als Prerelease, worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f809-131">Allows packages marked as prerelease to be uninstalled.</span></span>

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

### <span data-ttu-id="2f809-132">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="2f809-132">-AllVersions</span></span>

<span data-ttu-id="2f809-133">Geeft aan dat met deze cmdlet alle versies van het pakket worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f809-133">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="2f809-134">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="2f809-134">-Destination</span></span>

<span data-ttu-id="2f809-135">Hiermee geeft u een teken reeks van het pad naar het invoer object.</span><span class="sxs-lookup"><span data-stu-id="2f809-135">Specifies a string of the path to the input object.</span></span>

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

### <span data-ttu-id="2f809-136">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="2f809-136">-ExcludeVersion</span></span>

<span data-ttu-id="2f809-137">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="2f809-137">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="2f809-138">-Force</span><span class="sxs-lookup"><span data-stu-id="2f809-138">-Force</span></span>

<span data-ttu-id="2f809-139">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="2f809-139">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2f809-140">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="2f809-140">-ForceBootstrap</span></span>

<span data-ttu-id="2f809-141">Forceert **Package Management** de pakket provider automatisch te installeren voor het opgegeven pakket.</span><span class="sxs-lookup"><span data-stu-id="2f809-141">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="2f809-142">-Input object</span><span class="sxs-lookup"><span data-stu-id="2f809-142">-InputObject</span></span>

<span data-ttu-id="2f809-143">Hiermee wordt een pijplijn invoer geaccepteerd waarmee het **SoftwareIdentity** -object van het pakket wordt opgegeven vanuit de `Get-Package` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f809-143">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="2f809-144">**Input object** accepteert het **SoftwareIdentity** -object als een `Get-Package` waarde of een variabele die het object bevat.</span><span class="sxs-lookup"><span data-stu-id="2f809-144">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="2f809-145">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="2f809-145">-InstallUpdate</span></span>

<span data-ttu-id="2f809-146">Hiermee wordt aangegeven dat `Uninstall-Package` updates worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f809-146">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

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

### <span data-ttu-id="2f809-147">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2f809-147">-MaximumVersion</span></span>

<span data-ttu-id="2f809-148">Hiermee geeft u de Maxi maal toegestane pakket versie op die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2f809-148">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="2f809-149">Als u deze para meter niet opgeeft, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f809-149">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="2f809-150">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2f809-150">-MinimumVersion</span></span>

<span data-ttu-id="2f809-151">Hiermee geeft u de mini maal toegestane pakket versie op die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2f809-151">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="2f809-152">Als u deze para meter niet toevoegt, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="2f809-152">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="2f809-153">-Name</span><span class="sxs-lookup"><span data-stu-id="2f809-153">-Name</span></span>

<span data-ttu-id="2f809-154">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="2f809-154">Specifies one or more package names.</span></span> <span data-ttu-id="2f809-155">Meerdere pakket namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="2f809-155">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="2f809-156">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="2f809-156">-NoPathUpdate</span></span>

<span data-ttu-id="2f809-157">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f809-157">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="2f809-158">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="2f809-158">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

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

### <span data-ttu-id="2f809-159">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="2f809-159">-PackageManagementProvider</span></span>

<span data-ttu-id="2f809-160">Hiermee geeft u de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="2f809-160">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="2f809-161">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="2f809-161">-ProviderName</span></span>

<span data-ttu-id="2f809-162">Hiermee geeft u een of meer pakket provider namen op om te zoeken naar pakketten.</span><span class="sxs-lookup"><span data-stu-id="2f809-162">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="2f809-163">U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="2f809-163">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="2f809-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2f809-164">-RequiredVersion</span></span>

<span data-ttu-id="2f809-165">Hiermee geeft u de exacte toegestane versie van het pakket dat u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2f809-165">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="2f809-166">Als u deze para meter niet toevoegt, wordt `Uninstall-Package` de nieuwste versie van het pakket verwijderd die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="2f809-166">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="2f809-167">-Bereik</span><span class="sxs-lookup"><span data-stu-id="2f809-167">-Scope</span></span>

<span data-ttu-id="2f809-168">Hiermee geeft u het bereik op waarvoor het pakket moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="2f809-168">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="2f809-169">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="2f809-169">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2f809-170">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="2f809-170">CurrentUser</span></span>
- <span data-ttu-id="2f809-171">AllUsers</span><span class="sxs-lookup"><span data-stu-id="2f809-171">AllUsers</span></span>

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

### <span data-ttu-id="2f809-172">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="2f809-172">-SkipDependencies</span></span>

<span data-ttu-id="2f809-173">Hiermee wordt de verwijdering van software-afhankelijkheden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2f809-173">Skips the uninstallation of software dependencies.</span></span>

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

### <span data-ttu-id="2f809-174">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="2f809-174">-SkipPublisherCheck</span></span>

<span data-ttu-id="2f809-175">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="2f809-175">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="2f809-176">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="2f809-176">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="2f809-177">-Type</span><span class="sxs-lookup"><span data-stu-id="2f809-177">-Type</span></span>

<span data-ttu-id="2f809-178">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of beide.</span><span class="sxs-lookup"><span data-stu-id="2f809-178">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="2f809-179">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="2f809-179">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2f809-180">Module</span><span class="sxs-lookup"><span data-stu-id="2f809-180">Module</span></span>
- <span data-ttu-id="2f809-181">Script</span><span class="sxs-lookup"><span data-stu-id="2f809-181">Script</span></span>
- <span data-ttu-id="2f809-182">Alles</span><span class="sxs-lookup"><span data-stu-id="2f809-182">All</span></span>

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

### <span data-ttu-id="2f809-183">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2f809-183">-Confirm</span></span>

<span data-ttu-id="2f809-184">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2f809-184">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2f809-185">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2f809-185">-WhatIf</span></span>

<span data-ttu-id="2f809-186">Laat zien wat er zou gebeuren als de `Uninstall-Package` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f809-186">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="2f809-187">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f809-187">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2f809-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f809-188">CommonParameters</span></span>

<span data-ttu-id="2f809-189">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f809-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f809-190">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f809-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f809-191">INVOER</span><span class="sxs-lookup"><span data-stu-id="2f809-191">INPUTS</span></span>

### <span data-ttu-id="2f809-192">`Uninstall-Package` Hiermee worden **SoftwareIdentity** -objecten van de pijp lijn geaccepteerd als invoer.</span><span class="sxs-lookup"><span data-stu-id="2f809-192">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="2f809-193">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2f809-193">OUTPUTS</span></span>

### <span data-ttu-id="2f809-194">`Uninstall-Package` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2f809-194">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="2f809-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2f809-195">NOTES</span></span>

<span data-ttu-id="2f809-196">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f809-196">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="2f809-197">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="2f809-197">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="2f809-198">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="2f809-198">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="2f809-199">`Uninstall-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="2f809-199">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="2f809-200">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2f809-200">RELATED LINKS</span></span>

[<span data-ttu-id="2f809-201">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="2f809-201">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="2f809-202">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="2f809-202">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="2f809-203">Get-Package</span><span class="sxs-lookup"><span data-stu-id="2f809-203">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="2f809-204">Install-Package</span><span class="sxs-lookup"><span data-stu-id="2f809-204">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="2f809-205">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="2f809-205">Save-Package</span></span>](Save-Package.md)

