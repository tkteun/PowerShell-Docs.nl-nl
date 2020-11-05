---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 97ba55f4185d784e4b32bbe669296d44989f72d2
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249566"
---
# <span data-ttu-id="51297-103">Save-Package</span><span class="sxs-lookup"><span data-stu-id="51297-103">Save-Package</span></span>

## <span data-ttu-id="51297-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="51297-104">SYNOPSIS</span></span>
<span data-ttu-id="51297-105">Hiermee worden pakketten op de lokale computer opgeslagen zonder dat ze worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="51297-105">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="51297-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="51297-106">SYNTAX</span></span>

### <span data-ttu-id="51297-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="51297-107">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="51297-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="51297-108">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51297-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="51297-109">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="51297-110">NuGet</span><span class="sxs-lookup"><span data-stu-id="51297-110">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="51297-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="51297-111">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="51297-112">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="51297-112">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="51297-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="51297-113">DESCRIPTION</span></span>

<span data-ttu-id="51297-114">`Save-Package`Met de cmdlet worden pakketten opgeslagen op de lokale computer, maar worden de pakketten niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="51297-114">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="51297-115">Met deze cmdlet wordt de nieuwste versie van een pakket opgeslagen, tenzij u een **RequiredVerion** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="51297-115">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="51297-116">De para meters **Path** en **LiteralPath** sluiten elkaar wederzijds uit en kunnen niet worden toegevoegd aan dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="51297-116">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="51297-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="51297-117">EXAMPLES</span></span>

### <span data-ttu-id="51297-118">Voor beeld 1: een pakket opslaan op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="51297-118">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="51297-119">In dit voor beeld wordt de nieuwste versie van het pakket opgeslagen in een map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="51297-119">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="51297-120">De afhankelijkheden van het pakket worden gedownload met het pakket.</span><span class="sxs-lookup"><span data-stu-id="51297-120">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="51297-121">`Save-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="51297-121">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="51297-122">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="51297-122">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="51297-123">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-123">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="51297-124">Voor beeld 2: een specifieke pakket versie opslaan</span><span class="sxs-lookup"><span data-stu-id="51297-124">Example 2: Save a specific package version</span></span>

<span data-ttu-id="51297-125">In dit voor beeld wordt de versie van het pakket opgegeven en opgeslagen in een map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="51297-125">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="51297-126">`Save-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="51297-126">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="51297-127">**RequiredVersion** geeft een specifieke pakket versie aan.</span><span class="sxs-lookup"><span data-stu-id="51297-127">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="51297-128">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="51297-128">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="51297-129">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-129">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="51297-130">Voor beeld 3: Find-Package gebruiken om een pakket op te slaan</span><span class="sxs-lookup"><span data-stu-id="51297-130">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="51297-131">Met deze opdracht wordt `Find-Package` de nieuwste versie van het pakket gevonden en wordt het object naar verzonden `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="51297-131">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="51297-132">`Find-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="51297-132">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="51297-133">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="51297-133">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="51297-134">Het object wordt naar de pijp lijn verzonden `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="51297-134">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="51297-135">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-135">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="51297-136">Voor beeld 4: het pakket opslaan en installeren</span><span class="sxs-lookup"><span data-stu-id="51297-136">Example 4: Save and install the package</span></span>

<span data-ttu-id="51297-137">De nieuwste versie van het pakket en de bijbehorende afhankelijkheden worden gedownload en geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="51297-137">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="51297-138">`Save-Package` Hiermee downloadt u het pakket bestand en de afhankelijkheden ervan naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="51297-138">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="51297-139">`Install-Package` Hiermee installeert u het pakket en de afhankelijkheden van de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="51297-139">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="51297-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51297-140">PARAMETERS</span></span>

### <span data-ttu-id="51297-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="51297-141">-AcceptLicense</span></span>

<span data-ttu-id="51297-142">Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="51297-142">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="51297-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="51297-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="51297-144">Toestaan dat pakketten die zijn gemarkeerd als Prerelease, worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-144">Allows packages marked as Prerelease to be saved.</span></span>

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

### <span data-ttu-id="51297-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="51297-145">-AllVersions</span></span>

<span data-ttu-id="51297-146">Geeft aan dat met deze cmdlet alle beschik bare versies van het pakket worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-146">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="51297-147">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="51297-147">-Command</span></span>

