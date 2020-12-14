---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 93ec8264bad588e38554daddcdf5dc9befce053e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889354"
---
# <span data-ttu-id="1d0f0-102">Save-Package</span><span class="sxs-lookup"><span data-stu-id="1d0f0-102">Save-Package</span></span>

## <span data-ttu-id="1d0f0-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1d0f0-103">SYNOPSIS</span></span>
<span data-ttu-id="1d0f0-104">Hiermee worden pakketten op de lokale computer opgeslagen zonder dat ze worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-104">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="1d0f0-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1d0f0-105">SYNTAX</span></span>

### <span data-ttu-id="1d0f0-106">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1d0f0-106">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1d0f0-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1d0f0-107">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1d0f0-108">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1d0f0-108">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="1d0f0-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="1d0f0-109">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="1d0f0-110">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1d0f0-110">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="1d0f0-111">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1d0f0-111">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="1d0f0-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1d0f0-112">DESCRIPTION</span></span>

<span data-ttu-id="1d0f0-113">`Save-Package`Met de cmdlet worden pakketten opgeslagen op de lokale computer, maar worden de pakketten niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-113">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="1d0f0-114">Met deze cmdlet wordt de nieuwste versie van een pakket opgeslagen, tenzij u een **RequiredVerion** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-114">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="1d0f0-115">De para meters **Path** en **LiteralPath** sluiten elkaar wederzijds uit en kunnen niet worden toegevoegd aan dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-115">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="1d0f0-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1d0f0-116">EXAMPLES</span></span>

### <span data-ttu-id="1d0f0-117">Voor beeld 1: een pakket opslaan op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="1d0f0-117">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="1d0f0-118">In dit voor beeld wordt de nieuwste versie van het pakket opgeslagen in een map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-118">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="1d0f0-119">De afhankelijkheden van het pakket worden gedownload met het pakket.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-119">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="1d0f0-120">`Save-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-120">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="1d0f0-121">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="1d0f0-121">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="1d0f0-122">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-122">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="1d0f0-123">Voor beeld 2: een specifieke pakket versie opslaan</span><span class="sxs-lookup"><span data-stu-id="1d0f0-123">Example 2: Save a specific package version</span></span>

<span data-ttu-id="1d0f0-124">In dit voor beeld wordt de versie van het pakket opgegeven en opgeslagen in een map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-124">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="1d0f0-125">`Save-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-125">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="1d0f0-126">**RequiredVersion** geeft een specifieke pakket versie aan.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-126">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="1d0f0-127">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="1d0f0-127">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="1d0f0-128">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-128">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="1d0f0-129">Voor beeld 3: Find-Package gebruiken om een pakket op te slaan</span><span class="sxs-lookup"><span data-stu-id="1d0f0-129">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="1d0f0-130">Met deze opdracht wordt `Find-Package` de nieuwste versie van het pakket gevonden en wordt het object naar verzonden `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="1d0f0-130">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="1d0f0-131">`Find-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-131">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="1d0f0-132">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="1d0f0-132">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="1d0f0-133">Het object wordt naar de pijp lijn verzonden `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="1d0f0-133">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="1d0f0-134">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-134">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="1d0f0-135">Voor beeld 4: het pakket opslaan en installeren</span><span class="sxs-lookup"><span data-stu-id="1d0f0-135">Example 4: Save and install the package</span></span>

<span data-ttu-id="1d0f0-136">De nieuwste versie van het pakket en de bijbehorende afhankelijkheden worden gedownload en geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-136">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="1d0f0-137">`Save-Package` Hiermee downloadt u het pakket bestand en de afhankelijkheden ervan naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-137">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="1d0f0-138">`Install-Package` Hiermee installeert u het pakket en de afhankelijkheden van de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-138">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="1d0f0-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1d0f0-139">PARAMETERS</span></span>

### <span data-ttu-id="1d0f0-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="1d0f0-140">-AcceptLicense</span></span>