<span data-ttu-id="51297-148">Hiermee geeft u een of meer opdrachten op die zijn opgenomen in het pakket.</span><span class="sxs-lookup"><span data-stu-id="51297-148">Specifies one or more commands included in the package.</span></span>

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

### <span data-ttu-id="51297-149">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="51297-149">-ConfigFile</span></span>

<span data-ttu-id="51297-150">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="51297-150">Specifies a configuration File.</span></span>

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

### <span data-ttu-id="51297-151">-Bevat</span><span class="sxs-lookup"><span data-stu-id="51297-151">-Contains</span></span>

<span data-ttu-id="51297-152">`Save-Package` haalt objecten op als een item in de eigenschaps waarden van het object exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="51297-152">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="51297-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="51297-153">-Credential</span></span>

<span data-ttu-id="51297-154">Hiermee geeft u een gebruikers account op dat gemachtigd is om een pakket op te slaan van een opgegeven pakket provider of-bron.</span><span class="sxs-lookup"><span data-stu-id="51297-154">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="51297-155">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="51297-155">-DscResource</span></span>

<span data-ttu-id="51297-156">Hiermee geeft u een of meer resources voor desired state Configuration (DSC) voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="51297-156">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

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

### <span data-ttu-id="51297-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="51297-157">-Filter</span></span>

<span data-ttu-id="51297-158">Hiermee geeft u een filter op voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="51297-158">Specifies a filter for the package.</span></span>

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

### <span data-ttu-id="51297-159">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="51297-159">-FilterOnTag</span></span>

<span data-ttu-id="51297-160">Hiermee geeft u de tag op waarmee de resultaten worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="51297-160">Specifies the tag that filters the results.</span></span> <span data-ttu-id="51297-161">De resultaten die de opgegeven tag niet bevatten, worden uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="51297-161">Results that don't contain the specified tag are excluded.</span></span>

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

### <span data-ttu-id="51297-162">-Force</span><span class="sxs-lookup"><span data-stu-id="51297-162">-Force</span></span>

<span data-ttu-id="51297-163">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="51297-163">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="51297-164">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="51297-164">-ForceBootstrap</span></span>

<span data-ttu-id="51297-165">Geeft aan `Save-Package` dat **Package Management** automatisch de pakket provider voor het opgegeven pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="51297-165">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="51297-166">-Headers</span><span class="sxs-lookup"><span data-stu-id="51297-166">-Headers</span></span>

<span data-ttu-id="51297-167">Hiermee geeft u de headers voor het pakket op.</span><span class="sxs-lookup"><span data-stu-id="51297-167">Specifies the headers for the package.</span></span>

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

### <span data-ttu-id="51297-168">-Bevat</span><span class="sxs-lookup"><span data-stu-id="51297-168">-Includes</span></span>

<span data-ttu-id="51297-169">Hiermee worden de resources aangegeven die in het pakket zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="51297-169">Indicates the resources that the package includes.</span></span>

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

### <span data-ttu-id="51297-170">-Input object</span><span class="sxs-lookup"><span data-stu-id="51297-170">-InputObject</span></span>

<span data-ttu-id="51297-171">Een software-ID-object dat het pakket vertegenwoordigt dat u wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="51297-171">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="51297-172">Software-Id's maken deel uit van de resultaten van de `Find-Package` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51297-172">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

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

### <span data-ttu-id="51297-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="51297-173">-LiteralPath</span></span>

<span data-ttu-id="51297-174">Hiermee geeft u het letterlijke pad op waarin u het pakket wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="51297-174">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="51297-175">U kunt deze para meter en de para meter **Path** niet aan dezelfde opdracht toevoegen.</span><span class="sxs-lookup"><span data-stu-id="51297-175">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="51297-176">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="51297-176">-MaximumVersion</span></span>

<span data-ttu-id="51297-177">Hiermee geeft u de maximum versie van het pakket op dat u wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="51297-177">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="51297-178">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="51297-178">-MinimumVersion</span></span>

<span data-ttu-id="51297-179">Hiermee geeft u de minimum versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="51297-179">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="51297-180">-Name</span><span class="sxs-lookup"><span data-stu-id="51297-180">-Name</span></span>

<span data-ttu-id="51297-181">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="51297-181">Specifies one or more package names.</span></span>

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

### <span data-ttu-id="51297-182">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="51297-182">-PackageManagementProvider</span></span>

<span data-ttu-id="51297-183">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="51297-183">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="51297-184">-Path</span><span class="sxs-lookup"><span data-stu-id="51297-184">-Path</span></span>

<span data-ttu-id="51297-185">Hiermee geeft u de locatie op de lokale computer op waarop het pakket moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-185">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="51297-186">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="51297-186">-ProviderName</span></span>

<span data-ttu-id="51297-187">Hiermee geeft u een of meer provider namen op.</span><span class="sxs-lookup"><span data-stu-id="51297-187">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="51297-188">-Proxy</span><span class="sxs-lookup"><span data-stu-id="51297-188">-Proxy</span></span>

<span data-ttu-id="51297-189">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="51297-189">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="51297-190">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="51297-190">-ProxyCredential</span></span>

<span data-ttu-id="51297-191">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="51297-191">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="51297-192">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="51297-192">-PublishLocation</span></span>

<span data-ttu-id="51297-193">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="51297-193">Specifies the publish location.</span></span>

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

### <span data-ttu-id="51297-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="51297-194">-RequiredVersion</span></span>

<span data-ttu-id="51297-195">Hiermee geeft u de exacte versie van het pakket op dat moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-195">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="51297-196">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="51297-196">-RoleCapability</span></span>

<span data-ttu-id="51297-197">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="51297-197">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="51297-198">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="51297-198">-ScriptPublishLocation</span></span>

<span data-ttu-id="51297-199">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="51297-199">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="51297-200">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="51297-200">-ScriptSourceLocation</span></span>

<span data-ttu-id="51297-201">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="51297-201">Specifies the script source location.</span></span>

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

### <span data-ttu-id="51297-202">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="51297-202">-SkipValidate</span></span>

<span data-ttu-id="51297-203">Switch waarmee de validatie van de referenties van een pakket wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="51297-203">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="51297-204">-Source</span><span class="sxs-lookup"><span data-stu-id="51297-204">-Source</span></span>

<span data-ttu-id="51297-205">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="51297-205">Specifies one or more package sources.</span></span>

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

### <span data-ttu-id="51297-206">-Tag</span><span class="sxs-lookup"><span data-stu-id="51297-206">-Tag</span></span>

<span data-ttu-id="51297-207">Hiermee geeft u een label op waarnaar moet worden gezocht in de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="51297-207">Specifies a tag to search for within the package metadata.</span></span>

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

### <span data-ttu-id="51297-208">-Type</span><span class="sxs-lookup"><span data-stu-id="51297-208">-Type</span></span>

<span data-ttu-id="51297-209">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.</span><span class="sxs-lookup"><span data-stu-id="51297-209">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="51297-210">-Confirm</span><span class="sxs-lookup"><span data-stu-id="51297-210">-Confirm</span></span>

<span data-ttu-id="51297-211">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="51297-211">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="51297-212">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="51297-212">-WhatIf</span></span>

<span data-ttu-id="51297-213">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="51297-213">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="51297-214">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="51297-214">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="51297-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51297-215">CommonParameters</span></span>

<span data-ttu-id="51297-216">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51297-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51297-217">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="51297-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51297-218">INVOER</span><span class="sxs-lookup"><span data-stu-id="51297-218">INPUTS</span></span>

### <span data-ttu-id="51297-219">`Save-Package` objecten uit de pijp lijn accepteren.</span><span class="sxs-lookup"><span data-stu-id="51297-219">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="51297-220">UITVOER</span><span class="sxs-lookup"><span data-stu-id="51297-220">OUTPUTS</span></span>

### <span data-ttu-id="51297-221">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="51297-221">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="51297-222">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="51297-222">NOTES</span></span>

## <span data-ttu-id="51297-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="51297-223">RELATED LINKS</span></span>

[<span data-ttu-id="51297-224">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="51297-224">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="51297-225">Get-Package</span><span class="sxs-lookup"><span data-stu-id="51297-225">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="51297-226">Install-Package</span><span class="sxs-lookup"><span data-stu-id="51297-226">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="51297-227">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="51297-227">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="51297-228">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="51297-228">Uninstall-Package</span></span>](Uninstall-Package.md)