<span data-ttu-id="1d0f0-141">Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-142">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="1d0f0-142">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="1d0f0-143">Toestaan dat pakketten die zijn gemarkeerd als Prerelease, worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-143">Allows packages marked as Prerelease to be saved.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-144">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="1d0f0-144">-AllVersions</span></span>

<span data-ttu-id="1d0f0-145">Geeft aan dat met deze cmdlet alle beschik bare versies van het pakket worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-145">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="1d0f0-146">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="1d0f0-146">-Command</span></span>

<span data-ttu-id="1d0f0-147">Hiermee geeft u een of meer opdrachten op die zijn opgenomen in het pakket.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-147">Specifies one or more commands included in the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-148">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="1d0f0-148">-ConfigFile</span></span>

<span data-ttu-id="1d0f0-149">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-149">Specifies a configuration File.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-150">-Bevat</span><span class="sxs-lookup"><span data-stu-id="1d0f0-150">-Contains</span></span>

<span data-ttu-id="1d0f0-151">`Save-Package` haalt objecten op als een item in de eigenschaps waarden van het object exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-151">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="1d0f0-152">-Credential</span></span>

<span data-ttu-id="1d0f0-153">Hiermee geeft u een gebruikers account op dat gemachtigd is om een pakket op te slaan van een opgegeven pakket provider of-bron.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-153">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-154">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="1d0f0-154">-DscResource</span></span>

<span data-ttu-id="1d0f0-155">Hiermee geeft u een of meer resources voor desired state Configuration (DSC) voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-155">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-156">-Filter</span><span class="sxs-lookup"><span data-stu-id="1d0f0-156">-Filter</span></span>

<span data-ttu-id="1d0f0-157">Hiermee geeft u een filter op voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-157">Specifies a filter for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-158">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="1d0f0-158">-FilterOnTag</span></span>

<span data-ttu-id="1d0f0-159">Hiermee geeft u de tag op waarmee de resultaten worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-159">Specifies the tag that filters the results.</span></span> <span data-ttu-id="1d0f0-160">De resultaten die de opgegeven tag niet bevatten, worden uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-160">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-161">-Force</span><span class="sxs-lookup"><span data-stu-id="1d0f0-161">-Force</span></span>

<span data-ttu-id="1d0f0-162">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-162">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="1d0f0-163">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="1d0f0-163">-ForceBootstrap</span></span>

<span data-ttu-id="1d0f0-164">Geeft aan `Save-Package` dat **Package Management** automatisch de pakket provider voor het opgegeven pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-164">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="1d0f0-165">-Headers</span><span class="sxs-lookup"><span data-stu-id="1d0f0-165">-Headers</span></span>

<span data-ttu-id="1d0f0-166">Hiermee geeft u de headers voor het pakket op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-166">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-167">-Bevat</span><span class="sxs-lookup"><span data-stu-id="1d0f0-167">-Includes</span></span>

<span data-ttu-id="1d0f0-168">Hiermee worden de resources aangegeven die in het pakket zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-168">Indicates the resources that the package includes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-169">-Input object</span><span class="sxs-lookup"><span data-stu-id="1d0f0-169">-InputObject</span></span>

<span data-ttu-id="1d0f0-170">Een software-ID-object dat het pakket vertegenwoordigt dat u wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-170">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="1d0f0-171">Software-Id's maken deel uit van de resultaten van de `Find-Package` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-171">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1d0f0-172">-LiteralPath</span></span>

<span data-ttu-id="1d0f0-173">Hiermee geeft u het letterlijke pad op waarin u het pakket wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-173">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="1d0f0-174">U kunt deze para meter en de para meter **Path** niet aan dezelfde opdracht toevoegen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-174">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="1d0f0-175">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1d0f0-175">-MaximumVersion</span></span>

<span data-ttu-id="1d0f0-176">Hiermee geeft u de maximum versie van het pakket op dat u wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-176">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="1d0f0-177">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1d0f0-177">-MinimumVersion</span></span>

<span data-ttu-id="1d0f0-178">Hiermee geeft u de minimum versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-178">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="1d0f0-179">-Name</span><span class="sxs-lookup"><span data-stu-id="1d0f0-179">-Name</span></span>

<span data-ttu-id="1d0f0-180">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-180">Specifies one or more package names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-181">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="1d0f0-181">-PackageManagementProvider</span></span>

<span data-ttu-id="1d0f0-182">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-182">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-183">-Path</span><span class="sxs-lookup"><span data-stu-id="1d0f0-183">-Path</span></span>

<span data-ttu-id="1d0f0-184">Hiermee geeft u de locatie op de lokale computer op waarop het pakket moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-184">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="1d0f0-185">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="1d0f0-185">-ProviderName</span></span>

<span data-ttu-id="1d0f0-186">Hiermee geeft u een of meer provider namen op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-186">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="1d0f0-187">-Proxy</span><span class="sxs-lookup"><span data-stu-id="1d0f0-187">-Proxy</span></span>

<span data-ttu-id="1d0f0-188">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-188">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-189">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1d0f0-189">-ProxyCredential</span></span>

<span data-ttu-id="1d0f0-190">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="1d0f0-190">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-191">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="1d0f0-191">-PublishLocation</span></span>

<span data-ttu-id="1d0f0-192">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-192">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-193">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1d0f0-193">-RequiredVersion</span></span>

<span data-ttu-id="1d0f0-194">Hiermee geeft u de exacte versie van het pakket op dat moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-194">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="1d0f0-195">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1d0f0-195">-RoleCapability</span></span>

<span data-ttu-id="1d0f0-196">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-196">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-197">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="1d0f0-197">-ScriptPublishLocation</span></span>

<span data-ttu-id="1d0f0-198">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-198">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-199">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="1d0f0-199">-ScriptSourceLocation</span></span>

<span data-ttu-id="1d0f0-200">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-200">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-201">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="1d0f0-201">-SkipValidate</span></span>

<span data-ttu-id="1d0f0-202">Switch waarmee de validatie van de referenties van een pakket wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-202">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-203">-Source</span><span class="sxs-lookup"><span data-stu-id="1d0f0-203">-Source</span></span>

<span data-ttu-id="1d0f0-204">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-204">Specifies one or more package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-205">-Tag</span><span class="sxs-lookup"><span data-stu-id="1d0f0-205">-Tag</span></span>

<span data-ttu-id="1d0f0-206">Hiermee geeft u een label op waarnaar moet worden gezocht in de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-206">Specifies a tag to search for within the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-207">-Type</span><span class="sxs-lookup"><span data-stu-id="1d0f0-207">-Type</span></span>

<span data-ttu-id="1d0f0-208">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-208">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d0f0-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1d0f0-209">-Confirm</span></span>

<span data-ttu-id="1d0f0-210">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-210">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1d0f0-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1d0f0-211">-WhatIf</span></span>

<span data-ttu-id="1d0f0-212">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1d0f0-213">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1d0f0-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d0f0-214">CommonParameters</span></span>

<span data-ttu-id="1d0f0-215">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d0f0-216">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d0f0-217">INVOER</span><span class="sxs-lookup"><span data-stu-id="1d0f0-217">INPUTS</span></span>

### <span data-ttu-id="1d0f0-218">`Save-Package` objecten uit de pijp lijn accepteren.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-218">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="1d0f0-219">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1d0f0-219">OUTPUTS</span></span>

### <span data-ttu-id="1d0f0-220">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-220">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1d0f0-221">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1d0f0-221">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d0f0-222">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-222">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="1d0f0-223">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-223">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="1d0f0-224">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="1d0f0-224">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="1d0f0-225">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1d0f0-225">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="1d0f0-226">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1d0f0-226">RELATED LINKS</span></span>

[<span data-ttu-id="1d0f0-227">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="1d0f0-227">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="1d0f0-228">Get-Package</span><span class="sxs-lookup"><span data-stu-id="1d0f0-228">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="1d0f0-229">Install-Package</span><span class="sxs-lookup"><span data-stu-id="1d0f0-229">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="1d0f0-230">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="1d0f0-230">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="1d0f0-231">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="1d0f0-231">Uninstall-Package</span></span>](Uninstall-Package.md)
